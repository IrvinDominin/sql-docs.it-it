---
title: sp_attach_db (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/01/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_attach_db_TSQL
- sp_attach_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_attach_db
ms.assetid: 59bc993e-7913-4091-89cb-d2871cffda95
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b17a11f31faff52e2519d2c10d34af88108f0399
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spattachdb-transact-sql"></a>sp_attach_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Collega un database a un server.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] È consigliabile utilizzare CREATE DATABASE *database_name* FOR ATTACH invece. Per alte informazioni, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
> [!NOTE]  
>  Per ricompilare più file di log quando uno o più dispone di un nuovo percorso, utilizzare CREATE DATABASE *database_name* FOR ATTACH_REBUILD_LOG.  
  
> [!IMPORTANT]  
>  È consigliabile evitare di collegare o ripristinare database provenienti da origini sconosciute o non attendibili. Tali database possono contenere codice dannoso che potrebbe eseguire codice [!INCLUDE[tsql](../../includes/tsql-md.md)] indesiderato o causare errori modificando lo schema o la struttura fisica di database. Prima di usare un database da un'origine sconosciuta o non attendibile, eseguire [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sul database in un server non di produzione ed esaminare anche il codice contenuto nel database, ad esempio le stored procedure o altro codice definito dall'utente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_attach_db [ @dbname= ] 'dbname'  
    , [ @filename1= ] 'filename_n' [ ,...16 ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@dbname=** ] **'***dbnam* **'**  
 Nome del database da collegare al server. Il nome deve essere univoco. *dbname* è **sysname**, con un valore predefinito è NULL.  
  
 [ **@filename1=** ] **'***filename_n***'**  
 Nome fisico, ad esempio il percorso, di un file di database. *filename_n* è **nvarchar (260)**, con un valore predefinito è NULL. È possibile specificare un massimo di 16 nomi di file. I nomi dei parametri  **@filename1**  e di incremento per  **@filename16** . L'elenco dei nomi di file deve includere almeno il file primario, il quale contiene le tabelle di sistema che fanno riferimento ad altri file del database. Tale elenco deve includere inoltre tutti i file spostati dopo lo scollegamento del database.  
  
> [!NOTE]  
>  Questo argomento esegue il mapping al parametro FILENAME dell'istruzione CREATE DATABASE. Per alte informazioni, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
>   
>  Quando si collega un database di [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] contenente file di cataloghi full-text in un'istanza del server di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , i file di catalogo vengono collegati dal percorso precedente insieme agli altri file del database, come in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Per altre informazioni, vedere [Aggiornamento della ricerca full-text](../../relational-databases/search/upgrade-full-text-search.md).  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Il **sp_attach_db** stored procedure deve essere eseguita solo nei database in cui sono stati precedentemente scollegati dal server di database tramite l'impostazione esplicita **sp_detach_db** operazione o in database copiati. Se è necessario specificare più di 16 file, utilizzare CREATE DATABASE *database_name* FOR ATTACH o CREATE DATABASE *database_name* FOR_ATTACH_REBUILD_LOG. Per alte informazioni, vedere [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
 Si presuppone che i file non specificati siano memorizzati nell'ultima posizione nota. Per utilizzare un file in una posizione diversa, è necessario specificare la nuova posizione.  
  
 Un database creato con una versione più recente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può essere collegato con versioni precedenti.  
  
> [!NOTE]  
>  Non è possibile scollegare o collegare uno snapshot del database.  
  
 Quando si collega un database replicato copiato anziché scollegato, è necessario considerare quanto segue:  
  
-   Se si collega il database alla stessa istanza del server e alla stessa versione del database originale, non sono necessari passaggi aggiuntivi.  
  
-   Se si collega il database all'istanza del server stesso, ma con una versione aggiornata, è necessario eseguire [sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md) per aggiornare la replica al termine dell'operazione di collegamento.  
  
-   Se si collega il database a un'istanza di server diverso, indipendentemente dalla versione, è necessario eseguire [sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) per rimuovere la replica al termine dell'operazione di collegamento.  
  
 Quando un database viene collegato per la prima volta a una nuova istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]o ripristinato, nel server non è ancora archiviata una copia della chiave master del database, crittografata dalla chiave master del servizio. È necessario usare l'istruzione **OPEN MASTER KEY** per decrittografare la chiave master del database. Dopo aver decrittografato la DMK, è possibile usare l'istruzione **ALTER MASTER KEY REGENERATE** per abilitare la decrittografia automatica per le operazioni successive, in modo da fornire al server una copia della DMK crittografata con la chiave master del servizio (SMK). Quando un database è stato aggiornato da una versione precedente, la DMK deve essere rigenerata per usare l'algoritmo AES più recente. Per altre informazioni sulla rigenerazione della DMK, vedere [ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md). Il tempo richiesto per rigenerare la chiave DMK e aggiornarla ad AES dipende dal numero di oggetti protetti dalla DMK. È necessario rigenerare la chiave DMK per l'aggiornamento ad AES una sola volta e l'operazione non influenza le rigenerazioni future che fanno parte di una strategia di rotazione della chiave.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per informazioni sulla modalità di gestione delle autorizzazioni quando un database viene collegato, vedere [CREATE DATABASE &#40; SQL Server Transact-SQL &#41; ](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono collegati file da [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] al server corrente.  
  
```  
EXEC sp_attach_db @dbname = N'AdventureWorks2012',   
    @filename1 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_Data.mdf',   
    @filename2 =   
N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Collegamento e scollegamento di un database &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
