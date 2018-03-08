---
title: Configurare FILESTREAM in un cluster di failover | Microsoft Docs
ms.custom: 
ms.date: 08/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: blob
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], setting up on a failover cluster
ms.assetid: 6721f780-20b7-4109-8ddb-ac327310699e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4cfd6d35f3b0355aece3f6780f3f1e6b04813f7
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="set-up-filestream-on-a-failover-cluster"></a>Configurazione di FILESTREAM in un cluster di failover
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento viene descritto come abilitare FILESTREAM in un cluster di failover. Prima di eseguire questa procedura, è consigliabile acquisire familiarità con il [clustering di failover](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md) e abilitare FILESTREAM. Per informazioni su come abilitare FILESTREAM, vedere [Abilitare e configurare FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md).  
  
### <a name="to-set-up-filestream-on-a-failover-cluster"></a>Per configurare FILESTREAM in un cluster di failover  
  
1.  Configurare il nodo primario per il cluster di failover.  
  
     Al termine della configurazione, abilitare FILESTREAM nel nodo primario usando **Gestione configurazione SQL Server**. Verranno abilitate le impostazioni per cui è necessario disporre dei privilegi di amministratore di Windows. Se è necessario usare l'accesso remoto, selezionare **Consenti ai client remoti l'accesso tramite flusso ai dati FILESTREAM**. Verrà creata una risorsa cluster di condivisione file.  
  
2.  Configurare un nodo passivo.  
  
     Al termine della configurazione, abilitare FILESTREAM nel nodo passivo usando **Gestione configurazione SQL Server**. Il nome specificato per **Nome condivisione di Windows** deve essere lo stesso in tutti i nodi del cluster.  
  
3.  Per aggiungere più nodi passivi, ripetere il passaggio 2.  
  
4.  Una volta aggiunti tutti i nodi, completare il processo eseguendo la stored procedure sp_configure in ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
5.  Per aggiungere e abilitare nodi aggiuntivi nel cluster in qualsiasi momento, ripetere i passaggi 2, 3 e 4.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni di configurazione del server &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Creare un nuovo cluster di failover di SQL Server &#40;programma di installazione&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)   
 [Rimuovere un'istanza del cluster di failover di SQL Server &#40;programma di installazione&#41;](../../sql-server/failover-clusters/install/remove-a-sql-server-failover-cluster-instance-setup.md)   
 [Aggiungere o rimuovere nodi in un cluster di failover di SQL Server &#40;programma di installazione&#41;](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
  
