---
title: sys.dm_os_tasks (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
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
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2fd7607fb0e22206ce309bd30427ba3f8dc7631
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmostasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni attività in corso nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_tasks**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary(8)**|Indirizzo di memoria dell'oggetto.|  
|**task_state**|**nvarchar(60)**|Stato dell'attività. I possibili valori sono i seguenti:<br /><br /> PENDING: in attesa di un thread di lavoro.<br /><br /> RUNNABLE: eseguibile, ma in attesa di ricevere un quantum.<br /><br /> RUNNING: esecuzione in corso nell'utilità di pianificazione.<br /><br /> SUSPENDED: è disponibile un thread di lavoro, ma è in attesa di un evento.<br /><br /> DONE: completato.<br /><br /> SPINLOOP: bloccato in uno spinlock.|  
|**context_switches_count**|**int**|Numero di cambi di contesto dell'utilità di pianificazione completati dall'attività.|  
|**pending_io_count**|**int**|Numero di I/O fisici eseguiti dall'attività.|  
|**pending_io_byte_count**|**bigint**|Numero totale di byte degli I/O eseguiti dall'attività.|  
|**pending_io_byte_average**|**int**|Numero medio di byte degli I/O eseguiti dall'attività.|  
|**scheduler_id**|**int**|ID dell'utilità di pianificazione padre. Si tratta di un handle per le informazioni dell'utilità di pianificazione per l'attività. Per ulteriori informazioni, vedere [Sys.dm os_schedulers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID della sessione associata all'attività.|  
|**exec_context_id**|**int**|ID del contesto di esecuzione associato all'attività.|  
|**request_id**|**int**|ID della richiesta dell'attività. Per ulteriori informazioni, vedere [Sys.dm exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary(8)**|Indirizzo di memoria del thread di lavoro che sta eseguendo l'attività.<br /><br /> NULL = Per poter essere eseguita, l'attività è in attesa di un thread di lavoro oppure l'esecuzione dell'attività è stata completata.<br /><br /> Per ulteriori informazioni, vedere [os_workers &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary(8)**|Indirizzo di memoria dell'host.<br /><br /> 0 = Per creare l'attività non è stato utilizzato alcun host. Ciò semplifica l'identificazione dell'host utilizzato per creare l'attività.<br /><br /> Per ulteriori informazioni, vedere [Sys.dm os_hosts &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary(8)**|Indirizzo di memoria dell'attività padre dell'oggetto.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.   
  
## <a name="examples"></a>Esempi  
  
### <a name="a-monitoring-parallel-requests"></a>A. Monitoraggio di richieste in parallelo  
 Per le richieste che vengono eseguite in parallelo, vengono visualizzate più righe per la stessa combinazione di (\<**session_id**>, \< **request_id**>). Utilizzare la seguente query per trovare il [il max degree of parallelism opzione di configurazione Server Configurare](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) per tutte le richieste attive.  
  
> [!NOTE]  
>  Oggetto **request_id** è univoco all'interno di una sessione.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. Associazione di ID di sessione con thread di Windows  
 È possibile utilizzare la query seguente per associare un valore di ID di sessione a un ID di thread di Windows. È possibile monitorare le prestazioni del thread utilizzando Performance Monitor di Windows. La query seguente non restituisce informazioni per le sessioni sospese.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
  [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


