---
title: COALESCE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COALESCE
- COALESCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], nonnull
- COALESCE function
- first nonnull expressions [SQL Server]
- nonnull expressions
ms.assetid: fafc0dba-f8a8-4aad-9b7f-908e34b74d88
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 63c65bb6348afa4d095971b5833f26e8e33dd5a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666767"
---
# <a name="coalesce-transact-sql"></a>COALESCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Valuta gli argomenti seguendo l'ordine e restituisce il valore corrente della prima espressione che inizialmente non restituisce `NULL`. Ad esempio, `SELECT COALESCE(NULL, NULL, 'third_value', 'fourth_value');` restituisce il terzo valore perché il terzo valore è il primo valore non Null. 
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
COALESCE ( expression [ ,...n ] )   
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il tipo di dati dell'*espressione* con la precedenza del tipo di dati più alta. Se tutte le espressioni non ammettono valori Null, il risultato non ammetterà valori Null.  
  
## <a name="remarks"></a>Remarks  
 Quando tutti gli argomenti sono `NULL`, `COALESCE`restituisce `NULL`. Almeno uno dei valori Null deve essere un valore `NULL` tipizzato.  
  
## <a name="comparing-coalesce-and-case"></a>Confronto tra COALESCE e CASE  
 L'espressione `COALESCE` è una scorciatoia sintattica dell'espressione `CASE`.  Il codice `COALESCE`(*expression1*,*...n*) viene quindi riscritto da Query Optimizer come la seguente espressione `CASE`:  
  
 ```sql  
 CASE  
 WHEN (expression1 IS NOT NULL) THEN expression1  
 WHEN (expression2 IS NOT NULL) THEN expression2  
 ...  
 ELSE expressionN  
 END  
 ```  
  
 ciò significa che i valori di input (*expression1*, *expression2*, *expressionN*e così via) vengono valutati più volte. Inoltre, in conformità con lo standard SQL, un'espressione di valori che contiene una sottoquery è considerata non deterministica e la sottoquery viene valutata due volte. In entrambi i casi, è possibile che tra la prima valutazione e quelle successive i risultati siano diversi.  
  
 Ad esempio, quando viene eseguito il codice `COALESCE((subquery), 1)`, la sottoquery viene valutata due volte. Di conseguenza, è possibile che si ottengano risultati differenti a seconda del livello di isolamento della query. Ad esempio, il codice può restituire `NULL` con il livello di isolamento `READ COMMITTED` in un ambiente multiutente. Per assicurare risultati costanti, utilizzare il livello di isolamento `SNAPSHOT ISOLATION` oppure sostituire `COALESCE` con la funzione `ISNULL`. In alternativa, è possibile riscrivere la query per eseguire il push della sottoquery in una selezione secondaria, come illustrato nell'esempio seguente:  
  
```sql  
SELECT CASE WHEN x IS NOT NULL THEN x ELSE 1 END  
from  
(  
SELECT (SELECT Nullable FROM Demo WHERE SomeCol = 1) AS x  
) AS T;  
  
```  
  
## <a name="comparing-coalesce-and-isnull"></a>Confronto tra COALESCE e ISNULL  
 Le finalità della funzione `ISNULL` e dell'espressione `COALESCE` sono simili, ma i comportamenti differiscono.  
  
1.  Poiché `ISNULL` è una funzione, viene valutata una sola volta.  Come descritto in precedenza, i valori di input per l'espressione `COALESCE` possono essere valutati più volte.  
  
2.  La determinazione dei tipi di dati dell'espressione risultante è differente. `ISNULL` utilizza il tipo di dati del primo parametro, `COALESCE` segue le regole dell'espressione `CASE` e restituisce il tipo di dati del valore con la precedenza più alta.  
  
3.  Il supporto dei valori NULL dell'espressione risultante è differente per `ISNULL` e `COALESCE`. Il valore restituito da `ISNULL` non ammette mai i valori NULL (supponendo che il valore restituito sia un valore che non ammette valori NULL), mentre `COALESCE` con parametri non NULL è considerata `NULL`. Le espressioni `ISNULL(NULL, 1)` e `COALESCE(NULL, 1)`, quindi, sebbene equivalenti, hanno valori di supporto dei valori NULL differenti. Questa differenza è importante quando si utilizzano queste espressioni nelle colonne calcolate, creando vincoli di chiave o rendendo deterministico il valore restituito di una funzione scalare definita dall'utente in modo che possa essere indicizzato come mostrato nell'esempio che segue:  
  
    ```sql  
    USE tempdb;  
    GO  
    -- This statement fails because the PRIMARY KEY cannot accept NULL values  
    -- and the nullability of the COALESCE expression for col2   
    -- evaluates to NULL.  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0) PRIMARY KEY,   
    col3 AS ISNULL(col1, 0)   
    );   
  
    -- This statement succeeds because the nullability of the   
    -- ISNULL function evaluates AS NOT NULL.  
  
    CREATE TABLE #Demo   
    (   
    col1 integer NULL,   
    col2 AS COALESCE(col1, 0),   
    col3 AS ISNULL(col1, 0) PRIMARY KEY   
    );  
    ```  
  
