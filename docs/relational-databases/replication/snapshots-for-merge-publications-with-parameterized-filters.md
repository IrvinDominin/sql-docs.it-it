---
title: Snapshot per pubblicazioni di tipo merge con filtri con parametri | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameterized filters [SQL Server replication], snapshots
- snapshots [SQL Server replication], parameterized filters and
- filters [SQL Server replication], parameterized
- merge replication [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 99d7ae15-5457-4ad4-886b-19c17371f72c
caps.latest.revision: "37"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ec934637b86851a4d6fdc57722ac46aeebd0429e
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="snapshots-for-merge-publications-with-parameterized-filters"></a>Snapshot per pubblicazioni di tipo merge con filtri con parametri
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Quando si usano filtri di riga con parametri nelle pubblicazioni di tipo merge, ogni sottoscrizione con uno snapshot in due parti viene inizializzata dalla replica. Viene innanzitutto creato uno snapshot dello schema contenente tutti gli oggetti necessari alla replica e lo schema degli oggetti pubblicati, ma non i dati. Ogni sottoscrizione viene quindi inizializzata con uno snapshot che include gli oggetti e lo schema dello snapshot dello schema e i dati appartenenti alla partizione della sottoscrizione. Se più di una sottoscrizione riceve una determinata partizione, ovvero riceve lo stesso schema e gli stessi dati, lo snapshot di tale partizione viene creato una sola volta. Dallo stesso snapshot vengono inizializzate più sottoscrizioni. Per ulteriori informazioni sui filtri di riga con parametri, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
 È possibile creare snapshot per pubblicazioni con filtri con parametri in tre modi diversi:  
  
-   Pregenerare uno snapshot per ogni partizione. Questa opzione consente di controllare il momento in cui vengono generati gli snapshot.  
  
     È inoltre possibile aggiornare gli snapshot in base a una pianificazione. I nuovi Sottoscrittori che sottoscrivono una partizione per cui è stato creato uno snapshot riceveranno uno snapshot aggiornato.  
  
-   Consentire ai Sottoscrittori di richiedere la generazione e l'applicazione dello snapshot alla prima sincronizzazione. Questa opzione consente ai nuovi Sottoscrittori di eseguire la sincronizzazione senza l'intervento di un amministratore. Per consentire la generazione dello snapshot, è necessario che[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia in esecuzione nel server di pubblicazione.  
  
    > [!NOTE]  
    >  Se il filtro di uno o più articoli nella pubblicazione restituisce partizioni non sovrapposte univoche per ogni sottoscrizione, i metadati vengono eliminati a ogni esecuzione dell'agente di merge. Lo snapshot partizionato scade quindi più rapidamente. Quando si utilizza questa opzione, è consigliabile consentire ai Sottoscrittori di inizializzare la generazione e il recapito dello snapshot. Per ulteriori informazioni sulle opzioni di filtro, vedere [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
-   Generare manualmente uno snapshot per ogni Sottoscrittore con l'agente snapshot. Il Sottoscrittore deve quindi indicare il percorso dello snapshot all'agente di merge, in modo che sia possibile recuperare e applicare lo snapshot corretto.  
  
    > [!NOTE]  
    >  Questa opzione è supportata per garantire la compatibilità con le versioni precedenti e non consente le condivisioni snapshot FTP.  
  
 Il metodo più flessibile consiste nell'utilizzo di una combinazione di opzioni snapshot pregenerate e richieste dal Sottoscrittore: gli snapshot vengono pregenerati e aggiornati in base a una pianificazione, in genere durante i periodi di minore attività, ma un Sottoscrittore può generare il proprio snapshot nel caso in cui venga creata una sottoscrizione per cui è necessaria una nuova partizione.  
  
 Considerare [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], che dispone di forza lavoro mobile per la distribuzione delle scorte ai singoli negozi. Ogni venditore riceve una sottoscrizione basata sul proprio account di accesso, che consente di recuperare i dati relativi ai negozi serviti. L'amministratore decide di pregenerare gli snapshot e di aggiornarli ogni domenica. Occasionalmente viene aggiunto al sistema un nuovo utente per il quale sono necessari i dati per una partizione per cui non è disponibile alcuno snapshot. L'amministratore decide inoltre di consentire gli snapshot inizializzati dal Sottoscrittore, per evitare che si verifichi una situazione in cui un Sottoscrittore non può sottoscrivere la pubblicazione in quanto lo snapshot non è ancora disponibile. Quando il nuovo Sottoscrittore effettua la prima connessione, lo snapshot per la partizione specificata viene generato e viene applicato al Sottoscrittore. Per consentire la generazione dello snapshot, è necessario che[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia in esecuzione nel server di pubblicazione.  
  
 Per creare uno snapshot per una pubblicazione con filtri con parametri, vedere [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="security-settings-for-the-snapshot-agent"></a>Impostazioni di sicurezza per l'agente snapshot  
 L'agente snapshot crea gli snapshot per ogni partizione. Per gli snapshot pregenerati e per quelli richiesti da un Sottoscrittore, viene eseguito l'agente e vengono effettuate le connessioni con le credenziali specificate al momento della creazione del processo dell'agente snapshot. Tale processo viene creato tramite la Creazione guidata nuova pubblicazione o **sp_addpublication_snapshot**. Per modificare le credenziali, utilizzare **sp_changedynamicsnapshot_job**. Per altre informazioni, vedere [sp_changedynamicsnapshot_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedynamicsnapshot-job-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Inizializzare una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)   
 [Proteggere la cartella snapshot](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
