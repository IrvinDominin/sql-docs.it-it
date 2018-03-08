---
title: Configurare l'istanza del cluster di failover, SQL Server in Linux (RHEL) | Documenti Microsoft
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Inactive
ms.openlocfilehash: 26ccd4389bd02f659110c0fe3ac2cd8b23b240db
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2018
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Configurare l'istanza del cluster di failover, SQL Server in Linux (RHEL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Un'istanza cluster di failover di SQL Server nel disco condiviso due nodi fornisce la ridondanza a livello di server per la disponibilità elevata. In questa esercitazione imparare a creare un'istanza del cluster di failover a due nodi di SQL Server in Linux. I passaggi specifici che si completeranno includono:

> [!div class="checklist"]
> * Installare e configurare Linux
> * Installare e configurare SQL Server
> * Configurare il file hosts
> * Configurare l'archiviazione condivisa e spostare i file di database
> * Installare e configurare Pacemaker su ogni nodo del cluster
> * Configurare l'istanza del cluster di failover

In questo articolo viene illustrato come creare un'istanza di cluster di failover (FCI) disco condiviso a due nodi per SQL Server. L'articolo include istruzioni ed esempi di script per Red Hat Enterprise Linux (RHEL). Ubuntu distribuzioni sono simili a RHEL pertanto gli esempi di script in genere funzionano anche in Ubuntu. 

