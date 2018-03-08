---
title: CREARE la funzione di partizione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE PARTITION FUNCTION
- PARTITION
- PARTITION FUNCTION
- PARTITION_FUNCTION_TSQL
- PARTITION_TSQL
- CREATE_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- RANGE RIGHT partition functions
- RANGE LEFT partition functions
- partitioned indexes [SQL Server], functions
- functions [SQL Server], creating
- partition functions [SQL Server], creating
- partitioned tables [SQL Server], functions
- CREATE PARTITION FUNCTION statement
ms.assetid: 9dfe8b76-721e-42fd-81ae-14e22258c4f2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a095e1de4fdffc97d615a39fd7cf185c99493d02
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="create-partition-function-transact-sql"></a>CREATE PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Crea una funzione nel database corrente che esegue il mapping delle righe di una tabella o di un indice in partizioni in base ai valori della colonna specificata. L'utilizzo di CREATE PARTITION FUNCTION rappresenta il primo passaggio per la creazione di una tabella o di un indice partizionato. In una tabella o indice di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] possono essere presenti al massimo 15.000 partizioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE PARTITION FUNCTION partition_function_name ( input_parameter_type )  
AS RANGE [ LEFT | RIGHT ]   
FOR VALUES ( [ boundary_value [ ,...n ] ] )   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *partition_function_name*  
 Nome della funzione di partizione. I nomi delle funzioni di partizione devono essere univoci all'interno del database e conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 *input_parameter_type*  
 Tipo di dati della colonna usata per il partizionamento. Come colonne di partizionamento possono essere usati tutti i tipi di dati tranne **text**, **ntext**, **image**, **xml**, **timestamp**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, tipi di dati alias o tipi di dati CLR definiti dall'utente.  
  
 La colonna effettiva, ovvero la colonna di partizionamento, è specificata nell'istruzione CREATE TABLE o CREATE INDEX.  
  
 *boundary_value*  
 Specifica i valori limite per ogni partizione di una tabella o indice partizionato che utilizza *partition_function_name*. Se *boundary_value* è vuoto, la funzione di partizione esegue il mapping dell'intera tabella o indice utilizzando *partition_function_name* in un'unica partizione. È possibile usare una sola colonna di partizionamento, specificata in un'istruzione CREATE TABLE o CREATE INDEX.  
  
 *boundary_value* è un'espressione costante che può fare riferimento a variabili. incluse variabili di tipi definiti dall'utente o funzioni e funzioni definite dall'utente. Tale espressione non potrà invece fare riferimento a espressioni [!INCLUDE[tsql](../../includes/tsql-md.md)]. *boundary_value* deve corrispondere o essere convertibile in modo implicito nel tipo di dati fornito in *input_parameter_type*e non può essere troncato durante la conversione implicita in modo che le dimensioni e la scala del valore corrisponde a quello del relativo valore corrispondente *input_parameter_type*.  
  
> [!NOTE]  
>  Se *boundary_value* è costituito da **datetime** o **smalldatetime** valori letterali, questi valori letterali vengono valutati presupponendo che la lingua di sessione sia us_english. Questo comportamento è deprecato. Per garantire che la definizione della funzione di partizione funzioni nel modo previsto per tutte le lingue di sessione, è consigliabile usare costanti interpretate nello stesso modo per le impostazioni di tutte le lingue, ad esempio il formato aaaammgg, oppure convertire esplicitamente i valori letterali in uno stile specifico. Per determinare la lingua di sessione del server, eseguire `SELECT @@LANGUAGE`.  
  
 *... n*  
 Specifica il numero di valori forniti da *boundary_value*massimo è 14,999. Il numero di partizioni create è uguale a  *n*  + 1. Non è necessario elencare i valori in ordine. Se i valori non sono in ordine, [!INCLUDE[ssDE](../../includes/ssde-md.md)] li ordina, crea la funzione e restituisce un avviso che informa che i valori non sono in ordine. Il motore di Database restituisce un errore se  *n*  include valori duplicati.  
  
 **SINISTRA** | OK  
 Specifica il lato di ogni intervallo di valori limite sinistro o destro, il *boundary_value* [ **,***... n* ] appartiene, se i valori di intervallo vengono ordinati in base il [!INCLUDE[ssDE](../../includes/ssde-md.md)]in ordine crescente da sinistra a destra. Se omesso, il valore predefinito è LEFT.  
  
## <a name="remarks"></a>Osservazioni  
 L'ambito di una funzione di partizione è limitato al database in cui la funzione viene creata. All'interno del database le funzioni di partizione si trovano in uno spazio dei nomi separato rispetto alle funzioni.  
  
 Tutte le righe la cui colonna di partizionamento contiene valori NULL vengono inserite nella prima partizione a sinistra, a meno che non sia specificato NULL come valore limite e indicato RIGHT. In questo caso la prima partizione a sinistra sarà una partizione vuota e i valori NULL verranno inseriti nella partizione successiva.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire CREATE PARTITION FUNCTION è possibile usare qualsiasi delle autorizzazioni seguenti:  
  
-   Autorizzazione ALTER ANY DATASPACE. Questa autorizzazione viene concessa per impostazione predefinita al ruolo predefinito del server **sysadmin** e ai ruoli predefiniti del database **db_owner** e **db_ddladmin** .  
  
-   Autorizzazione CONTROL o ALTER per il database in cui viene creata la funzione di partizione.  
  