4.  Anche le convalide per `ISNULL` e `COALESCE` sono diverse. Ad esempio, un valore `NULL` per `ISNULL` viene convertito in **int**, mentre per `COALESCE` è necessario fornire un tipo di dati.  
  
5.  `ISNULL` accetta solo due parametri, mentre `COALESCE` accetta un numero variabile di parametri.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-running-a-simple-example"></a>A. Esecuzione di un esempio semplice  
 Nell'esempio seguente viene illustrato il modo in cui `COALESCE` seleziona i dati dalla prima colonna in cui è presente un valore non Null. In questo esempio viene utilizzato il database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT Name, Class, Color, ProductNumber,  
COALESCE(Class, Color, ProductNumber) AS FirstNotNull  
FROM Production.Product;  
```  
  
### <a name="b-running-a-complex-example"></a>B. Esecuzione di un esempio complesso  
 Nell'esempio seguente viene illustrata una tabella `wages` che include tre colonne con informazioni sulla retribuzione annua dei dipendenti, ovvero retribuzione oraria, stipendio e commissione. Un dipendente tuttavia riceve un solo tipo di paga. Per determinare l'importo totale pagato a tutti i dipendenti, utilizzare la funzione `COALESCE` per ottenere solo i valori non Null delle colonne `hourly_wage`, `salary` e `commission`.  
  
```sql  
SET NOCOUNT ON;  
GO  
USE tempdb;  
IF OBJECT_ID('dbo.wages') IS NOT NULL  
    DROP TABLE wages;  
GO  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   identity,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
GO  
INSERT dbo.wages (hourly_wage, salary, commission, num_sales)  
VALUES  
    (10.00, NULL, NULL, NULL),  
    (20.00, NULL, NULL, NULL),  
    (30.00, NULL, NULL, NULL),  
    (40.00, NULL, NULL, NULL),  
    (NULL, 10000.00, NULL, NULL),  
    (NULL, 20000.00, NULL, NULL),  
    (NULL, 30000.00, NULL, NULL),  
    (NULL, 40000.00, NULL, NULL),  
    (NULL, NULL, 15000, 3),  
    (NULL, NULL, 25000, 2),  
    (NULL, NULL, 20000, 6),  
    (NULL, NULL, 14000, 4);  
GO  
SET NOCOUNT OFF;  
GO  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS money) AS 'Total Salary'   
FROM dbo.wages  
ORDER BY 'Total Salary';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00  
  
 (12 row(s) affected)
 ```  
  
### <a name="c-simple-example"></a>C: esempio semplice  
 Nell'esempio seguente viene illustrato come `COALESCE` seleziona i dati dalla prima colonna in cui è presente un valore non Null. Si supponga per questo esempio che la tabella `Products` contenga i dati seguenti:  
  
 ```  
 Name         Color      ProductNumber  
 ------------ ---------- -------------  
 Socks, Mens  NULL       PN1278  
 Socks, Mens  Blue       PN1965  
 NULL         White      PN9876
 ```  
  
 è quindi possibile eseguire la seguente query COALESCE:  
  
```sql  
SELECT Name, Color, ProductNumber, COALESCE(Color, ProductNumber) AS FirstNotNull   
FROM Products ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Name         Color      ProductNumber  FirstNotNull  
 ------------ ---------- -------------  ------------  
 Socks, Mens  NULL       PN1278         PN1278  
 Socks, Mens  Blue       PN1965         Blue  
 NULL         White      PN9876         White
 ```  
  
 Si noti che nella prima riga, il valore `FirstNotNull` è `PN1278`, non `Socks, Mens`. Ciò è dovuto al fatto che la colonna `Name`non è stata specificata come parametro per `COALESCE` nell'esempio.  
  
### <a name="d-complex-example"></a>D: esempio complesso  
 L'esempio seguente usa `COALESCE` per confrontare i valori in tre colonne e restituire solo il valore non Null trovato nelle colonne.  
  
```sql  
CREATE TABLE dbo.wages  
(  
    emp_id        tinyint   NULL,  
    hourly_wage   decimal   NULL,  
    salary        decimal   NULL,  
    commission    decimal   NULL,  
    num_sales     tinyint   NULL  
);  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (1, 10.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (2, 20.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (3, 30.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (4, 40.00, NULL, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (5, NULL, 10000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (6, NULL, 20000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (7, NULL, 30000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (8, NULL, 40000.00, NULL, NULL);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (9, NULL, NULL, 15000, 3);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (10,NULL, NULL, 25000, 2);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (11, NULL, NULL, 20000, 6);  
  
INSERT INTO dbo.wages (emp_id, hourly_wage, salary, commission, num_sales)  
VALUES (12, NULL, NULL, 14000, 4);  
  
SELECT CAST(COALESCE(hourly_wage * 40 * 52,   
   salary,   
   commission * num_sales) AS decimal(10,2)) AS TotalSalary   
FROM dbo.wages  
ORDER BY TotalSalary;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Total Salary  
 ------------  
 10000.00  
 20000.00  
 20800.00  
 30000.00  
 40000.00  
 41600.00  
 45000.00  
 50000.00  
 56000.00  
 62400.00  
 83200.00  
 120000.00
 ```  
  
## <a name="see-also"></a>Vedere anche  
 [ISNULL &#40;Transact-SQL&#41;](../../t-sql/functions/isnull-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)  
  
  
