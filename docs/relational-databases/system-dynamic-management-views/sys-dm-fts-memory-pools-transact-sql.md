---
title: sys.dm_fts_memory_pools (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools_TSQL
- sys.dm_fts_memory_pools
- dm_fts_memory_pools
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_pools dynamic management view
ms.assetid: 24747239-cd78-4d55-a00a-19233a457f42
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 02b742ae19835ef9167351bac9db6f53cfb5b08d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsmemorypools-transact-sql"></a>sys.dm_fts_memory_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sui pool di memoria condivisi disponibili per il componente gatherer full-text per una ricerca o un intervallo di ricerche per indicizzazione full-text.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|ID del pool di memoria allocato.<br /><br /> 0 = Buffer di piccole dimensioni<br /><br /> 1 = Buffer di grandi dimensioni|  
|**buffer_size**|**int**|Dimensioni di ogni buffer allocato nel pool di memoria.|  
|**min_buffer_limit**|**int**|Numero minimo di buffer consentiti nel pool di memoria.|  
|**max_buffer_limit**|**int**|Numero massimo di buffer consentiti nel pool di memoria.|  
|**buffer_count**|**int**|Numero corrente di buffer di memoria condivisa nel pool di memoria.|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  

## <a name="physical-joins"></a>Join fisici  
 ![Join significativi di questa vista a gestione dinamica](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-pools-1.gif "join significativi di questa vista a gestione dinamica")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|Molti-a-uno|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la memoria condivisa totale utilizzata dal componente [!INCLUDE[msCoName](../../includes/msconame-md.md)]gatherer full-text del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
```  
SELECT SUM(buffer_size * buffer_count) AS "total memory"   
    FROM sys.dm_fts_memory_pools;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca full-Text e funzioni e viste a gestione dinamica della ricerca semantica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
