---
title: Funzioni di aggregazione (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], aggregate
- aggregate functions [SQL Server], about aggregate functions
- summarizing functions
- aggregate functions [SQL Server]
ms.assetid: 0c06ae42-eb0a-4d77-9d74-aa1e7f344009
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e376fccb023a862a71e61a1437a19028758ad200
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="aggregate-functions-transact-sql"></a>Funzioni di aggregazione (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Le funzioni di aggregazione eseguono un calcolo in un set di valori e restituiscono un singolo valore. Ad eccezione di `COUNT`, le funzioni di aggregazione ignorano i valori Null. Le funzioni di aggregazione vengono spesso usate con la clausola GROUP BY dell'istruzione SELECT.
  
Tutte le funzioni di aggregazione sono deterministiche. In altre parole, le funzioni di aggregazione restituiscono lo stesso valore ogni volta che vengono chiamate con un set specifico di valori di input. Per altre informazioni sul determinismo delle funzioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md). La [clausola OVER](../../t-sql/queries/select-over-clause-transact-sql.md) può seguire tutte le funzioni di aggregazione, ad eccezione di GROUPING e GROUPING_ID.
  
Usare le funzioni di aggregazione come espressioni solo nei casi seguenti:
-   Nell'elenco di selezione di un'istruzione SELECT (una sottoquery o una query esterna).  
-   Nella clausola HAVING.  
  
[!INCLUDE[tsql](../../includes/tsql-md.md)] include le funzioni di aggregazione seguenti:
  
|||  
|-|-|  
|[AVG](../../t-sql/functions/avg-transact-sql.md)|[MIN](../../t-sql/functions/min-transact-sql.md)|  
|[CHECKSUM_AGG](../../t-sql/functions/checksum-agg-transact-sql.md)|[SUM](../../t-sql/functions/sum-transact-sql.md)|  
|[COUNT](../../t-sql/functions/count-transact-sql.md)|[STDEV](../../t-sql/functions/stdev-transact-sql.md)|  
|[COUNT_BIG](../../t-sql/functions/count-big-transact-sql.md)|[STDEVP](../../t-sql/functions/stdevp-transact-sql.md)|  
|[GROUPING](../../t-sql/functions/grouping-transact-sql.md)|[STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md)|  
|[GROUPING_ID](../../t-sql/functions/grouping-id-transact-sql.md)|[VAR](../../t-sql/functions/var-transact-sql.md)|  
|[MAX](../../t-sql/functions/max-transact-sql.md)|[VARP](../../t-sql/functions/varp-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche
[Funzioni predefinite &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)  
[Clausola OVER &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
