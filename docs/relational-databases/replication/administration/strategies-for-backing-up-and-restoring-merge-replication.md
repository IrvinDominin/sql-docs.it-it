---
title: "Strategie di backup e ripristino della replica di tipo merge | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "recupero [replica di SQL Server], replica di tipo merge"
  - "backup [replica di SQL Server], replica di tipo merge"
  - "ripristino [replica di SQL Server], replica di tipo merge"
  - "replica di tipo merge [replica di SQL Server], backup e ripristino"
ms.assetid: b8ae31c6-d76f-4dd7-8f46-17d023ca3eca
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 48
---
# Strategie di backup e ripristino della replica di tipo merge
  Per la replica di tipo merge, eseguire periodicamente il backup dei database seguenti:  
  
-   Database di pubblicazione nel server di pubblicazione.  
  
-   Database di distribuzione nel server di distribuzione.  
  
-   Database di sottoscrizione in ogni Sottoscrittore.  
  
-   Database di sistema **master** e **msdb** nel server di pubblicazione, nel database di distribuzione e in tutti i Sottoscrittori. È necessario che il backup di questi database venga eseguito contemporaneamente e che venga inoltre eseguito nello stesso momento di quello del relativo database di replica. Eseguire, ad esempio, il backup dei database **master** e **msdb** nel server di pubblicazione nello stesso momento in cui si esegue il backup del database di pubblicazione. Se il database di pubblicazione viene ripristinato, verificare che i database **master** e **msdb** siano consistenti con il database di pubblicazione in termini di impostazioni e di configurazione della replica.  
  
 Se si eseguono backup regolari del log, le eventuali modifiche correlate alla replica dovrebbero essere incluse nei backup del log. Se non si eseguono backup del log, è necessario eseguire un backup ogni volta che viene modificata un'impostazione relativa alla replica. Per altre informazioni, vedere [Common Actions Requiring an Updated Backup](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md).  
  
 Scegliere una delle modalità descritte di seguito per eseguire il backup e il ripristino del database di pubblicazione e quindi attenersi alle indicazioni elencate per il database di distribuzione e i database di sottoscrizione.  
  
## Backup e ripristino del database di pubblicazione  
 Per il ripristino di un database di pubblicazione di tipo merge, sono disponibili due modalità. Dopo avere ripristinato il database di pubblicazione da un backup, sarà necessario eseguire una delle operazioni seguenti:  
  
-   Sincronizzare il database di pubblicazione con un database di sottoscrizione.  
  
-   Reinizializzare tutte le sottoscrizioni delle pubblicazioni nel database di pubblicazione.  
  
 L'utilizzo di una di queste modalità assicura che dopo l'esecuzione di un ripristino il server di pubblicazione e tutti i Sottoscrittori siano sincronizzati.  
  
