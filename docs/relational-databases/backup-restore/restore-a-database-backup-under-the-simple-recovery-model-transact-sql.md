---
title: "Ripristinare un backup del database nel modello di recupero con registrazione minima (Transact-SQL) | Microsoft Docs"
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
  - "backup completi [SQL Server]"
  - "ripristini di database [SQL Server], backup completi"
  - "esecuzione del backup dei database [SQL Server], backup completi"
  - "backup dei database [SQL Server], backup completi"
  - "ripristino di database [SQL Server], backup completi"
ms.assetid: a928fa36-e285-476f-9a7b-6840a8bb7283
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# Ripristinare un backup del database nel modello di recupero con registrazione minima (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  In questo argomento viene descritto come ripristinare un backup completo del database.  
  
> [!IMPORTANT]  
>  L'amministratore di sistema che esegue il ripristino del backup completo del database deve essere l'unico utente collegato al database.  
  
## Prerequisiti e indicazioni  
  
-   Per ripristinare un database crittografato, è necessario poter accedere alla chiave asimmetrica o al certificato utilizzato per crittografare il database. Non è possibile effettuare l'operazione di ripristino del database senza almeno uno di questi due elementi. Di conseguenza, il certificato utilizzato per crittografare la chiave di crittografia del database deve essere conservato fino a quando il backup è necessario. Per altre informazioni, vedere [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
-   Per motivi di sicurezza, è consigliabile non collegare o ripristinare database da origini sconosciute o non attendibili. Tali database possono contenere codice dannoso che potrebbe eseguire codice [!INCLUDE[tsql](../../includes/tsql-md.md)] indesiderato o causare errori modificando lo schema o la struttura fisica di database. Prima di usare un database da un'origine sconosciuta o non attendibile, eseguire [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sul database in un server non di produzione ed esaminare anche il codice contenuto nel database, ad esempio le stored procedure o altro codice definito dall'utente.  
  
## Livello di compatibilità del database dopo l'aggiornamento  
 I livelli di compatibilità dei database **tempdb**, **model**, **msdb** e **Resource** vengono impostati sul livello di compatibilità di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dopo l'aggiornamento. Il database di sistema **master** mantiene il livello di compatibilità precedente all'aggiornamento a meno che tale livello non fosse minore di 100. Se il livello di compatibilità di **master** era minore di 100 prima dell'aggiornamento, viene impostato su 100 dopo l'aggiornamento.  
  
 Se il livello di compatibilità di un database utente è 100 o superiore prima dell'aggiornamento, rimane invariato dopo l'aggiornamento. Se il livello di compatibilità è 90 prima dell'aggiornamento, nel database aggiornato viene impostato su 100, ovvero sul livello di compatibilità supportato più basso in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  I nuovi database utente erediteranno il livello di compatibilità del database **model**.  
  
## Procedure  
  
#### Per ripristinare un backup completo del database  
  
1.  Eseguire l'istruzione RESTORE DATABASE per ripristinare il backup completo del database, specificando:  
  
    -   Nome del database da ripristinare.  
  
    -   Il dispositivo di backup da cui viene ripristinato il backup completo del database.  
  
    -   La clausola NORECOVERY, se è disponibile un backup del log delle transazioni o un backup differenziale del database da applicare dopo il ripristino del backup completo del database.  
  
    > [!IMPORTANT]  
    >  Per ripristinare un database crittografato, è necessario poter accedere alla chiave asimmetrica o al certificato utilizzato per crittografare il database. Non è possibile effettuare l'operazione di ripristino del database senza almeno uno di questi due elementi. Di conseguenza, il certificato utilizzato per crittografare la chiave di crittografia del database deve essere conservato fino a quando il backup è necessario. Per altre informazioni, vedere [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md).  
  
2.  Facoltativamente, specificare:  
  
    -   La clausola FILE per identificare il set di backup nel dispositivo di backup da ripristinare.  
  
> [!NOTE]  
>  Se si ripristina un database di una versione precedente a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], il database viene aggiornato automaticamente. In genere, il database diventa subito disponibile. Se tuttavia un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] include indici full-text, questi vengono importati, reimpostati o ricompilati dal processo di aggiornamento, a seconda dell'impostazione della proprietà del server **upgrade_option**. Se l'opzione di aggiornamento è impostata per l'importazione (**upgrade_option** = 2) o la ricompilazione (**upgrade_option** = 0), gli indici full-text non saranno disponibili durante l'aggiornamento. A seconda della quantità di dati indicizzati, l'importazione può richiedere diverse ore, mentre la ricompilazione può risultare dieci volte più lunga. Si noti inoltre che quando l'opzione di aggiornamento è impostata sull'importazione, gli indici full-text associati vengono ricompilati se non è disponibile un catalogo full-text. Per modificare l'impostazione della proprietà del server **upgrade_option**, usare [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md).  
  
## Esempio  
  
### Descrizione  
 In questo esempio viene eseguito un ripristino da nastro del backup completo del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
### Esempio  
  
```  
USE master;  
GO  
RESTORE DATABASE AdventureWorks2012  
   FROM TAPE = '\\.\Tape0';  
GO  
```  
  
## Vedere anche  
 [Ripristini di database completi &#40;modello di recupero con registrazione completa&#41;](../../relational-databases/backup-restore/complete-database-restores-full-recovery-model.md)   
 [Ripristini di database completi &#40;modello di recupero con registrazione minima&#41;](../../relational-databases/backup-restore/complete-database-restores-simple-recovery-model.md)   
 [Backup completo del database &#40;SQL Server&#41;](../../relational-databases/backup-restore/full-database-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)   
 [Informazioni sulla cronologia e sull'intestazione del backup &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-history-and-header-information-sql-server.md)   
 [Ricompilare database di sistema](../../relational-databases/databases/rebuild-system-databases.md)  
  
  