---
title: OPTION Clause (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
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
- OPTION clause
- OPTION_TSQL
- OPTION
- OPTION_clause_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- clauses [SQL Server], OPTION
- OPTION clause
ms.assetid: f47e2f3f-9302-4711-9d66-16b1a2a7ffe3
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cf74a87408ca73229636f3e4ad341838c861bc43
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="option-clause-transact-sql"></a>Clausola OPTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica che l'hint per la query indicato deve essere utilizzato in tutta la query. Sono consentiti più hint per la query. Ogni hint, tuttavia, può essere specificato una sola volta. In una istruzione è consentito utilizzare una sola clausola OPTION.  
  
 La clausola può essere specificata nelle istruzioni SELECT, DELETE, UPDATE e MERGE.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ OPTION ( <query_hint> [ ,...n ] ) ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
OPTION ( <query_option> [ ,...n ] )  
  
<query_option> ::=  
    LABEL = label_name |  
    <query_hint>  
  
<query_hint> ::=  
    HASH JOIN   
    | LOOP JOIN   
    | MERGE JOIN  
    | FORCE ORDER  
    | { FORCE | DISABLE } EXTERNALPUSHDOWN  
```  
  
## <a name="arguments"></a>Argomenti  
 *query_hint*  
 Parole chiave che indicano quali hint di ottimizzazione vengono utilizzati per personalizzare la modalità di elaborazione dell'istruzione nel motore di database. Per altre informazioni, vedere [Hint per la query &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-an-option-clause-with-a-group-by-clause"></a>A. Utilizzo di una clausola OPTION con una clausola GROUP BY  
 Nell'esempio seguente viene illustrato l'utilizzo della clausola `OPTION` con una clausola `GROUP BY`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, OrderQty, SUM(LineTotal) AS Total  
FROM Sales.SalesOrderDetail  
WHERE UnitPrice < $5.00  
GROUP BY ProductID, OrderQty  
ORDER BY ProductID, OrderQty  
OPTION (HASH GROUP, FAST 10);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-select-statement-with-a-label-in-the-option-clause"></a>B. Istruzione SELECT con un'etichetta nella clausola OPTION  
 Nell'esempio seguente viene illustrato un semplice [!INCLUDE[ssDW](../../includes/ssdw-md.md)] istruzione SELECT con un'etichetta nella clausola OPTION.  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactResellerSales  
  OPTION ( LABEL = 'q17' );  
```  
  
### <a name="c-select-statement-with-a-query-hint-in-the-option-clause"></a>C. Istruzione SELECT con un hint per la query nella clausola OPTION  
 Nell'esempio seguente viene illustrata un'istruzione SELECT che utilizza un hint per la query HASH JOIN nella clausola OPTION.  
  
```  
-- Uses AdventureWorks  
  
SELECT COUNT (*) FROM dbo.DimCustomer a  
INNER JOIN dbo.FactInternetSales b   
ON (a.CustomerKey = b.CustomerKey)  
OPTION (HASH JOIN);  
```  
  
### <a name="d-select-statement-with-a-label-and-multiple-query-hints-in-the-option-clause"></a>D. Istruzione SELECT con un'etichetta e più hint per la query nella clausola OPTION  
 L'esempio seguente è un [!INCLUDE[ssDW](../../includes/ssdw-md.md)] istruzione SELECT che contiene un'etichetta e più hint per la query. Quando viene eseguita la query sui nodi di calcolo, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applicherà un hash join o un join di tipo merge, in base alla strategia che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] decide è la soluzione ottimale.  
  
```  
-- Uses AdventureWorks  
  
SELECT COUNT (*) FROM dbo.DimCustomer a  
INNER JOIN dbo.FactInternetSales b   
ON (a.CustomerKey = b.CustomerKey)  
OPTION ( Label = 'CustJoin', HASH JOIN, MERGE JOIN);  
```  
  
