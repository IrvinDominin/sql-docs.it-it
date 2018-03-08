---
title: RANGO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 10/25/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RANK
- RANK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row ranking [SQL Server]
- tied rows [SQL Server]
- ranking rows
- RANK function [Transact-SQL]
ms.assetid: 2d96f6d2-5db7-4b3c-a63e-213c58e4af55
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 657f152f295fd93d3749ed6ff4865cd753dc3e95
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="rank-transact-sql"></a>RANK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il rango di ogni riga all'interno della partizione di un set di risultati. Il valore di rango di una riga è uno più il numero di ranghi che precedono la riga in questione.  

  ROW_NUMBER e numero di dimensioni sono simili. Numeri ROW_NUMBER tutte le righe in sequenza (ad esempio 1, 2, 3, 4, 5). Numero di dimensioni fornisce lo stesso valore numerico per ties (ad esempio 1, 2, 2, 4, 5).   
  
> [!NOTE]
> CLASSIFICAZIONE è che un tipo di valore calcolato quando viene eseguita la query. Per rendere persistenti i numeri in una tabella, vedere [proprietà IDENTITY](../../t-sql/statements/create-table-transact-sql-identity-property.md) e [sequenza](../../t-sql/statements/create-sequence-transact-sql.md). 
   
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
RANK ( ) OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>Argomenti  
 SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine dei dati prima che venga applicata la funzione. Il *order_by_clause* è obbligatorio. Il \<righe o clausola range > della OVER clausola non può essere specificata per la funzione RANK. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>Tipi restituiti  
 **bigint**  
  
## <a name="remarks"></a>Osservazioni  
 Se due o più righe hanno un valore equivalente per un rango, ogni riga equivalente riceve lo stesso rango. Ad esempio, se due venditori principali hanno lo stesso valore SalesYTD, viene assegnato a entrambi il rango uno. Al venditore con il valore SalesYTD più alto successivo viene assegnato il rango tre, poiché sono presenti due righe di rango più elevato. Pertanto, la funzione RANK non restituirà sempre valori interi consecutivi.  
  
 L'ordinamento utilizzato per l'intera query determina l'ordinamento in base al quale vengono visualizzate le righe in un set di risultati,  
  
 RANK è non deterministico. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-ranking-rows-within-a-partition"></a>A. Classificazione di righe all'interno di una partizione  
 Nell'esempio seguente vengono assegnati i ranghi per i prodotti nelle ubicazioni di inventario specificate in base alle quantità. Il set di risultati viene partizionato da `LocationID` e ordinato logicamente in base al valore di `Quantity`. Si noti che la quantità dei prodotti 494 e 495 è la stessa. Poiché tali prodotti sono collegati, vengono entrambi classificati con uno.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.ProductID, p.Name, i.LocationID, i.Quantity  
    ,RANK() OVER   
    (PARTITION BY i.LocationID ORDER BY i.Quantity DESC) AS Rank  
FROM Production.ProductInventory AS i   
INNER JOIN Production.Product AS p   
    ON i.ProductID = p.ProductID  
WHERE i.LocationID BETWEEN 3 AND 4  
ORDER BY i.LocationID;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
ProductID   Name                   LocationID   Quantity Rank  
----------- ---------------------- ------------ -------- ----  
494         Paint - Silver         3            49       1  
495         Paint - Blue           3            49       1  
493         Paint - Red            3            41       3  
496         Paint - Yellow         3            30       4  
492         Paint - Black          3            17       5  
495         Paint - Blue           4            35       1  
496         Paint - Yellow         4            25       2  
493         Paint - Red            4            24       3  
492         Paint - Black          4            14       4  
494         Paint - Silver         4            12       5  
 (10 row(s) affected)  
```  
  
### <a name="b-ranking-all-rows-in-a-result-set"></a>B. Classificazione di tutte le righe in un set di risultati  
 Nell'esempio seguente vengono restituiti i primi dieci dipendenti classificati in base allo stipendio. Poiché non è specificata alcuna clausola PARTITION BY, la funzione RANK è stata applicata a tutte le righe nel set di risultati.  
  
```  
USE AdventureWorks2012  
SELECT TOP(10) BusinessEntityID, Rate,   
       RANK() OVER (ORDER BY Rate DESC) AS RankBySalary  
FROM HumanResources.EmployeePayHistory AS eph1  
WHERE RateChangeDate = (SELECT MAX(RateChangeDate)   
                        FROM HumanResources.EmployeePayHistory AS eph2  
                        WHERE eph1.BusinessEntityID = eph2.BusinessEntityID)  
ORDER BY BusinessEntityID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
BusinessEntityID Rate                  RankBySalary  
---------------- --------------------- --------------------  
1                125.50                1  
2                63.4615               4  
3                43.2692               8  
4                29.8462               19  
5                32.6923               16  
6                32.6923               16  
7                50.4808               6  
8                40.8654               10  
9                40.8654               10  
10               42.4808               9  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-ranking-rows-within-a-partition"></a>C: classificazione di righe all'interno di una partizione  
 Nell'esempio seguente classifica i venditori in ogni territorio di vendita in base alla loro vendite totali. Il set di righe viene partizionato in base a `SalesTerritoryGroup` e ordinato in base a `SalesAmountQuota`.  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
LastName          TotalSales     SalesTerritoryGroup  RankResult
----------------  -------------  -------------------  --------
Tsoflias          1687000.0000   Australia            1
Saraiva           7098000.0000   Canada               1
Vargas            4365000.0000   Canada               2
Carson            12198000.0000  Central              1
Varkey Chudukatil 5557000.0000   France               1
Valdez            2287000.0000   Germany              1
Blythe            11162000.0000  Northeast            1
Campbell          4025000.0000   Northwest            1
Ansman-Wolfe      3551000.0000   Northwest            2
Mensa-Annan       2753000.0000   Northwest            3
Reiter            8541000.0000   Southeast            1
Mitchell          11786000.0000  Southwest            1
Ito               7804000.0000   Southwest            2
Pak               10514000.0000  United Kingdom       1
```  
  
## <a name="see-also"></a>Vedere anche  
 [DENSE_RANK &#40; Transact-SQL &#41;](../../t-sql/functions/dense-rank-transact-sql.md)   
 [ROW_NUMBER &#40; Transact-SQL &#41;](../../t-sql/functions/row-number-transact-sql.md)   
 [NTILE &#40; Transact-SQL &#41;](../../t-sql/functions/ntile-transact-sql.md)   
 [Rango funzioni &#40; Transact-SQL &#41;](../../t-sql/functions/ranking-functions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  



