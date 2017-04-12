---
title: "Recupero di un database senza ripristino dei dati (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ripristino [SQL Server], solo recupero"
  - "scenario di solo recupero [SQL Server]"
  - "ripristino di database [SQL Server], solo recupero"
  - "recupero [SQL Server], solo recupero"
  - "recupero del database [SQL Server]"
  - "ripristini di database [SQL Server], solo recupero"
  - "recupero [SQL Server], senza ripristinare i dati"
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# Recupero di un database senza ripristino dei dati (Transact-SQL)
  Generalmente, tutti i dati in un database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono ripristinati prima che venga recuperato il database. È tuttavia possibile che un'operazione di ripristino recuperi il database senza ripristinare effettivamente un backup, ad esempio nel caso di recupero di un file di sola lettura compatibile con il database. Questa operazione viene definita *ripristino con solo recupero*. Quando i dati offline sono già compatibili con il database è necessario solo renderli disponibili; un'operazione di ripristino con solo recupero completa il recupero del database e porta i dati online.  
  
 Un ripristino con solo recupero può essere eseguito per un intero database, per uno o più file o filegroup.  
  
## Ripristino del database con solo recupero  
 Un ripristino di database con solo recupero può risultare utile nelle situazioni seguenti:  
  
-   Il database non è stato recuperato durante il ripristino dell'ultimo backup in una sequenza di ripristino e ora si desidera recuperare il database per attivare la modalità online.  
  
-   Il database è in modalità standby e si desidera renderlo aggiornabile senza applicare un ulteriore backup del log.  
  
 La sintassi dell'istruzione [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) per un ripristino di database con solo recupero è la seguente:  
  
 RESTORE DATABASE *nome_database* WITH RECOVERY  
  
> [!NOTE]  
>  La clausola FROM **=** \<*dispositivo_backup>* non viene usata per i ripristini con solo recupero perché il backup non è necessario.  
  
 **Esempio**  
  
 Nel seguente esempio viene recuperato il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] durante un'operazione di recupero senza eseguire il ripristino dei dati.  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## Ripristino del file con solo recupero  
 Un ripristino di file con solo recupero può risultare utile nella situazione seguente:  
  
 Viene eseguito il ripristino a fasi di un database. Dopo il ripristino del filegroup primario, uno o più file non ripristinati sono consistenti con il nuovo stato del database, ad esempio perché è stato mantenuto l'accesso in sola lettura per un certo periodo di tempo. È pertanto sufficiente recuperare questi file senza eseguire un'operazione di copia dei dati.  
  
 Un'operazione di ripristino con solo recupero attiva la modalità online per i dati del filegroup offline. Non è prevista alcuna fase di copia dei dati, di rollforward o di rollback. Per informazioni sulle fasi del ripristino, vedere [Panoramica del ripristino e del recupero &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
 La sintassi dell'istruzione [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) per un ripristino del file con solo recupero è la seguente:  
  
 RESTORE DATABASE *nome_database* { FILE **=***nome_file_logico* | FILEGROUP **=***nome_filegroup_logico* }[ **,**...*n* ] WITH RECOVERY  
  
 **Esempio**  
  
 Nell'esempio riportato di seguito, viene illustrato un ripristino di file con solo recupero, dei file presenti in un filegroup secondario, `SalesGroup2`, nel database `Sales`. Il filegroup primario è già stato ripristinato durante la fase iniziale di un ripristino a fasi e `SalesGroup2` è consistente con il filegroup primario ripristinato. Per recuperare questo filegroup e attivare la modalità online, è sufficiente una singola istruzione.  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## Esempi di completamento di uno scenario di ripristino frammentario con un ripristino con solo recupero  
 **Modello di recupero con registrazione minima**  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di filegroup selezionati &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 **Modello di recupero con registrazione completa**  
  
-   [Esempio: Ripristino a fasi di un database &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Esempio: Ripristino a fasi di filegroup selezionati &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## Vedere anche  
 [Ripristino in linea &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Ripristini a fasi &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Ripristini di file &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Ripristini di file &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  