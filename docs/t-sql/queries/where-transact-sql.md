---
title: WHERE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WHERE_TSQL
- WHERE
dev_langs:
- TSQL
helpviewer_keywords:
- retrieving rows
- clauses [SQL Server], WHERE
- WHERE clause, about WHERE clause
- row retrieval [SQL Server], WHERE clause
- WHERE clause
ms.assetid: a8430421-7bce-4fab-a2d2-56c00a3c6fa4
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: c91187d506ab994c654159da24ff0904b0b8b96a
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="where-transact-sql"></a>WHERE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica la condizione di ricerca che deve essere soddisfatta dalle righe restituite da una query.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
[ WHERE <search_condition> ]  
```  
  
## <a name="arguments"></a>Argomenti  
\<*search_condition* > definisce la condizione deve essere soddisfatta per le righe da restituire. Non sono previsti limiti per il numero di predicati che è possibile includere in una condizione di ricerca. Per ulteriori informazioni sulle condizioni di ricerca e predicati, vedere [condizione di ricerca &#40; Transact-SQL &#41; ](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrato come utilizzare alcune condizioni di ricerca comuni nella clausola `WHERE`.  
  
### <a name="a-finding-a-row-by-using-a-simple-equality"></a>A. Ricerca di una riga tramite una semplice uguaglianza  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName = 'Smith' ;  
```  
  
### <a name="b-finding-rows-that-contain-a-value-as-part-of-a-string"></a>B. Ricerca di righe che contengono un valore come parte di una stringa  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE ('%Smi%');  
```  
  
### <a name="c-finding-rows-by-using-a-comparison-operator"></a>C. Ricerca di righe tramite un operatore di confronto  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey  <= 500;  
```  
  
### <a name="d-finding-rows-that-meet-any-of-three-conditions"></a>D. Ricerca di righe che soddisfano una di tre condizioni  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey = 1 OR EmployeeKey = 8 OR EmployeeKey = 12;  
```  
  
### <a name="e-finding-rows-that-must-meet-several-conditions"></a>E. Ricerca di righe che devono soddisfare diverse condizioni  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey <= 500 AND LastName LIKE '%Smi%' AND FirstName LIKE '%A%';  
```  
  
### <a name="f-finding-rows-that-are-in-a-list-of-values"></a>F. Ricerca di righe incluse in un elenco di valori  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName IN ('Smith', 'Godfrey', 'Johnson');  
```  
  
### <a name="g-finding-rows-that-have-a-value-between-two-values"></a>G. Ricerca di righe con un valore compreso tra due valori  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE EmployeeKey Between 100 AND 200;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [Predicates &#40;Transact-SQL&#41;](~/t-sql/queries/predicates.md)   
 [Condizione di ricerca &#40; Transact-SQL &#41;](../../t-sql/queries/search-condition-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)  
  
  