### <a name="e-using-a-query-hint-when-querying-a-view"></a>E. Utilizzando un hint di query quando si eseguono query di una vista  
 Nell'esempio seguente crea una visualizzazione denominata CustomerView e quindi viene utilizzato un hint per la query HASH JOIN in una query che fa riferimento a una vista e una tabella.  
  
```  
-- Uses AdventureWorks  
  
CREATE VIEW CustomerView  
AS  
SELECT CustomerKey, FirstName, LastName FROM ssawPDW..DimCustomer;  
  
SELECT COUNT (*) FROM dbo.CustomerView a  
INNER JOIN dbo.FactInternetSales b  
ON (a.CustomerKey = b.CustomerKey)  
OPTION (HASH JOIN);  
  
DROP VIEW CustomerView;  
  
```  
  
### <a name="f-query-with-a-subselect-and-a-query-hint"></a>F. Query con un sub-SELECT e di un hint per la query  
 Nell'esempio seguente viene illustrata una query che contiene una sub-SELECT e un hint per la query. Hint per la query viene applicata a livello globale. Hint per la query non consentiti da aggiungere all'istruzione sub-SELECT.  
  
```  
-- Uses AdventureWorks  
  
CREATE VIEW CustomerView AS  
SELECT CustomerKey, FirstName, LastName FROM ssawPDW..DimCustomer;  
  
SELECT * FROM (  
SELECT COUNT (*) AS a FROM dbo.CustomerView a  
INNER JOIN dbo.FactInternetSales b  
ON ( a.CustomerKey = b.CustomerKey )) AS t  
OPTION (HASH JOIN);  
```  
  
### <a name="g-force-the-join-order-to-match-the-order-in-the-query"></a>G. Forzare l'ordine di join per corrispondere all'ordine della query  
 Nell'esempio seguente viene utilizzato l'hint FORCE ORDER per forzare il piano di query da utilizzare l'ordine di join specificata dalla query. Ciò migliorerà le prestazioni in alcune query. non tutte le query.  
  
```  
-- Uses AdventureWorks  
  
-- Obtain partition numbers, boundary values, boundary value types, and rows per boundary  
-- for the partitions in the ProspectiveBuyer table of the ssawPDW database.  
SELECT sp.partition_number, prv.value AS boundary_value, lower(sty.name) AS boundary_value_type, sp.rows   
FROM sys.tables st JOIN sys.indexes si ON st.object_id = si.object_id AND si.index_id <2  
JOIN sys.partitions sp ON sp.object_id = st.object_id AND sp.index_id = si.index_id  
JOIN sys.partition_schemes ps ON ps.data_space_id = si.data_space_id   
JOIN sys.partition_range_values prv ON prv.function_id = ps.function_id   
JOIN sys.partition_parameters pp ON pp.function_id = ps.function_id   
JOIN sys.types sty ON sty.user_type_id = pp.user_type_id AND prv.boundary_id = sp.partition_number   
WHERE st.object_id = (SELECT object_id FROM sys.objects WHERE name = 'FactResellerSales')   
ORDER BY sp.partition_number  
OPTION ( FORCE ORDER )  
;  
```  
  
### <a name="h-using-externalpushdown"></a>H. Utilizzando externalpushdown non è  
 Nell'esempio seguente forza la distribuzione della clausola WHERE per il processo MapReduce nella tabella esterna Hadoop.  
  
```  
SELECT ID FROM External_Table_AS A   
WHERE ID < 1000000  
OPTION (FORCE EXTERNALPUSHDOWN);  
```  
  
 Nell'esempio seguente impedisce la distribuzione della clausola WHERE per il processo MapReduce nella tabella esterna Hadoop. Vengono restituite tutte le righe a PDW in cui è applicata la clausola WHERE.  
  
```  
SELECT ID FROM External_Table_AS A   
WHERE ID < 10  
OPTION (DISABLE EXTERNALPUSHDOWN);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Hints &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)  
  
  

