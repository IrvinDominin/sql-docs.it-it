---
title: sys.dm_pdw_query_stats_xe (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5d551241-db35-4958-b60f-55e996f95c1f
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00109ae27ca0038a6da8f8bd359c3d99d4e84a3f
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwquerystatsxe-transact-sql"></a>sys.dm_pdw_query_stats_xe (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Questa DMV è deprecata e verrà rimossa in una versione futura. In questa versione, restituisce 0 righe.  
  
|Nome colonna|Tipo di dati|Description|Intervallo|  
|-----------------|---------------|-----------------|-----------|  
|evento|**nvarchar(60)**|Chiave per la visualizzazione.||  
|event_id|**nvarchar(36)**|||  
|create_time|**datetime**|||  
|session_id|**int**|L'id per la sessione.|Vedere session_id in [sys.dm_pdw_exec_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md).|  
|cpu|**int**|||  
|reads|**int**|Numero di letture logiche dopo l'avvio dell'evento.||  
|writes|**int**|Numero di scritture logiche dopo l'avvio dell'evento.||  
|sql_text|**nvarchar(4000)**|||  
|client_app_name|**nvarchar(255)**|||  
|tsql_stack|**nvarchar(255)**|||  
|pdw_node_id|**int**|Nodo in cui è in esecuzione questa istanza di Xevent.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste a gestione dinamica Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
