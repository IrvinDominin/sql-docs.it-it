---
title: sys.dm_pdw_diag_processing_stats (Transact-SQL) | Microsoft Docs
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
ms.assetid: df659c55-4f63-45f8-8afe-ce300031bc5b
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ab28a8e13851642b11a5f465365ab2b48b51bd9
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmpdwdiagprocessingstats-transact-sql"></a>sys.dm_pdw_diag_processing_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Visualizza informazioni relative a tutti gli eventi di diagnostica interni che potrebbe essere incorporati nelle sessioni di diagnostica definite dall'amministratore. Query su questa vista per comprendere le statistiche sottostanti la diagnostica e i sottosistemi di gestione degli eventi che determinano la popolazione di tutte le altre DMV. Sono disponibili un gruppo di code per ogni processo in ogni nodo.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|Nodo dispositivo che si trova in questo log.|  
|**process_id**|**int**|Identificatore di processo in esecuzione questa statistica di invio.|  
|**target_name**|**nvarchar(255)**|Nome della coda.|  
|**queue_size**|**int**|Il numero di elementi nella coda dei processi. Le dimensioni della coda sono in genere 0. Un numero positivo indica che il sistema è in sovraccarico e backlog di eventi di compilazione. Un numero positivo nelle altre colonne comporta sistema è danneggiato per tale coda particolare e le relative viste a gestione dinamica.|  
|**lost_events_count**|**bigint**|Il numero di eventi perdita.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e viste a gestione dinamica Parallel Data Warehouse &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