Per ulteriori informazioni, vedere [istanza SQL Server Failover Cluster (FCI) in Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>Prerequisiti

Per completare lo scenario end-to-end seguente devono essere presenti due macchine per distribuire il cluster a due nodi e un altro server per l'archiviazione. Passaggi seguenti viene descritto come questi server verranno configurati.

## <a name="set-up-and-configure-linux"></a>Installare e configurare Linux

Il primo passaggio consiste nel configurare il sistema operativo nei nodi del cluster. In ogni nodo del cluster, configurare una distribuzione di linux. Utilizzare la stessa distribuzione e la versione in entrambi i nodi. Utilizzare uno o l'altra le seguenti distribuzioni:
    
* RHEL con una sottoscrizione valida per il componente aggiuntivo a disponibilità elevata

## <a name="install-and-configure-sql-server"></a>Installare e configurare SQL Server

1. Installare e configurare SQL Server in entrambi i nodi.  Per istruzioni dettagliate, vedere [installazione di SQL Server in Linux](sql-server-linux-setup.md).
1. Specificare un nodo primario e l'altro come secondario, ai fini di configurazione. Utilizzare questi termini per le operazioni seguenti in questa Guida.  
1. Nel nodo secondario, arrestare e disabilitare il Server SQL.
    Nell'esempio seguente arresta e disattiva SQL Server: 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Intervalli di tempo, viene generato per l'istanza di SQL Server e inserito in una chiave Master del Server `var/opt/mssql/secrets/machine-key`. In Linux, SQL Server viene sempre eseguito come un account locale denominato mssql. Poiché si tratta di un account locale, l'identità non è condivise tra i nodi. Pertanto, è necessario copiare la chiave di crittografia dal nodo primario a ogni nodo secondario in modo che ogni account locale mssql possono accedervi per decrittografare la chiave Master del Server. 

1.  Nel nodo primario, creare un account di accesso SQL server per Pacemaker e concedere l'autorizzazione di accesso per l'esecuzione `sp_server_diagnostics`. Pacemaker utilizza questo account per verificare quale sia il nodo è in esecuzione SQL Server. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Connettersi a SQL Server `master` con l'account sa di database ed eseguire le operazioni seguenti:

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   In alternativa, è possibile impostare le autorizzazioni a un livello più granulare. Richiede l'account di accesso Pacemaker `VIEW SERVER STATE` per query sullo stato di integrità con sp_server_diagnostics, `setupadmin` e `ALTER ANY LINKED SERVER` per aggiornare il nome dell'istanza FCI con il nome della risorsa eseguendo sp_dropserver e sp_addserver. 

1. Nel nodo primario, arrestare e disabilitare il Server SQL. 

## <a name="configure-the-hosts-file"></a>Configurare il file hosts

In ogni nodo del cluster, configurare il file hosts. Il file hosts deve includere l'indirizzo IP e nome di ogni nodo del cluster.

1. Controllare l'indirizzo IP per ogni nodo. Lo script seguente viene illustrato l'indirizzo IP del nodo corrente. 

    ```bash
    sudo ip addr show
    ```

1. Impostare il nome del computer in ogni nodo. Assegnare a ogni nodo un nome univoco che è di 15 caratteri o meno. Impostare il nome del computer, aggiungerlo al `/etc/hosts`. Lo script seguente consente di modificare `/etc/hosts` con `vi`. 

   ```bash
   sudo vi /etc/hosts
   ```
   Nell'esempio seguente `/etc/hosts` aggiunte due nodi denominati `sqlfcivm1` e `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

## <a name="configure-storage--move-database-files"></a>Configurare l'archiviazione e spostare i file di database  

È necessario fornire spazio di archiviazione accessibili a entrambi i nodi. È possibile utilizzare iSCSI o NFS, SMB. Configurare l'archiviazione, presentare l'archiviazione per i nodi del cluster e quindi spostare i file di database nella nuova risorsa di archiviazione. Gli articoli seguenti vengono illustrati i passaggi per ogni tipo di archiviazione:

- [Configurare l'istanza del cluster di failover SQL Server in Linux - iSCSI:](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Configurare i cluster di failover - NFS - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Configurazione di cluster di failover - SMB - SQL Server in Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installare e configurare Pacemaker su ogni nodo del cluster

1. In entrambi i nodi del cluster creare un file per archiviare nome utente e password di SQL Server per l'accesso a Pacemaker. 

    Il comando seguente crea e popola questo file:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd    
    ```

1. In entrambi i nodi del cluster aprire le porte del firewall di Pacemaker. Per aprire queste porte con `firewalld`, eseguire il comando seguente:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Se si sta usando un altro firewall che non ha una configurazione a disponibilità elevata predefinita, è necessario aprire le porte seguenti per consentire a Pacemaker di comunicare con altri nodi del cluster
   >
   > * TCP: porte 2224, 3121, 21064
   > * UDP: porta 5405

1. Installare i pacchetti Pacemaker in ogni nodo.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
1. Impostare la password per l'utente predefinito creato durante l'installazione dei pacchetti Corosync e Pacemaker. Usare la stessa password in entrambi i nodi. 

   ```bash
   sudo passwd hacluster
   ```
1. Abilitare e avviare il servizio `pcsd` e Pacemaker. In questo modo, i nodi potranno unirsi nuovamente in join con il cluster dopo il riavvio. Eseguire il comando seguente in entrambi i nodi.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. Installare l'agente delle risorse FCI per SQL Server. Eseguire i comandi seguenti in entrambi i nodi. 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="configure-the-failover-cluster-instance"></a>Configurare l'istanza del cluster di failover

Verrà creata l'istanza cluster di failover in un gruppo di risorse. Questo è un po' più semplice perché il gruppo di risorse riduce la necessità di vincoli. Tuttavia, è possibile aggiungere le risorse nel gruppo di risorse nell'ordine in che cui deve iniziare. L'ordine che devono avviare è: 

1. Risorsa di archiviazione
2. Risorsa di rete
3. Risorsa dell'applicazione

In questo esempio creerà un'istanza cluster di failover del gruppo NewLinFCIGrp. Il nome del gruppo di risorse deve essere univoco rispetto a qualsiasi risorsa creata mediante Pacemaker.

1.  Creare la risorsa disco. Se non si verifica un problema, non si otterrà alcuna risposta. Il modo per creare la risorsa disco dipende dal tipo di archiviazione. Di seguito è riportato un esempio per ogni tipo di archiviazione. Utilizzare l'esempio in cui si applica al tipo di archiviazione per l'archiviazione in cluster.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > è il nome della risorsa associato al disco iSCSI

    \<VolumeGroupName > è il nome del gruppo di volumi  

    \<LogicalVolumeName > è il nome del volume logico che è stato creato  

    \<FolderToMountiSCSIDIsk > è la cartella per montare il disco (per i database di sistema e il percorso predefinito, sarebbe /var/opt/mssql/data)

    \<FileSystemType > sarebbe EXT4 o XFS a seconda della modalità di formattazione delle operazioni e supporta quali la distribuzione. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > è il nome della risorsa associato alla condivisione NFS

    \<IPAddressOfNFSServer > è l'indirizzo IP del server NFS che si desidera utilizzare

    \<FolderOnNFSServer > è il nome della condivisione NFS

    \<FolderToMountNFSShare > è la cartella per montare il disco (per i database di sistema e il percorso predefinito, sarebbe /var/opt/mssql/data)

    Di seguito è riportato un esempio:

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<NomeServer > è il nome del server con la condivisione SMB

    \<Nomecondivisione > è il nome della condivisione

    \<Nome cartella > è il nome della cartella creata nel passaggio precedente
    
    \<Nome utente > è il nome dell'utente per accedere alla condivisione

    \<Password > è la password per l'utente

    \<ADDomain > è il dominio di Active Directory (se applicabile quando si utilizza una condivisione SMB basate su Windows Server)

    \<mssqlUID > è l'UID dell'utente mssql

    \<mssqlGID > è GID dell'utente mssql

    \<RGName > è il nome del gruppo di risorse
 
2.  Creare l'indirizzo IP che verrà utilizzato dall'istanza FCI. Se non si verifica un problema, non si otterrà alcuna risposta.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > è il nome della risorsa associato all'indirizzo IP

    \<Indirizzo IP > è l'indirizzo IP per l'istanza FCI

    \<NetworkCard > è la scheda di rete associata alla subnet (ad esempio eth0)

    \<Subnet mask > è la subnet mask della subnet (ad esempio 24)

    \<RGName > è il nome del gruppo di risorse
 
3.  Creare la risorsa istanza cluster di failover. Se non si verifica un problema, non si otterrà alcuna risposta.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > è il nome della risorsa non solo, ma il nome descrittivo associato con l'istanza FCI. Questo è ciò che gli utenti e applicazioni userà per connettersi. 

    \<RGName > è il nome del gruppo di risorse.
 
4.  Eseguire il comando `sudo pcs resource`. Il failover deve essere online.
 
5.  Connettersi all'istanza di FCI con SQL Server Management Studio o utilizzando il nome DNS o risorse dell'istanza FCI sqlcmd.

6.  Eseguire l'istruzione `SELECT @@SERVERNAME`. Deve restituire il nome dell'istanza FCI.

7.  Eseguire l'istruzione `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Deve restituire il nome del nodo su cui è in esecuzione l'istanza FCI.

8.  Eseguire manualmente il failover in altri nodi. Vedere le istruzioni in [istanza cluster di failover Operate: SQL Server in Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  Infine, eseguire il failover al nodo originale e rimuovere il vincolo di condivisione del percorso.

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>Riepilogo

In questa esercitazione è completato le attività seguenti.

> [!div class="checklist"]
> * Installare e configurare Linux
> * Installare e configurare SQL Server
> * Configurare il file hosts
> * Configurare l'archiviazione condivisa e spostare i file di database
> * Installare e configurare Pacemaker su ogni nodo del cluster
> * Configurare l'istanza del cluster di failover

## <a name="next-steps"></a>Passaggi successivi

- [Utilizzare l'istanza del cluster di failover, SQL Server in Linux](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
