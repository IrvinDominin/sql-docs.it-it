---
title: sys.dm_fts_memory_buffers (Transact-SQL) | Microsoft Docs
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
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 190d564ec27cf7921fbfbd9d6e85fc594b77c2d6
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sui buffer di memoria appartenenti a uno specifico pool di memoria utilizzati in una ricerca o in un intervallo di ricerche per indicizzazione full-text.  
  
> [!NOTE]
> La colonna seguente verrà rimossa in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**. Evitare l'utilizzo di questa colonna in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è implementata.  

  
|Colonna|Tipo di dati|Description|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|ID del pool di memoria allocato.<br /><br /> 0 = Buffer di piccole dimensioni<br /><br /> 1 = Buffer di grandi dimensioni|  
|**memory_address**|**varbinary(8)**|Indirizzo del buffer di memoria allocato.|  
|**name**|**nvarchar(4000)**|Nome del buffer di memoria condivisa per cui è stata eseguita questa allocazione.|  
|**is_free**|**bit**|Stato corrente del buffer di memoria.<br /><br /> 0 = Libero<br /><br /> 1 = Occupato|  
|**row_count**|**int**|Numero di righe gestite dal buffer.|  
|**bytes_used**|**int**|Quantità, espressa in byte, di memoria utilizzata nel buffer.|  
|**percent_used**|**int**|Percentuale della memoria allocata utilizzata.|  
  
## <a name="permissions"></a>Autorizzazioni  
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], richiede `VIEW SERVER STATE` autorizzazione.   
In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, è necessario il `VIEW DATABASE STATE` autorizzazione per il database. In [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Standard e Basic, è necessario il **amministratore del Server** o **amministratore di Azure Active Directory** account.  
 
## <a name="physical-joins"></a>Join fisici  
 ![Join significativi di questa vista a gestione dinamica](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "join significativi di questa vista a gestione dinamica")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|From|Per|Relazione|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|Molti-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Ricerca full-Text e funzioni e viste a gestione dinamica della ricerca semantica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