> [!NOTE]  
>  Se alcune tabelle contengono colonne Identity, sarà necessario verificare che dopo un ripristino vengano assegnati gli intervalli corretti di valori Identity. Per ulteriori informazioni, vedere [replicare colonne Identity](../../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
### Sincronizzazione del database di pubblicazione  
 La sincronizzazione di un database di pubblicazione con un database di sottoscrizione consente di caricare da uno o più database di sottoscrizione le modifiche apportate in precedenza al database di pubblicazione, ma non rappresentate nel backup ripristinato. I dati che è possibile caricare dipendono dal modo in cui una pubblicazione è filtrata:  
  
-   Se la pubblicazione non è filtrata, sarà possibile aggiornare il database di pubblicazione eseguendo la sincronizzazione con il Sottoscrittore più aggiornato.  
  
-   Se la pubblicazione è filtrata, l'aggiornamento del database di pubblicazione potrebbe non essere possibile. Considerare una tabella partizionata in modo che ogni sottoscrizione riceva i dati relativi ai clienti solo per una singola area: Nord, Est, Sud e Ovest. Se per ogni partizione di dati è disponibile almeno un Sottoscrittore, la sincronizzazione con un Sottoscrittore per ogni partizione dovrebbe consentire di aggiornare il database di pubblicazione. Tuttavia, se ad esempio i dati nella partizione Ovest non sono stati replicati in alcun Sottoscrittore, questi dati nel server di pubblicazione non potranno essere aggiornati.  
  
> [!IMPORTANT]  
>  Il ripristino delle tabelle pubblicate in seguito alla sincronizzazione di un database di pubblicazione con un database di sottoscrizione può avvenire in un momento più recente rispetto ad altre tabelle non pubblicate di cui è stato ripristinato il backup.  
  
 Se si sincronizza con un server di sottoscrizione che esegue una versione di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], la sottoscrizione non può essere anonima, ma deve essere una sottoscrizione client o server (definito per le sottoscrizioni locali e globali nelle versioni precedenti).  
  
 Per sincronizzare una sottoscrizione, vedere [sincronizzare una sottoscrizione Push](../../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizzare una sottoscrizione Pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
### Reinizializzazione di tutte le sottoscrizioni  
 La reinizializzazione di tutte le sottoscrizioni garantisce che tutti i Sottoscrittori siano in uno stato consistente con il database di pubblicazione ripristinato. È necessario utilizzare questo approccio se si desidera ripristinare lo stato precedente di un'intera topologia, rappresentato dal backup di un determinato database di pubblicazione. È ad esempio possibile reinizializzare tutte le sottoscrizioni se si ripristina lo stato precedente di un database di pubblicazione al fine di correggere un'operazione batch eseguita in modo errato.  
  
 Se si sceglie questa opzione, generare un nuovo snapshot per il recapito ai Sottoscrittori reinizializzati subito dopo aver ripristinato il database di pubblicazione.  
  
 Per reinizializzare una sottoscrizione, vedere [reinizializzare una sottoscrizione](../../../relational-databases/replication/reinitialize-a-subscription.md).  
  
 Per creare e applicare uno snapshot, vedere [creare e applicare lo Snapshot iniziale](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md) e [creare uno Snapshot per una pubblicazione di tipo Merge con filtri con parametri](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## Backup e ripristino del database di distribuzione  
 Con la replica di tipo merge, è necessario eseguire backup periodici del database di distribuzione, che può essere ripristinato senza particolari attenzioni a condizione che il backup utilizzato non sia precedente al periodo di memorizzazione più breve di tutte le pubblicazioni in cui viene utilizzato il server di distribuzione. Se, ad esempio, vi sono tre pubblicazioni il cui periodo di memorizzazione è pari a 10, 20 e 30 giorni rispettivamente, la copia di backup utilizzata per il ripristino del database non deve avere più di 10 giorni. Il database di distribuzione svolge un ruolo limitato nella replica di tipo merge: non viene utilizzato per archiviare dati utilizzati nel rilevamento delle modifiche e non consente l'archiviazione temporanea delle modifiche della replica di tipo merge per il successivo inoltro ai database di sottoscrizione, come invece avviene nella replica transazionale.  
  
## Backup e ripristino di un database di sottoscrizione  
 Per garantire il corretto recupero di un database di sottoscrizione, è necessario che i Sottoscrittori vengano sincronizzati con il server di pubblicazione prima di eseguire il backup del database di sottoscrizione. La sincronizzazione deve avvenire anche dopo che il database di sottoscrizione è stato ripristinato:  
  
-   La sincronizzazione con il server di pubblicazione prima di un backup del database di sottoscrizione consente di garantire che, nel caso in cui un Sottoscrittore venga ripristinato dal backup, la sottoscrizione sia ancora compresa nel periodo di memorizzazione della pubblicazione. Si supponga, ad esempio, che il periodo di memorizzazione di una pubblicazione sia pari a 10 giorni. L'ultima sincronizzazione è stata eseguita 8 giorni prima e al momento viene eseguito il backup. Se il backup viene ripristinato dopo quattro giorni, l'ultima sincronizzazione risalirà a dodici giorni prima, ovvero il periodo di memorizzazione è già trascorso. In questo caso, sarà necessario reinizializzare il Sottoscrittore. Se il Sottoscrittore fosse stato sincronizzato prima del backup, il database di sottoscrizione sarebbe rientrato nel periodo di memorizzazione.  
  
     È necessario che il backup non sia precedente al periodo di memorizzazione più breve di tutte le pubblicazioni di cui il Sottoscrittore effettua la sottoscrizione. Se, ad esempio, un Sottoscrittore sottoscrive tre pubblicazioni i cui periodi di memorizzazione sono di 10, 20 e 30 giorni rispettivamente, il backup utilizzato per il ripristino del database non deve avere più di 10 giorni.  
  
-   La sincronizzazione del database di sottoscrizione con ognuna delle relative pubblicazioni dopo un ripristino garantisce che il Sottoscrittore sia aggiornato con tutte le modifiche apportate nel server di pubblicazione.  
  
 Per impostare il periodo di memorizzazione della pubblicazione, vedere [impostare il periodo di scadenza per le sottoscrizioni](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md).  
  
 Per sincronizzare una sottoscrizione, vedere [sincronizzare una sottoscrizione Push](../../../relational-databases/replication/synchronize-a-push-subscription.md) e [sincronizzare una sottoscrizione Pull](../../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
## Backup e ripristino di un database di ripubblicazione  
 Un database che sottoscrive i dati di un server di pubblicazione e a sua volta li pubblica in altri database di sottoscrizione viene definito database di ripubblicazione. Per ripristinare un database di ripubblicazione, seguire le indicazioni disponibili nelle sezioni "Backup e ripristino del database di pubblicazione" e "Backup e ripristino di un database di sottoscrizione" in questo argomento.  
  
## Vedere anche  
 [Backup e ripristino di database SQL Server](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Backup e ripristino di database replicati](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)  
  
  