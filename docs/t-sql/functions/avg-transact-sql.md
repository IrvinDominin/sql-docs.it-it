---
title: AVG (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
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
- AVG_TSQL
- AVG
dev_langs:
- TSQL
helpviewer_keywords:
- AVG function [Transact-SQL]
- GROUP BY clause, AVG function
- DISTINCT keyword
- values [SQL Server], average
- average values
ms.assetid: 4534b705-d946-441b-9b5d-5fbe561c9131
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 40240e2c06055d61eb047c319349f4869b9979df
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="avg-transact-sql"></a>AVG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce la media dei valori di un gruppo. I valori Null vengono ignorati.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
AVG ( [ ALL | DISTINCT ] expression )  
   OVER ( [ partition_by_clause ] order_by_clause )    
```  
  
## <a name="arguments"></a>Argomenti  
ALL  
Applica la funzione di aggregazione a tutti i valori. Il valore predefinito è ALL.
  
DISTINCT  
Indica che la funzione AVG deve essere eseguita solo in ogni istanza univoca di un valore, indipendentemente dal numero di occorrenze del valore.
  
*espressione*  
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di uno, categoria del tipo di dati numerici o numerici approssimativi, ad eccezione del **bit** tipo di dati. Non è possibile utilizzare funzioni di aggregazione e sottoquery.
  
SU **(** [ *partition_by_clause* ] *order_by_clause***)**  
*partition_by_clause* suddivide il set di risultati generato dalla clausola FROM in partizioni a cui viene applicata la funzione. Se non specificato, la funzione tratta tutte le righe del set di risultati della query come un unico gruppo. *order_by_clause* determina l'ordine logico in cui viene eseguita l'operazione. *order_by_clause* è obbligatorio. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).
  
## <a name="return-types"></a>Tipi restituiti
Il tipo restituito è determinato dal tipo di risultato valutato del *espressione*.
  
|Risultato dell'espressione|Tipo restituito|  
|---|---|
|**tinyint**|**int**|  
|**smallint**|**int**|  
|**int**|**int**|  
|**bigint**|**bigint**|  
|**decimale** categoria (p, s)|**Decimal (38, s)** diviso **decimale (10, 0)**|  
|**Money** e **smallmoney** categoria|**money**|  
|**float** e **reale** categoria|**float**|  
  
## <a name="remarks"></a>Osservazioni  
Se il tipo di dati *espressione* un alias di dati, il tipo restituito è anche di tipo del tipo di dati alias. Tuttavia, se il tipo di dati di base di tipo di dati alias viene promosso, ad esempio da **tinyint** a **int**, il valore restituito è di dati promosso tipo e non il tipo di dati alias.
  
AVG () calcola la media di un set di valori dividendo la somma di tali valori per il numero di valori non Null. Se la somma supera il valore massimo per il tipo di dati del valore restituito, verrà restituito un errore.
  
AVG è una funzione deterministica quando viene utilizzata senza le clausole ORDER BY e OVER. Non è deterministica quando viene specificata con le clausole ORDER BY e OVER. Per altre informazioni, vedere [Funzioni deterministiche e non deterministiche](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-the-sum-and-avg-functions-for-calculations"></a>A. Utilizzo delle funzioni SUM e AVG per l'esecuzione di calcoli  
Nell'esempio seguente viene calcolata la media delle ore di ferie e la somma delle ore di malattia utilizzate dai vicepresidenti di [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]. Ogni funzione di aggregazione restituisce un singolo valore di riepilogo per tutte le righe recuperate. Nell'esempio viene utilizzato il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].
  
```sql
SELECT AVG(VacationHours)AS 'Average vacation hours',   
    SUM(SickLeaveHours) AS 'Total sick leave hours'  
FROM HumanResources.Employee  
WHERE JobTitle LIKE 'Vice President%';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Average vacation hours       Total sick leave hours
 ----------------------       ----------------------
25                           97
  
(1 row(s) affected)
```
  
### <a name="b-using-the-sum-and-avg-functions-with-a-group-by-clause"></a>B. Utilizzo delle funzioni SUM e AVG con una clausola GROUP BY  
Ogni funzione di aggregazione, se utilizzata con la clausola `GROUP BY`, restituisce un singolo valore per ogni gruppo anziché per l'intera tabella. Nell'esempio seguente vengono prodotti valori di riepilogo per ciascun territorio di vendita nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Nel riepilogo viene elencata la media dei premi di produttività ricevuti dai venditori in ogni area e la somma delle vendite da inizio anno per ogni area.
  
```sql
SELECT TerritoryID, AVG(Bonus)as 'Average bonus', SUM(SalesYTD) as 'YTD sales'  
FROM Sales.SalesPerson  
GROUP BY TerritoryID;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
TerritoryID Average Bonus         YTD Sales  
----------- --------------------- ---------------------  
NULL        0.00                  1252127.9471  
1           4133.3333             4502152.2674  
2           4100.00               3763178.1787  
3           2500.00               3189418.3662  
4           2775.00               6709904.1666  
5           6700.00               2315185.611  
6           2750.00               4058260.1825  
7           985.00                3121616.3202  
8           75.00                 1827066.7118  
9           5650.00               1421810.9242  
10          5150.00               4116871.2277  
  
(11 row(s) affected)  
```  
  
### <a name="c-using-avg-with-distinct"></a>C. Utilizzo di AVG con DISTINCT  
Nell'istruzione seguente viene restituito il prezzo medio di listino dei prodotti nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Se si specifica DISTINCT, nel calcolo vengono considerati solo i valori univoci.
  
```sql
SELECT AVG(DISTINCT ListPrice)  
FROM Production.Product;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------------
437.4042
  
(1 row(s) affected)
```
  
### <a name="d-using-avg-without-distinct"></a>D. Utilizzo della funzione AVG senza DISTINCT  
Senza DISTINCT, la funzione `AVG` trova il prezzo medio di listino di tutti i prodotti nella tabella `Product` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)], inclusi i valori duplicati.
  
```sql
SELECT AVG(ListPrice)  
FROM Production.Product;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------------
438.6662
  
(1 row(s) affected)
```
  
### <a name="e-using-the-over-clause"></a>E. Utilizzo della clausola OVER  
Nell'esempio seguente viene utilizzata la funzione AVG con la clausola OVER per fornire una media mobile delle vendite annuali per ogni area presente nella tabella `Sales.SalesPerson` del database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. I dati vengono partizionati in base a `TerritoryID` e ordinati logicamente in base a `SalesYTD`. La funzione AVG viene pertanto calcolata per ogni area in base all'anno di vendita. Si noti che per `TerritoryID` 1, sono presenti due righe per l'anno di vendita 2005, a indicare due venditori con vendite in tale anno. Viene calcolata la media delle vendite delle due righe e nel calcolo viene quindi inclusa la terza riga che rappresenta le vendite per l'anno 2006.
  
```sql
SELECT BusinessEntityID, TerritoryID   
   ,DATEPART(yy,ModifiedDate) AS SalesYear  
   ,CONVERT(varchar(20),SalesYTD,1) AS  SalesYTD  
   ,CONVERT(varchar(20),AVG(SalesYTD) OVER (PARTITION BY TerritoryID   
                                            ORDER BY DATEPART(yy,ModifiedDate)   
                                           ),1) AS MovingAvg  
   ,CONVERT(varchar(20),SUM(SalesYTD) OVER (PARTITION BY TerritoryID   
                                            ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS CumulativeTotal  
FROM Sales.SalesPerson  
WHERE TerritoryID IS NULL OR TerritoryID < 5  
ORDER BY TerritoryID,SalesYear;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID TerritoryID SalesYear   SalesYTD             MovingAvg            CumulativeTotal  
---------------- ----------- ----------- -------------------- -------------------- --------------------  
274              NULL        2005        559,697.56           559,697.56           559,697.56  
287              NULL        2006        519,905.93           539,801.75           1,079,603.50  
285              NULL        2007        172,524.45           417,375.98           1,252,127.95  
283              1           2005        1,573,012.94         1,462,795.04         2,925,590.07  
280              1           2005        1,352,577.13         1,462,795.04         2,925,590.07  
284              1           2006        1,576,562.20         1,500,717.42         4,502,152.27  
275              2           2005        3,763,178.18         3,763,178.18         3,763,178.18  
277              3           2005        3,189,418.37         3,189,418.37         3,189,418.37  
276              4           2005        4,251,368.55         3,354,952.08         6,709,904.17  
281              4           2005        2,458,535.62         3,354,952.08         6,709,904.17  
  
(10 row(s) affected)  
  
```  
  
In questo esempio la clausola OVER non include PARTITION BY. La funzione verrà pertanto applicata a tutte le righe restituite dalla query. La clausola ORDER BY specificata nella clausola OVER determina l'ordine logico in base al quale viene applicata la funzione AVG. La query restituisce una media mobile delle vendite annuali per tutte le aree di vendita specificate nella clausola WHERE. La clausola ORDER BY specificata nell'istruzione SELECT determina l'ordine in cui vengono visualizzate le righe della query.
  
```sql
SELECT BusinessEntityID, TerritoryID   
   ,DATEPART(yy,ModifiedDate) AS SalesYear  
   ,CONVERT(varchar(20),SalesYTD,1) AS  SalesYTD  
   ,CONVERT(varchar(20),AVG(SalesYTD) OVER (ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS MovingAvg  
   ,CONVERT(varchar(20),SUM(SalesYTD) OVER (ORDER BY DATEPART(yy,ModifiedDate)   
                                            ),1) AS CumulativeTotal  
FROM Sales.SalesPerson  
WHERE TerritoryID IS NULL OR TerritoryID < 5  
ORDER BY SalesYear;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
BusinessEntityID TerritoryID SalesYear   SalesYTD             MovingAvg            CumulativeTotal  
---------------- ----------- ----------- -------------------- -------------------- --------------------  
274              NULL        2005        559,697.56           2,449,684.05         17,147,788.35  
275              2           2005        3,763,178.18         2,449,684.05         17,147,788.35  
276              4           2005        4,251,368.55         2,449,684.05         17,147,788.35  
277              3           2005        3,189,418.37         2,449,684.05         17,147,788.35  
280              1           2005        1,352,577.13         2,449,684.05         17,147,788.35  
281              4           2005        2,458,535.62         2,449,684.05         17,147,788.35  
283              1           2005        1,573,012.94         2,449,684.05         17,147,788.35  
284              1           2006        1,576,562.20         2,138,250.72         19,244,256.47  
287              NULL        2006        519,905.93           2,138,250.72         19,244,256.47  
285              NULL        2007        172,524.45           1,941,678.09         19,416,780.93  
(10 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche
[Funzioni di aggregazione &#40; Transact-SQL &#41;](../../t-sql/functions/aggregate-functions-transact-sql.md)  
[IN una clausola &#40; Transact-SQL &#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
  
