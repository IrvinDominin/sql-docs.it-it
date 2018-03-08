---
title: sys.dm_pdw_errors (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: 
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 944eac31-5691-432b-b9f5-f1e11c05191f
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4131409826a4c5dd602a4638c688c9682a1e97d2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwerrors-transact-sql"></a>sys.dm_pdw_errors (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Contiene informazioni su tutti gli errori rilevati durante l'esecuzione di una richiesta o una query.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|error_id|**nvarchar(36)**|Chiave per la visualizzazione.<br /><br /> Id numerico univoco associato all'errore.|È univoco tra tutti gli errori di query nel sistema.|  
|origine|**nvarchar(64)**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|tipo|**nvarchar(4000)**|Tipo di errore che si è verificato.|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|create_time|**datetime**|Ora in cui si è verificato l'errore.|Minore o uguale all'ora corrente.|  
|pwd_node_id|**int**|Identificatore del nodo specifico coinvolte, se presente. Per ulteriori informazioni su ID di nodo, vedere [sys.dm_pdw_nodes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md).||  
|session_id|**nvarchar(32)**|Identificatore della sessione interessata, se presente. Per ulteriori informazioni su ID di sessione, vedere [sys.dm_pdw_exec_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).||  
|request_id|**nvarchar(32)**|Identificatore della richiesta coinvolto, se presente. Per ulteriori informazioni su ID di richiesta, vedere [sys.dm_pdw_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).||  
|spid|**int**|SPID della sessione di SQL Server coinvolte, se presente.||  
|thread_id|**int**|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]||  
|dettagli|**nvarchar(4000)**|Contiene la descrizione di testo di errore completo.||  
  
 Per informazioni sulle righe massimi mantenuto da questa vista, vedere la sezione valori massimi vista di sistema nel [valori minimo e massimo (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste a gestione dinamica Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
