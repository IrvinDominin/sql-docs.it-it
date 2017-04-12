---
title: "Spostamento di un database tramite la funzionalit&#224; di scollegamento e collegamento (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "collegamento di database [SQL Server]"
  - "spostamento di database [SQL Server]"
  - "scollegamento di database [SQL Server]"
  - "riposizionamento di database [SQL Server]"
  - "scollegamento di database [SQL Server]"
  - "collegamento di database [SQL Server]"
ms.assetid: 6732a431-cdef-4f1e-9262-4ac3b77c275e
caps.latest.revision: 47
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 47
---
# Spostamento di un database tramite la funzionalit&#224; di scollegamento e collegamento (Transact-SQL)
  In questo argomento si illustra come spostare un database scollegato in un'altra posizione e come ricollegarlo alla stessa istanza oppure a un'altra istanza del server in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Tuttavia, è consigliabile spostare i database utilizzando la procedura di rilocazione pianificata ALTER DATABASE anziché la funzionalità di scollegamento e collegamento. Per altre informazioni, vedere [Spostare database utente](../../relational-databases/databases/move-user-databases.md).  
  
> [!IMPORTANT]  
>  È consigliabile evitare di collegare o ripristinare database provenienti da origini sconosciute o non attendibili. Tali database possono contenere codice dannoso che potrebbe eseguire codice [!INCLUDE[tsql](../../includes/tsql-md.md)] indesiderato o causare errori modificando lo schema o la struttura fisica di database. Prima di usare un database da un'origine sconosciuta o non attendibile, eseguire [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sul database in un server non di produzione ed esaminare anche il codice contenuto nel database, ad esempio le stored procedure o altro codice definito dall'utente.  
  
## Procedura  
  
#### Per spostare un database utilizzando la funzionalità di scollegamento e collegamento  
  
1.  Scollegare il database. Per altre informazioni, vedere [Scollegare un database](../../relational-databases/databases/detach-a-database.md).  
  
2.  In Esplora risorse o in una finestra del prompt dei comandi di Windows spostare nella nuova posizione il file o i file del database scollegato e i relativi file di log.  
  
    > [!NOTE]  
    >  Per spostare un database composto da un singolo file è possibile utilizzare la posta elettronica se le dimensioni del file sono sufficientemente ridotte.  
  
     È consigliabile spostare i file di log anche se si prevede di crearne di nuovi. In alcuni casi, per il ricollegamento di un database sono necessari i file di log esistenti. Mantenere pertanto sempre tutti i file di log scollegati fino a quando il database non è stato collegato senza di essi.  
  
    > [!NOTE]  
    >  Se si tenta di collegare il database senza specificare il file di log, verrà eseguita una ricerca di tale file nella relativa posizione originale. Se nella posizione originale esiste ancora una copia del log, verrà collegata tale copia. Per evitare di utilizzare il file di log originale, specificare il percorso del nuovo file di log oppure rimuovere la copia originale del file di log dopo averlo copiato nella nuova posizione.  
  
3.  Collegare i file copiati. Per altre informazioni, vedere [Attach a Database](../../relational-databases/databases/attach-a-database.md).  
  
## Esempio  
 Nell'esempio seguente si crea una copia del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] denominata `MyAdventureWorks`. Le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono eseguite in una finestra dell'editor di query connessa all'istanza del server a cui è collegata.  
  
1.  Scollegare il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] eseguendo le istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti:  
  
    ```  
    USE master;  
    GO  
    EXEC sp_detach_db @dbname = N'AdventureWorks2012';  
    GO  
    ```  
  
2.  Copiare i file di database (AdventureWorks208R2_Data.mdf e AdventureWorks208R2_log) rispettivamente in: C:\MySQLServer\AdventureWorks208R2_Data.mdf e C:\MySQLServer\AdventureWorks208R2_Log.ldf, utilizzando il metodo desiderato.  
  
    > [!IMPORTANT]  
    >  Nel caso di un database di produzione, posizionare su dischi separati il database e il log delle transazioni.  
  
     Per copiare i file in rete su un disco di un computer remoto, utilizzare il nome UNC (Universal Naming Convention) della posizione remota. Il formato di un nome UNC è **\\\\***Servername***\\***Sharename***\\***Path***\\***Filename*. Come per la scrittura di file nel disco rigido locale, è necessario che l'account utente utilizzato dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponga delle autorizzazioni appropriate per la lettura o la scrittura di un file nel disco remoto.  
  
3.  Collegare il database spostato e, facoltativamente, collegare il relativo log tramite l'esecuzione delle istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] seguenti:  
  
    ```  
    USE master;  
    GO  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Data.mdf'),  
        (FILENAME = 'C:\MySQLServer\AdventureWorks2012_Log.ldf')  
        FOR ATTACH;  
    GO  
    ```  
  
     In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] un database appena collegato non è immediatamente visibile in Esplora oggetti. Per visualizzarlo, in Esplora oggetti scegliere **Aggiorna** dal menu **Visualizza**. Quando si espande il nodo **Database** in Esplora oggetti, il database appena collegato viene visualizzato nell'elenco dei database.  
  
## Vedere anche  
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
  