---
title: datetime2 (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- datetime2
- datetime2_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- dates [SQL Server], data types
- date and time [SQL Server], datetime2
- data types [SQL Server], date and time
- datetime2 data type [SQL Server]
ms.assetid: 868017f3-214f-43ef-8536-cc1632a2288f
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 70a3f27fc59fcc904679040029e47f312017dbe3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="datetime2-transact-sql"></a>datetime2 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Definisce una data costituita dalla combinazione di un'ora del giorno espressa nel formato 24 ore. **datetime2** può essere considerato come un'estensione dell'oggetto esistente **datetime** tipo che dispone di un intervallo di date più grande, una maggiore precisione frazionaria predefinita e una precisione specificata dall'utente facoltativa.
  
## <a name="datetime2-description"></a>descrizione di datetime2
  
|Proprietà|Valore|  
|--------------|-----------|  
|Sintassi|**datetime2** [(*precisione frazionaria dei secondi*)]|  
|Utilizzo|DICHIARARE @MyDatetime2 **datetime2 (7)**<br /><br /> CREARE una tabella Table1 (Column1 **datetime2 (7)** )|  
|Formato predefinito dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|AAAA-MM-GG hh:mm:ss[.secondi frazionari]<br /><br /> Per ulteriori informazioni, vedere la sezione seguente relativa alla compatibilità con le versioni precedenti per i client legacy.|  
|Intervallo di date|Da 01-01-0001 a 31-12-9999<br /><br /> Gennaio 1,1 CE e il 31 dicembre 9999 CE|  
|Intervallo di ore|da 00:00:00 a 23:59:59.9999999|  
|Intervallo di differenze di fuso orario|Nessuno|  
|Intervalli di elementi|AAAA rappresenta un numero di quattro cifre compreso tra 0001 e 9999, indicante l'anno.<br /><br /> MM rappresenta un numero di due cifre compreso tra 01 e 12, indicante un mese dell'anno specificato.<br /><br /> GG rappresenta un numero di due cifre compreso tra 01 e 31, a seconda del mese, indicante il giorno del mese specificato.<br /><br /> hh rappresenta un numero di due cifre compreso tra 00 e 23, indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre compreso tra 00 e 59, indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre compreso tra 00 e 59, indicante i secondi.<br /><br /> n* rappresenta un numero composto da 0 a 7 cifre e compreso tra 0 e 9999999, indicante i secondi frazionari. In Informatica, i secondi frazionari verranno troncati quando n > 3.|  
|Lunghezza in caratteri|Da un minimo di 19 posizioni (AAAA-MM-GG hh:mm:ss ) a un massimo di 27 posizioni (AAAA-MM-GG hh:mm:ss.0000000)|  
|Precisione, scala|Da 0 a 7 cifre, con un'accuratezza di 100 nanosecondi. La precisione predefinita è 7 cifre.|  
|Dimensioni dello spazio di archiviazione|6 byte per le precisioni minori di 3; 7 byte per le precisioni 3 e 4. Tutte le altre precisioni richiedono 8 byte.|  
|Accuratezza|100 nanosecondi|  
|Valore predefinito|1900-01-01 00:00:00|  
|Calendario|Gregoriano|  
|Precisione in secondi frazionari definita dall'utente|Sì|  
|Considerazione e conservazione delle differenze di fuso orario|No|  
|Considerazione dell'ora legale|No|  
  
Per i metadati di tipo di dati, vedere [systypes &#40; Transact-SQL &#41; ](../../relational-databases/system-compatibility-views/sys-systypes-transact-sql.md) o [TYPEPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/typeproperty-transact-sql.md). Precisione e scala sono variabili per alcuni tipi di dati di data e ora. Per ottenere la precisione e scala di una colonna, vedere [COLUMNPROPERTY &#40; Transact-SQL &#41; ](../../t-sql/functions/columnproperty-transact-sql.md), [COL_LENGTH &#40; Transact-SQL &#41; ](../../t-sql/functions/col-length-transact-sql.md), o [Columns &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md).
  
## <a name="supported-string-literal-formats-for-datetime2"></a>Formati di letterale stringa supportati per datetime2
Le tabelle seguenti elencano i ISO 8601 e ODBC stringa letterale formati supportati per **datetime2**. Per informazioni sui formati alfabetico, numerici, senza separatori e tempi per le parti di data e ora di **datetime2**, vedere [data &#40; Transact-SQL &#41; ](../../t-sql/data-types/date-transact-sql.md) e [ora &#40; Transact-SQL &#41; ](../../t-sql/data-types/time-transact-sql.md).
  
|ISO 8601|Descrizioni|  
|---|---|
|YYYY-MM-DDThh:mm:ss[.nnnnnnn]<br /><br /> YYYY-MM-DDThh:mm:ss[.nnnnnnn]|Su questo formato non influiscono le impostazioni locali delle sessioni SET LANGUAGE e SET DATEFORMAT. Il **T**, due punti (:) e il punto (.) sono inclusi nella stringa di valore letterale, ad esempio ' 2007-05-02T19:58:47.1234567'.|  
  
|ODBC|Description|  
|---|---|
|{ ts 'aaaa-mm-gg hh:mm:ss[.secondi frazionari]' }|Specifico delle API ODBC:<br /><br /> Il numero di cifre a destra del separatore decimale che rappresenta i secondi frazionari comprende da 0 a 7 cifre (100 nanosecondi).|  
  
## <a name="ansi-and-iso-8601-compliance"></a>Conformità ANSI e ISO 8601  
La conformità agli standard ANSI e ISO 8601 di [data](../../t-sql/data-types/date-transact-sql.md) e [ora](../../t-sql/data-types/time-transact-sql.md) si applicano a **datetime2**.
  
##  <a name="backward-compatibility-for-down-level-clients"></a>Compatibilità con le versioni precedenti dei client legacy  
Alcuni client legacy non supportano il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati. Nella tabella seguente viene illustrato il mapping del tipo tra un'istanza di livello principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i client legacy.
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Formato predefiniti dei valori letterali stringa passati al client legacy|ODBC delle versioni precedenti|OLEDB delle versioni precedenti|JDBC delle versioni precedenti|SQLCLIENT delle versioni precedenti|  
| --- | --- | --- | --- | --- | --- |
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**data**|YYYY-MM-DD|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetime2**|AAAA-MM-GG hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetimeoffset**|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [+ &#124;-] hh: mm|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
  
## <a name="converting-date-and-time-data"></a>La conversione dei dati di data e ora
Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
### <a name="converting-other-date-and-time-types-to-the-datetime2-data-type"></a>Conversione di altri tipi di data e ora per il tipo di dati datetime2
In questa sezione viene descritto cosa accade quando vengono convertiti in altri tipi di dati data e ora di **datetime2** tipo di dati.  
  
Quando la conversione è da **data**, l'anno, mese e giorno vengono copiati.  Il componente della fase è impostato su 00.00.00.0000000.  Nel codice seguente vengono illustrati i risultati della conversione di un valore `date` in un valore `datetime2`.  
  
```sql
DECLARE @date date = '12-21-16';
DECLARE @datetime2 datetime2 = @date;

SELECT @datetime2 AS '@datetime2', @date AS '@date';
  
--Result  
--@datetime2                  @date
----------------------------- ----------
--2016-12-21 00:00:00.0000000 2016-12-21
```  
  
Quando la conversione è da **Time (n)**, viene copiato il componente di ora e il componente Data è impostato su ' 1900-01-01'. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `time(7)` in un valore `datetime2`.  
  
```sql
DECLARE @time time(7) = '12:10:16.1234567';
DECLARE @datetime2 datetime2 = @time;

SELECT @datetime2 AS '@datetime2', @time AS '@time';
  
--Result  
--@datetime2                  @time
----------------------------- ----------------
--1900-01-01 12:10:16.1234567 12:10:16.1234567
```  
  
Quando la conversione è da **smalldatetime**, ore e minuti vengono copiati. mentre i secondi e i secondi frazionari vengono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `smalldatetime` in un valore `datetime2`.  
  
```sql
DECLARE @smalldatetime smalldatetime = '12-01-16 12:32';
DECLARE @datetime2 datetime2 = @smalldatetime;

SELECT @datetime2 AS '@datetime2', @smalldatetime AS '@smalldatetime'; 
  
--Result  
--@datetime2                  @smalldatetime
----------------------------- -----------------------
--2016-12-01 12:32:00.0000000 2016-12-01 12:32:00 
```  
  
Quando la conversione è da **DateTimeOffset (n)**, i componenti di data e ora vengono copiati. Il fuso orario viene troncato. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `datetimeoffset(7)` in un valore `datetime2`.  
  
```sql
DECLARE @datetimeoffset datetimeoffset(7) = '2016-10-23 12:45:37.1234567 +10:0';
DECLARE @datetime2 datetime2 = @datetimeoffset;

SELECT @datetime2 AS '@datetime2', @datetimeoffset AS '@datetimeoffset'; 
  
--Result  
--@datetime2                  @datetimeoffset
----------------------------- ----------------------------------
--2016-10-23 12:45:37.1234567 2016-10-23 12:45:37.1234567 +10:00
```  

Quando la conversione è da **datetime**, data e ora vengono copiati.  La precisione frazionaria è esteso a 7 cifre.  Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `datetime` in un valore `datetime2`.

```sql
DECLARE @datetime datetime = '2016-10-23 12:45:37.333';
DECLARE @datetime2 datetime2 = @datetime;

SELECT @datetime2 AS '@datetime2', @datetime AS '@datetime';
   
--Result  
--@datetime2                  @datetime
------------------------- ---------------------------
--2016-10-23 12:45:37.3333333 2016-10-23 12:45:37.333
```  
  
### <a name="converting-string-literals-to-datetime2"></a>Conversione di valori letterali stringa nel tipo di dati datetime2  
Le conversioni da valori letterali stringa a tipi di data e ora sono consentite se tutte le parti delle stringhe hanno formati validi. In caso contrario, viene generato un errore di runtime. Le conversioni implicite o esplicite che non specificano uno stile, dai tipi di data e ora ai valori letterali stringa, saranno nel formato predefinito della sessione corrente. Nella tabella seguente vengono illustrate le regole per la conversione di una stringa letterale per il **datetime2** tipo di dati.
  
|Valore letterale stringa di input|**datetime2**|  
|---|---|
|ODBC DATE|Vengono eseguito il mapping di valori letterali stringa ODBC per la **datetime** tipo di dati. Qualsiasi operazione di assegnazione dai valori letterali di ODBC DATETIME in **datetime2** tipi provocheranno una conversione implicita tra **datetime** e questo tipo in base a quanto definito dalle regole di conversione.|  
|ODBC TIME|Vedere la regola relativa a ODBC DATE.|  
|ODBC DATETIME|Vedere la regola relativa a ODBC DATE.|  
|Solo DATE|Il valore predefinito per la parte di TIME è 00:00:00.|  
|solo TIME|Il valore predefinito per la parte di DATE è 1900-1-1.|  
|solo TIMEZONE|Vengono forniti i valori predefiniti.|  
|DATE + TIME|Semplice|  
|DATE + TIMEZONE|Non consentiti.|  
|TIME + TIMEZONE|Il valore predefinito per la parte di DATE è 1900-1-1. L'input TIMEZONE viene ignorato.|  
|DATE + TIME + TIMEZONE|Verrà utilizzato DATETIME locale.|  
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa a ciascun **data** e **ora** tipo di dati.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
|Tipo di dati|Output|  
|---|---|
|**time**|12:35:29. 1234567|  
|**data**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