-   Autorizzazione CONTROL SERVER o ALTER ANY DATABASE per il server del database in cui viene creata la funzione di partizione.  
  
##  <a name="BKMK_examples"></a> Esempi  
  
### <a name="a-creating-a-range-left-partition-function-on-an-int-column"></a>A. Creazione di una funzione di partizione RANGE LEFT in una colonna int  
 La funzione di partizione seguente crea quattro partizioni in una tabella o un indice.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES (1, 100, 1000);  
```  
  
 Nella tabella seguente viene illustrato come una tabella che utilizza questa funzione di partizione nella colonna di partizionamento **col1** sarebbe partizionata.  
  
|Partition|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Valori**|**Col1** <= `1`|**col1**  >  `1` AND **col1** <= `100`|**col1**  >  `100` AND **col1** <=`1000`|**Col1** > `1000`|  
  
### <a name="b-creating-a-range-right-partition-function-on-an-int-column"></a>B. Creazione di una funzione di partizione RANGE RIGHT in una colonna int  
 La funzione di partizione seguente usa gli stessi valori per *boundary_value* [ **,***... n* ] dell'esempio precedente, ma viene specificato RANGE RIGHT.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF2 (int)  
AS RANGE RIGHT FOR VALUES (1, 100, 1000);  
```  
  
 Nella tabella seguente viene illustrato come una tabella che utilizza questa funzione di partizione nella colonna di partizionamento **col1** sarebbe partizionata.  
  
|Partition|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Valori**|**col1** \<`1`|**col1**  >=  `1` AND **col1** \<`100`|**col1**  >=  `100` AND **col1** \<`1000`|**Col1** >= `1000`| 
  
### <a name="c-creating-a-range-right-partition-function-on-a-datetime-column"></a>C. Creazione di una funzione di partizione RANGE RIGHT in una colonna datetime  
 La funzione di partizione seguente suddivide una tabella o un indice in 12 partizioni, una per ogni mese del valore dell'anno di valori in un **datetime** colonna.  
  
```sql  
CREATE PARTITION FUNCTION [myDateRangePF1] (datetime)  
AS RANGE RIGHT FOR VALUES ('20030201', '20030301', '20030401',  
               '20030501', '20030601', '20030701', '20030801',   
               '20030901', '20031001', '20031101', '20031201');  
```  
  
 Nella tabella seguente viene illustrato come una tabella o indice che usa questa funzione di partizione nella colonna di partizionamento **datecol** sarebbe partizionata.  
  
|Partition|1|2|...|11|12|  
|---------------|-------|-------|---------|--------|--------|  
|**Valori**|**datecol** \<`February 1, 2003`|**datecol**  >=  `February 1, 2003` AND **datecol** \<`March 1, 2003`||**datecol**  >=  `November 1, 2003` AND **col1** \<`December 1, 2003`|**datecol** >= `December 1, 2003`| 
  
### <a name="d-creating-a-partition-function-on-a-char-column"></a>D. Creazione di una funzione di partizione in una colonna char  
 La funzione di partizione seguente crea quattro partizioni in una tabella o un indice.  
  
```sql  
CREATE PARTITION FUNCTION myRangePF3 (char(20))  
AS RANGE RIGHT FOR VALUES ('EX', 'RXE', 'XR');  
```  
  
 Nella tabella seguente viene illustrato come una tabella che utilizza questa funzione di partizione nella colonna di partizionamento **col1** sarebbe partizionata.  
  
|Partition|1|2|3|4|  
|---------------|-------|-------|-------|-------|  
|**Valori**|**col1** \< `EX`...|**col1**  >=  `EX` AND **col1** \< `RXE`...|**col1**  >=  `RXE` AND **col1** \< `XR`...|**Col1** >= `XR`| 
  
### <a name="e-creating-15000-partitions"></a>E. Creazione di 15.000  
 La funzione di partizione seguente crea 15.000 partizioni in una tabella o un indice.  
  
```sql  
--Create integer partition function for 15,000 partitions.  
DECLARE @IntegerPartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION IntegerPartitionFunction (int) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i int = 1;  
WHILE @i < 14999  
BEGIN  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N', ';  
SET @i += 1;  
END  
SET @IntegerPartitionFunction += CAST(@i as nvarchar(10)) + N');';  
EXEC sp_executesql @IntegerPartitionFunction;  
GO  
```  
  
### <a name="f-creating-partitions-for-multiple-years"></a>F. Creazione di partizioni per più anni  
 La funzione di partizione seguente partizioni di una tabella o un indice in 50 partizioni in un **datetime2** colonna. È presente una partizione per ogni mese tra gennaio 2007 e gennaio 2011.  
  
```sql  
--Create date partition function with increment by month.  
DECLARE @DatePartitionFunction nvarchar(max) = 
    N'CREATE PARTITION FUNCTION DatePartitionFunction (datetime2) 
    AS RANGE RIGHT FOR VALUES (';  
DECLARE @i datetime2 = '20070101';  
WHILE @i < '20110101'  
BEGIN  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10)) + '''' + N', ';  
SET @i = DATEADD(MM, 1, @i);  
END  
SET @DatePartitionFunction += '''' + CAST(@i as nvarchar(10))+ '''' + N');';  
EXEC sp_executesql @DatePartitionFunction;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e indici partizionati](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [$PARTITION &#40; Transact-SQL &#41;](../../t-sql/functions/partition-transact-sql.md)   
 [ALTER PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [Sys. partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [Sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [Sys. Partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  

