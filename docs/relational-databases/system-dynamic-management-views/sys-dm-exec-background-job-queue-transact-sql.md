---
title: sys.dm_exec_background_job_queue (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_background_job_queue
- sys.dm_exec_background_job_queue_TSQL
- dm_exec_background_job_queue_TSQL
- sys.dm_exec_background_job_queue
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_background_job_queue dynamic management function
ms.assetid: 05d9884f-b74c-4e3c-a23b-c90c1ea5ef02
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d80848491c46046ba260956fb02ce41e7becdd6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecbackgroundjobqueue-transact-sql"></a>sys.dm_exec_background_job_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni processo di Query Processor pianificato per l'esecuzione asincrona (in background).  
  
> **NOTA** Per chiamare questo metodo dal  **[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]**  o  **[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]** , utilizzare il nome **sys.dm_pdw_nodes_exec_background_job_queue**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**time_queued**|**datetime**|Ora in cui il processo viene aggiunto alla coda.|  
|**job_id**|**int**|Identificatore di processo.|  
|**database_id**|**int**|Database in cui il processo viene eseguito.|  
|**object_id1**|**int**|Il valore dipende dal tipo di processo. Per altre informazioni, vedere la sezione Osservazioni.|  
|**object_id2**|**int**|Il valore dipende dal tipo di processo. Per altre informazioni, vedere la sezione Osservazioni.|  
|**object_id3**|**int**|Il valore dipende dal tipo di processo. Per altre informazioni, vedere la sezione Osservazioni.|  
|**object_id4**|**int**|Il valore dipende dal tipo di processo. Per altre informazioni, vedere la sezione Osservazioni.|  
|**error_code**|**int**|Codice di errore nel caso di reinserimento del processo a causa di un errore. È NULL in caso di processo sospeso, non prelevato o completato.|  
|**request_type**|**smallint**|Tipo di richiesta del processo.|  
|**retry_count**|**smallint**|Numero di volte che il processo è stato prelevato dalla coda e reinserito nella coda per mancanza di risorse o altri motivi.|  
|**in_progress**|**smallint**|Indica se è stata avviata l'esecuzione del processo.<br /><br /> 1 = avviato<br /><br /> 0 = Processo in attesa di avvio|  
|**session_id**|**smallint**|Identificatore di sessione.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessaria l'autorizzazione VIEW SERVER STATE nel server.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Premium richiede l'autorizzazione VIEW DATABASE STATE nel database. In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Standard e Basic richiede il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] account amministratore.  
  
## <a name="remarks"></a>Osservazioni  
 In questa vista vengono restituite solo le informazioni relative ai processi asincroni di aggiornamento delle statistiche. Per ulteriori informazioni su aggiornamenti asincroni delle statistiche, vedere [statistiche](../../relational-databases/statistics/statistics.md).  
  
 I valori di **object_id1** tramite **object_id4** dipendono dal tipo della richiesta di processo. Nella tabella seguente viene descritto il significato delle colonne per i diversi tipi di processo.  
  
|Tipo di richiesta|object_id1|object_id2|object_id3|object_id4|  
|------------------|-----------------|-----------------|-----------------|-----------------|  
|Aggiornamenti asincroni delle statistiche|ID di tabella o vista|ID delle statistiche|Non usato|Non usato|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero di processi asincroni attivi nella coda in background per ogni database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT DB_NAME(database_id) AS [Database], COUNT(*) AS [Active Async Jobs]  
FROM sys.dm_exec_background_job_queue  
WHERE in_progress = 1  
GROUP BY database_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica &#40; relative all'esecuzione Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [Statistiche](../../relational-databases/statistics/statistics.md)   
 [KILL STATS JOB &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-stats-job-transact-sql.md)  
  
  



