---
title: "Backup e ripristino di database abilitati per l&#39;estensione | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Estensione database, backup"
  - "backup (Estensione database)"
ms.assetid: 18f0dff0-d8ce-4bee-a935-76ed6dfb3208
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Backup e ripristino di database abilitati per l&#39;estensione
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

 I backup di database consentono di eseguire un ripristino in seguito a diversi tipi di errori e guasti.  
  
 -   È necessario eseguire il backup dei database di SQL Server abilitati per l'estensione.  
      
 -   Microsoft Azure esegue automaticamente il backup dei dati remoti di cui Estensione database ha eseguito la migrazione da SQL Server ad Azure.  

> [!TIP] Il backup è solo una parte di una soluzione di continuità aziendale e a disponibilità elevata completa. Per altre informazioni sulla disponibilità elevata, vedere [Soluzioni a disponibilità elevata](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).
   
## Backup dei dati di SQL Server  
  
Per eseguire il backup dei database di SQL Server abilitati per l'estensione è possibile continuare a usare i metodi di backup di SQL Server già in uso. Per altre informazioni, vedere [Backup e ripristino di database SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).
  
 I backup di un database abilitato per l'estensione contengono solo dati locali e dati idonei per la migrazione della data e dell'ora in cui viene eseguito il backup. I dati idonei sono dati non ancora trasferiti ma che verranno trasferiti in Azure in base alle impostazioni di migrazione delle tabelle. Si tratta di un backup **shallow** che non include i dati di cui è già stata eseguita la migrazione in Azure.  
  
## Backup dei dati di Azure remoti   
  
Microsoft Azure esegue automaticamente il backup dei dati remoti di cui Estensione database ha eseguito la migrazione da SQL Server ad Azure.    
### Azure riduce il rischio di perdita di dati con il backup automatico  
Il servizio Estensione database di SQL Server in Azure protegge i database remoti con snapshot di archiviazione automatici almeno ogni 8 ore. Ogni snapshot viene conservato per 7 giorni per offrire più punti di ripristino.  
  
### Azure riduce il rischio di perdita di dati con la ridondanza geografica  
I backup dei database di Azure vengono memorizzati nell'archiviazione con ridondanza geografica e accesso in lettura (RA-GRS) di Azure e hanno quindi ridondanza geografica per impostazione predefinita. L'archiviazione con ridondanza geografica replica i dati in un'area secondaria a centinaia di miglia di distanza dall'area primaria. Nelle aree primaria e secondaria i dati vengono replicati tre volte in domini di errore e domini di aggiornamento separati. Ciò garantisce la durabilità dei dati anche in caso di interruzione o guasto totale che rende una delle aree di Azure non disponibile.

### <a name="stretchRPO"></a>Estensione database riduce il rischio di perdita dei dati di Azure con il mantenimento temporaneo delle righe migrate
Dopo aver effettuato la migrazione delle righe idonee da SQL Server ad Azure, Estensione database mantiene le righe nella tabella di gestione temporanea per un minimo di 8 ore. Se si ripristina un backup del database di Azure, Estensione database usa le righe salvate nella tabella di gestione temporanea per risolvere le differenze tra il database di SQL Server e il database di Azure.

Dopo aver ripristinato un backup dei dati di Azure, è necessario eseguire la stored procedure [sys.sp_rda_reauthorize_db](../../relational-databases/system-stored-procedures/sys-sp-rda-reauthorize-db-transact-sql.md) per riconnettere il database di SQL Server abilitato per l'estensione al database di Azure remoto. Quando si esegue **sys.sp_rda_reauthorize_db**, Estensione database risolve automaticamente le differenze tra il database di SQL Server e il database di Azure.

Per aumentare il numero di ore dei dati migrati mantenuti temporaneamente da Estensione database nella tabella di gestione temporanea, eseguire la stored procedure [sys.sp_rda_set_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md) e specificare un numero di ore maggiore di 8. Per decidere la quantità di dati da mantenere, considerare quanto segue:
-   La frequenza dei backup automatici di Azure (almeno ogni 8 ore).
-   Il tempo necessario dal momento in cui si è verificato il problema per individuarlo e decidere di ripristinare un backup.
-   La durata dell'operazione di ripristino di Azure.

> [!NOTE] L'aumento della quantità di dati mantenuta temporaneamente da Estensione database nella tabella di gestione temporanea incrementa la quantità di spazio necessario in SQL Server.

Per controllare il numero di ore di dati mantenuto temporaneamente da Estensione database nella tabella di gestione temporanea, eseguire la stored procedure [sys.sp_rda_get_rpo_duration](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md).

## Vedere anche  
[Restore Stretch-enabled databases (Ripristinare database abilitati per l'estensione)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
 [Gestione e risoluzione dei problemi di Estensione database](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md)   
   
  
  