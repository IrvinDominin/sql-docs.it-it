---
title: "Aggiornare un&#39;istanza del cluster di failover di SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "02/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "aggiornamento di cluster di failover"
  - "cluster [SQL Server], aggiornamento"
  - "clustering di failover [SQL Server], aggiornamento"
ms.assetid: daac41fe-7d0b-4f14-84c2-62952ad8cbfa
caps.latest.revision: 47
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 47
---
# Aggiornare un&#39;istanza del cluster di failover di SQL Server
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta l'aggiornamento di un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a una nuova versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a un nuovo Service Pack di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o aggiornamento cumulativo o quando si esegue l'installazione in un nuovo Service Pack o aggiornamento cumulativo di Windows separatamente in tutti i nodi cluster di failover, con tempo di inattività limitato a un singolo failover manuale (o due failover manuali in caso di failback alla replica primaria originale).  
  
 L'aggiornamento del sistema operativo Windows di un cluster di failover non è supportato per i sistemi operativi precedenti a Windows Server 2012 R2. Per aggiornare un nodo del cluster in esecuzione su Windows Server 2012 R2, vedere [Aggiornamento in sequenza del sistema operativo del cluster](https://technet.microsoft.com/en-us/library/dn850430.aspx)  
  
 I dettagli relativi al supporto sono i seguenti:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]l'aggiornamento è supportato sia tramite l'interfaccia utente sia dal prompt dei comandi. È possibile eseguire l'aggiornamento dal prompt dei comandi in ogni nodo del cluster di failover o tramite l'interfaccia utente del programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per aggiornare ogni nodo del cluster.  Per altre informazioni, vedere [Eseguire l'aggiornamento di un'istanza del cluster di failover di SQL Server &#40;installazione&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md) e [Installazione di SQL Server 2016 dal prompt dei comandi](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
-   In un aggiornamento di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non sono supportati gli scenari seguenti:  
  
    -   Non è possibile eseguire l'aggiornamento da un'istanza autonoma di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a un cluster di failover.  
  
    -   Non è possibile aggiungere funzionalità a un cluster di failover. Non è possibile ad esempio aggiungere il [!INCLUDE[ssDE](../../../includes/ssde-md.md)] a un cluster di failover solo di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] esistente.  
  
    -   Non è possibile effettuare il downgrade di un nodo del cluster di failover a un'istanza autonoma.  
  
    -   La modifica dell'edizione del cluster di failover è limitata a determinati scenari. Per altre informazioni, vedere [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
-   Durante l'aggiornamento del cluster di failover, il tempo di inattività è limitato alla durata del failover e al tempo necessario per l'esecuzione degli script di aggiornamento. Se si segue il processo di aggiornamento in sequenza del cluster di failover indicato sotto e sono soddisfatti tutti i prerequisiti in tutti i nodi prima di iniziare il processo di aggiornamento, il tempo di inattività è minimo. L'aggiornamento di SQL Server 2014 quando le tabelle con ottimizzazione per la memoria sono in uso comporta maggiore tempo. Per altre informazioni, vedere [Plan and Test the Database Engine Upgrade Plan](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md).  
  
## Prerequisiti  
 Prima di iniziare, esaminare le informazioni seguenti:  
  
-   [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md): verificare che sia possibile eseguire l'aggiornamento a SQL Server 2016 dalla versione del sistema operativo Windows e di SQL Server. Ad esempio, non è possibile eseguire direttamente l'aggiornamento da un'istanza di clustering di failover di SQL Server 2005 a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] o aggiornare un cluster di failover in esecuzione su Windows Server 2003.  
  
-   [Choose a Database Engine Upgrade Method](../../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md): selezionare il metodo e la procedura di aggiornamento appropriati in base alla verifica degli aggiornamenti della versione e dell'edizione supportate e anche agli altri componenti installati nell'ambiente interessato per aggiornare i componenti nell'ordine corretto.  
  
-   [Pianificare e testare il piano di aggiornamento del motore di database](../../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md): esaminare le note sulla versione, i problemi di aggiornamento noti e l'elenco di controllo pre-aggiornamento e sviluppare e testare il piano di aggiornamento.  
  
-   [Hardware and Software Requirements for Installing SQL Server 2016](../../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md): esaminare i requisiti software per l'installazione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Se è necessario software aggiuntivo, installarlo in ogni nodo prima di iniziare il processo di aggiornamento per ridurre al minimo eventuali tempi di inattività.  
  
## Eseguire un aggiornamento o un aggiornamento in sequenza  
 Per aggiornare un cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], eseguire il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per aggiornare i nodi del cluster di failover, uno alla volta, a partire dai nodi passivi. Man mano che viene aggiornato, ogni nodo viene escluso dai possibili proprietari del cluster di failover. In caso di failover imprevisto, i nodi aggiornati non partecipano al failover fino a quando la proprietà del gruppo di risorse del cluster non viene spostata in un nodo aggiornato dal programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per impostazione predefinita, il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] determina automaticamente il momento in cui eseguire il failover a un nodo aggiornato, che dipende dal numero complessivo di nodi nell'istanza del cluster di failover e dal numero di nodi già aggiornati. Quando un numero di nodi uguale o maggiore della metà è già stato aggiornato, il programma di installazione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] esegue il failover a un nodo aggiornato nel momento in cui si esegue l'aggiornamento del nodo successivo. In seguito al failover a un nodo aggiornato, il gruppo cluster viene spostato in un nodo aggiornato. Tutti i nodi aggiornati vengono inseriti nell'elenco dei possibili proprietari e tutti i nodi non ancora aggiornati vengono rimossi da tale elenco. Man mano che ne viene eseguito l'aggiornamento, ogni nodo rimanente viene aggiunto ai possibili proprietari del cluster di failover.  
  
 Questo processo comporta un tempo di inattività limitato alla durata del failover e al tempo di esecuzione degli script di aggiornamento del database durante l'aggiornamento dell'intero cluster di failover.  
  
 Per controllare il comportamento del failover dei nodi del cluster durante il processo di aggiornamento, eseguire l'operazione di aggiornamento nel prompt dei comandi e utilizzare il parametro /FAILOVERCLUSTERROLLOWNERSHIP. Per altre informazioni, vedere [Installazione di SQL Server 2016 dal prompt dei comandi](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
## Vedere anche  
 [Eseguire l'aggiornamento a SQL Server 2016 usando l'Installazione guidata &#40;programma di installazione&#41;](../../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)   
 [Installazione di SQL Server 2016 dal prompt dei comandi](../../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)   
 [Eseguire l'aggiornamento di un'istanza del cluster di failover di SQL Server &#40;installazione&#41;](../../../sql-server/failover-clusters/windows/upgrade-a-sql-server-failover-cluster-instance-setup.md)  
  
  