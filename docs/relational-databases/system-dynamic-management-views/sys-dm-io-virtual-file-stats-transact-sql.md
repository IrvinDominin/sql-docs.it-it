---
title: sys.dm_io_virtual_file_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_io_virtual_file_stats
- sys.dm_io_virtual_file_stats_TSQL
- sys.dm_io_virtual_file_stats
- dm_io_virtual_file_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_virtual_file_stats dynamic management function
ms.assetid: fa3e321f-6fe5-45ff-b397-02a0dd3d6b7d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2ab0b534ceea8712c9c197ea52f2da66065d3167
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmiovirtualfilestats-transact-sql"></a>sys.dm_io_virtual_file_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Restituisce le statistiche di I/O per i file di log e di dati. Questa vista a gestione dinamica sostituisce il [fn_virtualfilestats](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md) (funzione).  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], utilizzare il nome **sys.dm_pdw_nodes_io_virtual_file_stats**. 

## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database

sys.dm_io_virtual_file_stats (   
    { database_id | NULL },  
    { file_id | NULL }  
)  
```  

```  
-- Syntax for Azure SQL Data Warehouse

sys.dm_pdw_nodes_io_virtual_file_stats
```
  
## <a name="arguments"></a>Argomenti  


 *database_id* | NULL

 **Si applica a:** (a partire da 2008) di SQL Server, Database SQL di Azure

 ID del database. *database_id* è di tipo int, non prevede alcun valore predefinito. Gli input validi sono il numero di ID di un database o NULL. Se si specifica NULL, vengono restituiti tutti i database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La funzione predefinita [DB_ID](../../t-sql/functions/db-id-transact-sql.md) può essere specificato.  
  
*file_id* | NULL

**Si applica a:** (a partire da 2008) di SQL Server, Database SQL di Azure
 
ID del file. *file_id* è di tipo int, non prevede alcun valore predefinito. Gli input validi sono il numero di ID di un file o NULL. Se si specifica NULL, vengono restituiti tutti i file nel database.  
  
 La funzione predefinita [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) possono essere specificati e fa riferimento a un file nel database corrente.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Nome del database.</br></br>Per SQL Data Warehouse, questo è il nome del database archiviato nel nodo identificato dal pdw_node_id. Ogni nodo dispone di un database tempdb con 13 file. Ogni database di distribuzione è 5 file ogni nodo dispone di un database per ogni distribuzione. Se, ad esempio, ogni nodo contiene 4 distribuzioni, i risultati mostrano 20 file di database di distribuzione per pdw_node_id. 
|**database_id**|**smallint**|ID del database.|  
|**file_id**|**smallint**|ID di file.|  
|**sample_ms**|**bigint**|Numero di millisecondi dall'avvio del computer. È possibile utilizzare questa colonna per confrontare output diversi di questa funzione.</br></br>Il tipo di dati è **int** per [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|**num_of_reads**|**bigint**|Numero di letture eseguite nel file.|  
|**num_of_bytes_read**|**bigint**|Numero totale di byte letti nel file.|  
|**io_stall_read_ms**|**bigint**|Tempo totale di attesa degli utenti, in millisecondi, per il completamento delle operazioni di lettura nel file.|  
|**num_of_writes**|**bigint**|Numero di scritture eseguite nel file.|  
|**num_of_bytes_written**|**bigint**|Numero totale di byte scritti nel file.|  
|**io_stall_write_ms**|**bigint**|Tempo totale di attesa degli utenti, in millisecondi, per il completamento delle operazioni di scrittura nel file.|  
|**io_stall**|**bigint**|Tempo totale di attesa degli utenti, in millisecondi, per il completamento delle operazioni di I/O nel file.|  
|**size_on_disk_bytes**|**bigint**|Numero di byte utilizzati nel disco per il file. Per i file sparse, questo numero corrisponde al numero effettivo di byte nel disco utilizzati per gli snapshot di database.|  
|**file_handle**|**varbinary**|Handle di file Windows per il file.|  
|**io_stall_queued_read_ms**|**bigint**|**Non si applica a:**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)].<br /><br /> Latenza di I/O totale introdotta dalla governance delle risorse di I/O per le letture. Non ammette i valori Null. Per ulteriori informazioni, vedere [Sys.dm resource_governor_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).|  
|**io_stall_queued_write_ms**|**bigint**|**Non si applica a:**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)].<br /><br />  Latenza di I/O totale introdotta dalla governance delle risorse di I/O per le scritture. Non ammette i valori Null.|
|**pdw_node_id**|**int**|**Si applica a:** [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]</br></br>Identificatore del nodo per la distribuzione.
 
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE. Per ulteriori informazioni, vedere [funzioni e viste a gestione dinamica &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Esempi  

### <a name="a-return-statistics-for-a-log-file"></a>A. Restituisce le statistiche per un file di log

**Si applica a:** (a partire da 2008) di SQL Server, Database SQL di Azure

 Nell'esempio seguente vengono restituite le statistiche per il file di log nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT * FROM sys.dm_io_virtual_file_stats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="b-return-statistics-for-file-in-tempdb"></a>B. Restituire statistiche per il file in tempdb

**Si applica a:** Azure SQL Data Warehouse

```sql
SELECT * FROM sys.dm_pdw_nodes_io_virtual_file_stats 
WHERE database_name = ‘tempdb’ AND file_id = 2;

```

## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [I O relativi a funzioni e viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

