---
title: sys.dm_os_memory_cache_hash_tables (Transact-SQL) | Microsoft Docs
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
- sys.dm_os_memory_cache_hash_tables_TSQL
- sys.dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables
- dm_os_memory_cache_hash_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_hash_tables dynamic management view
ms.assetid: 68b94f35-8f80-4d2b-bcde-7a21934219af
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d18182e52de0c0324e15b4fa36fb89f57af8209
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmosmemorycachehashtables-transact-sql"></a>sys.dm_os_memory_cache_hash_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni cache attiva nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_memory_cache_hash_tables**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Indirizzo (chiave primaria) della voce nella cache. Non ammette i valori Null.|  
|**name**|**nvarchar(256)**|Nome della cache. Non ammette i valori Null.|  
|**type**|**nvarchar(60)**|Tipo di cache. Non ammette i valori Null.|  
|**table_level**|**int**|Numero di tabella hash. Una cache specifica può avere più tabelle hash corrispondenti a funzioni hash diverse. Non ammette i valori Null.|  
|**buckets_count**|**int**|Numero di bucket nella tabella hash. Non ammette i valori Null.|  
|**buckets_in_use_count**|**int**|Numero di bucket in uso. Non ammette i valori Null.|  
|**buckets_min_length**|**int**|Numero minimo di voci nella cache in un bucket. Non ammette i valori Null.|  
|**buckets_max_length**|**int**|Numero massimo di voci nella cache in un bucket. Non ammette i valori Null.|  
|**buckets_avg_length**|**int**|Numero medio di voci nella cache in ogni bucket. Non ammette i valori Null.|  
|**buckets_max_length_ever**|**int**|Numero massimo di voci nella cache in un hash bucket per la tabella hash corrente dall'avvio del server. Non ammette i valori Null.|  
|**hits_count**|**bigint**|Numero di riscontri nella cache. Non ammette i valori Null.|  
|**misses_count**|**bigint**|Numero di mancati riscontri nella cache. Non ammette i valori Null.|  
|**buckets_avg_scan_hit_length**|**int**|Numero medio di voci controllate in un bucket prima che venga individuato un elemento ricercato. Non ammette i valori Null.|  
|**buckets_avg_scan_miss_length**|**int**|Numero medio di voci controllate in un bucket prima che la ricerca venga conclusa con esito negativo. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|L'identificatore per il nodo che utilizza questo tipo di distribuzione.<br /><br /> **Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
  
## <a name="see-also"></a>Vedere anche  
 
  [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


