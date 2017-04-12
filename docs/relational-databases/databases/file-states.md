---
title: "Stati dei file | Microsoft Docs"
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
  - "restoring - stato di file [SQL Server]"
  - "verifica degli stati di file"
  - "stati correnti di file"
  - "verifica degli stati di filegroup"
  - "stati di file [SQL Server]"
  - "online - stato di file"
  - "offline - stato di file [SQL Server]"
  - "visualizzazione degli stati di filegroup"
  - "visualizzazione degli stati di file"
  - "suspect - stato di file"
  - "recovering - stato di file [SQL Server]"
  - "stato corrente di filegroup"
  - "recupero in sospeso - stato di file [SQL Server]"
  - "visualizzazione di stati di file"
  - "stati [SQL Server], file"
  - "visualizzazione di stati di filegroup"
  - "defunct - stato di file"
ms.assetid: b426474d-8954-4df0-b78b-887becfbe8d6
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Stati dei file
  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lo stato di un file di database viene gestito in modo indipendente dallo stato del database. Lo stato di un file è sempre specifico, ad esempio ONLINE o OFFLINE. Per visualizzare lo stato corrente di un file, usare la vista del catalogo [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) o [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md). Se il database è offline, lo stato dei file è indicato nella vista del catalogo [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md).  
  
 Lo stato dei file di un filegroup determina la disponibilità dell'intero filegroup. Un filegroup è disponibile se tutti i file in esso inclusi sono online. Per visualizzare lo stato corrente di un filegroup, usare la vista del catalogo [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md). Se un filegroup è offline e si tenta di accedervi tramite un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)], l'operazione avrà esito negativo e verrà restituito un errore. Quando Query Optimizer compila i piani di query per le istruzioni SELECT, evita gli indici non cluster e le viste cluster incluse nei filegroup offline, lasciando che queste istruzioni vengano eseguite. Se tuttavia il filegroup offline contiene l'indice cluster o heap della tabella di destinazione, l'istruzione SELECT avrà esito negativo, così come tutte le istruzioni INSERT, UPDATE o DELETE che implicano la modifica di una tabella tramite un indice incluso in un filegroup offline.  
  
## Definizioni degli stati del file  
 Nella tabella seguente sono riportate le definizioni degli stati del file.  
  
|State|Definizione|  
|-----------|----------------|  
|ONLINE|Il file è disponibile per tutte le operazioni. I file del filegroup primario sono sempre online se il database stesso è online. Se un file del filegroup primario non è online, il database non sarà online e gli stati dei file secondari risulteranno indefiniti.|  
|OFFLINE|Il file non è accessibile e potrebbe non essere presente sul disco. I file vengono portati offline a seguito di un'azione esplicita da parte dell'utente e rimangono tali finché l'utente non interviene.<br /><br /> **\*\* Attenzione \*\*** Un file deve essere portato offline solo se è danneggiato, ma può essere ripristinato. Per riportare online un file impostato su offline, è necessario ripristinare il file dal backup. Per altre informazioni sul ripristino di un singolo file, vedere [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md).|  
|RESTORING|Il file è in fase di ripristino. Questo stato indica che è stato eseguito un comando di ripristino che interessa l'intero file e non solo una pagina e rimarrà attivo fino al completamento dell'operazione di ripristino e di recupero del file.|  
|RECOVERY PENDING|Il recupero del file è stato posticipato. Questo stato viene attivato automaticamente durante un processo di ripristino a fasi in cui il file non viene ripristinato e recuperato. Per risolvere l'errore e consentire il completamento del processo di recupero, è necessario un ulteriore intervento da parte dell'utente. Per altre informazioni, vedere [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md).|  
|SUSPECT|Non è stato possibile recuperare il file durante un processo di ripristino online. Se il file è incluso nel filegroup primario, anche il database viene contrassegnato come suspect, ovvero sospetto. In caso contrario, solo il file sarà sospetto mentre il database risulterà ancora online.<br /><br /> Lo stato suspect rimarrà attivo finché il file non viene reso disponibile mediante uno dei metodi seguenti:<br /><br /> Ripristino e recupero<br /><br /> DBCC CHECKDB con REPAIR_ALLOW_DATA_LOSS|  
|DEFUNCT|Il file è stato eliminato quando non era online. Lo stato di tutti i file di un filegroup è defunct quando si rimuove un filegroup offline.|  
  
## Contenuto correlato  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
 [Stati del database](../../relational-databases/databases/database-states.md)  
  
 [Stati di mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
 [Filegroup e file di database](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  