---
title: sp_query_store_remove_query (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/29/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SP_QUERY_STORE_REMOVE_QUERY
- SP_QUERY_STORE_REMOVE_QUERY_TSQL
- SYS.SP_QUERY_STORE_REMOVE_QUERY
- SYS.SP_QUERY_STORE_REMOVE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_query_store_remove_query
- sp_query_store_remove_query
ms.assetid: cc39ca92-3cba-478e-beef-65560aa84007
caps.latest.revision: 8
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ad280acf3f473c8bd38771cc515d311b7c65dd05
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spquerystoreremovequery-transact-sql"></a>sp_query_store_remove_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Rimuove la query, nonché tutti i piani e statistiche di runtime dall'archivio query.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_query_store_remove_query [ @query_id = ] query_id [;]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@query_id =** ] *query_id*  
 È l'id della query deve essere rimosso dall'archivio query. *query_id* è un **bigint**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **EXECUTE** autorizzazione per il database, e **eliminare** autorizzazione sulle viste del catalogo di archivio query.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce informazioni sulle query in archivio query.  
  
```  
SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*  
FROM sys.query_store_plan AS Pl  
JOIN sys.query_store_query AS Qry  
    ON Pl.query_id = Qry.query_id  
JOIN sys.query_store_query_text AS Txt  
    ON Qry.query_text_id = Txt.query_text_id ;  
```  
  
 Dopo aver identificato query_id che si desidera eliminare, utilizzare l'esempio seguente per eliminare la query.  
  
 Esempio seguente.  
  
```  
EXEC sp_query_store_remove_query 3;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_query_store_force_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-force-plan-transact-sql.md)   
 [sp_query_store_remove_plan &#40;Transct-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-remove-plan-transct-sql.md)   
 [sp_query_store_unforce_plan &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-unforce-plan-transact-sql.md)   
 [sp_query_store_reset_exec_stats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-reset-exec-stats-transact-sql.md)   
 [sp_query_store_flush_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-query-store-flush-db-transact-sql.md)   
 [Viste del catalogo di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)   
 [Monitoraggio delle prestazioni con Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)  
  
  
