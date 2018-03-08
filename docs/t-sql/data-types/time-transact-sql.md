---
title: ora (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 6/7/2017
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
- time_TSQL
- time
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- time [SQL Server]
- date and time [SQL Server], time
- data types [SQL Server], date and time
- time data type [SQL Server]
ms.assetid: 30a6c681-8190-48e4-94d0-78182290a402
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 4a5a46eee481e9da3f388f88e982d705dbe150ea
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="time-transact-sql"></a>time (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Definisce l'ora di un giorno. Il fuso orario non viene preso in considerazione e il formato è basato sulle 24 ore.  
  
  > [!NOTE]  
  > Vengono fornite informazioni di informatica per i clienti PDW utilizzando il connettore di Informatica. 
  
## <a name="time-description"></a>Descrizione di time  
  
|Proprietà|Valore|  
|--------------|-----------|  
|Sintassi|**tempo** [(*frazionaria seconda scala*)]|  
|Utilizzo|DICHIARARE @MyTime **Time (7)**<br /><br /> CREARE una tabella Table1 (Column1 **Time (7)** )|  
|*scala di frazioni*|Specifica il numero di cifre per la parte frazionaria dei secondi.<br /><br /> Può essere un numero intero compreso tra 0 e 7. Per Informatica, può essere un intero compreso tra 0 e 3.<br /><br /> La scala di frazioni di predefinita è 7 (100 ns).|  
|Formato predefinito dei valori letterali stringa<br /><br /> (utilizzato per client legacy)|hh.mm.ss [. nnnnnnn] per Informatica)<br /><br /> Per ulteriori informazioni, vedere la sezione seguente relativa alla compatibilità con le versioni precedenti per i client legacy.|  
|Intervallo|00.00.00.0000000 e 23.59.59.9999999 (00.00.00.000 tramite 23:59:59.999 per Informatica)|  
|Intervalli di elementi|hh rappresenta un numero di due cifre tra 0 e 23 indicante l'ora.<br /><br /> mm rappresenta un numero di due cifre tra 0 e 59 indicante i minuti.<br /><br /> ss rappresenta un numero di due cifre tra 0 e 59 indicante i secondi.<br /><br /> n\*è uguale a zero a sette cifre, compreso tra 0 e 9999999, indicante i secondi frazionari. Per Informatica, n\* è uguale a zero a tre cifre, compreso tra 0 e 999.|  
|Lunghezza in caratteri|da 8 posizioni minimo (hh:mm:ss) a 16 massimo (hh:mm:ss.nnnnnnn) Per Informatica, il valore massimo è 12 (hh:mm:ss.nnn).|  
|Precisione, scala<br /><br /> (l'utente specifica solo la scala)|Vedere la tabella riportata di seguito.|  
|Dimensioni dello spazio di archiviazione|5 byte, fisso è l'impostazione predefinita con la precisione in secondi frazionari predefinita pari a 100 ns. In Informatica, il valore predefinito è 4 byte, fissate, con il valore predefinito di 1 ms frazionari secondo precisione.|  
|Accuratezza|100 nanosecondi (1 millisecondo in Informatica)|  
|Valore predefinito|00:00:00<br /><br /> Questo valore viene utilizzato per la parte del tempo aggiunta per la conversione implicita da **data** a **datetime2** o **datetimeoffset**.|  
|Precisione in secondi frazionari definita dall'utente|Sì|  
|Considerazione e conservazione delle differenze di fuso orario|No|  
|Considerazione dell'ora legale|No|  
  
|Scala specificata|Risultato (precisione, scala)|Lunghezza della colonna (byte)|Precisione<br /><br /> secondi<br /><br /> precisione|  
|---------------------|---------------------------------|-----------------------------|------------------------------------------|  
|**time**|(16,7) [(12,3) in Informatica]|5 (4 in Informatica)|7 (3 in Informatica)|  
|**time(0)**|(8,0)|3|0-2|  
|**Time(1)**|(10,1)|3|0-2|  
|**Time(2)**|(11,2)|3|0-2|  
|**Time(3)**|(12,3)|4|3-4|  
|**Time(4)**<br /><br /> Non è supportato in Informatica.|(13,4)|4|3-4|  
|**Time(5)**<br /><br /> Non è supportato in Informatica.|(14,5)|5|5-7|  
|**Time(6)**<br /><br /> Non è supportato in Informatica.|(15,6)|5|5-7|  
|**time(7)**<br /><br /> Non è supportato in Informatica.|(16,7)|5|5-7|  
  
## <a name="supported-string-literal-formats-for-time"></a>Formati di valore letterale stringa supportati per l'ora  
 La tabella seguente mostra la stringa di formati di valore letterale per il **ora** tipo di dati.  
  
|SQL Server|Description|  
|----------------|-----------------|  
|hh:mm [: ss][:secondi frazionari][AM][PM]<br /><br /> hh:mm [: ss].secondi frazionari][AM][PM]<br /><br /> hhAM[PM]<br /><br /> hh AM [PM]|Il valore relativo all'ora 0 rappresenta l'ora dopo mezzanotte (AM), indipendentemente dall'indicazione AM. Non è possibile specificare PM quando l'ora è uguale a 0.<br /><br /> I valori di ora compresi tra 01 e 11 rappresentano le ore antimeridiane (prima di mezzogiorno) se non si specifica né AM né PM. Se si specifica AM, i valori indicano le ore prima di mezzogiorno, mentre rappresentano le ore postmeridiane (dopo mezzogiorno) se si specifica PM.<br /><br /> Il valore di ora 12 rappresenta l'ora che inizia a mezzogiorno se non si specifica né AM né PM. Rappresenta invece l'ora che inizia a mezzanotte se si specifica AM e l'ora che inizia a mezzogiorno se si specifica PM. Ad esempio, 12:01 indica un minuto dopo mezzogiorno, così come 12:01 PM, mentre 12:01 AM indica un minuto dopo la mezzanotte. 12:01 AM equivale a 00:01 o 00:01 AM.<br /><br /> I valori di ora compresi tra 13 e 23 rappresentano le ore postmeridiane se non si specifica né AM né PM e le ore postmeridiane se si specifica PM. Non è possibile specificare AM per valori di ora compresi tra 13 e 23.<br /><br /> Un valore relativo all'ora 24 non è valido. Per indicare la mezzanotte, utilizzare 12:00 AM o 00:00.<br /><br /> È possibile far precedere i millisecondi dai due punti (:) o da un punto (.). Se si utilizzano i due punti, il valore indica i millesimi di secondo. Un valore preceduto da un punto indica i decimi di secondo se è composto da una sola cifra, i centesimi di secondo se è composto da due cifre e i millesimi di secondo se è composto da tre cifre. Ad esempio, 12:30:20:1 indica che sono trascorsi 20 secondi e un millesimo di secondo dalle 12:30, mentre 12:30:20.1 indica che sono trascorsi venti secondi e un decimo di secondo dalle 12:30.|  
  
|ISO 8601|Note|  
|--------------|-----------|  
|hh:mm:ss<br /><br /> hh:mm[:ss][.secondi frazionari]|hh è un numero di due cifre, compreso tra 0 e 14, che rappresenta il numero di ore della differenza di fuso orario.<br /><br /> mm è un numero di due cifre, tra 0 e 59, che rappresenta il numero di minuti aggiuntivi della differenza di fuso orario.|  
  
|ODBC|Note|  
|----------|-----------|  
|{t 'hh.mm.ss[.secondi frazionari]'}|Specifico delle API ODBC|  
  
## <a name="compliance-with-ansi-and-iso-8601-standards"></a>Conformità agli standard ANSI e ISO 8601  
 L'utilizzo dell'ora 24 per indicare la mezzanotte e del secondo del salto a 59 come definito dall'ISO 8601(5.3.2 e 5.3) non è supportato per essere compatibile con i tipi di data ed ora esistenti.  
  
 Il formato predefinito dei valori letterali stringa utilizzato per i client legacy risulterà compatibile con il formato standard SQL, definito come hh:mm:ss[.nnnnnnn]. Questo formato assomiglia alla definizione ISO 8601 per TIME che esclude i secondi frazionari.  
  
##  <a name="BackwardCompatibilityforDownlevelClients"></a>Compatibilità con le versioni precedenti per i client legacy  
 Alcuni client legacy non supportano il **ora**, **data**, **datetime2** e **datetimeoffset** tipi di dati. Nella tabella seguente viene illustrato il mapping del tipo tra un'istanza di livello principale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e i client legacy.  
  
|Tipo di dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Formato predefiniti dei valori letterali stringa passati al client legacy|ODBC delle versioni precedenti|OLEDB delle versioni precedenti|JDBC delle versioni precedenti|SQLCLIENT delle versioni precedenti|  
|-----------------------------------------|----------------------------------------------------------------|----------------------|-----------------------|----------------------|---------------------------|  
|**time**|hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**data**|YYYY-MM-DD|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetime2**|AAAA-MM-GG hh:mm:ss[.nnnnnnn]|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
|**datetimeoffset**|AAAA-MM-gg hh.mm.ss [. nnnnnnn] [+ &#124;-] hh: mm|SQL_WVARCHAR o SQL_VARCHAR|DBTYPE_WSTR o DBTYPE_STR|Java.sql.String|Stringa o SqString|  
  
## <a name="converting-date-and-time-data"></a>Conversione dei dati relativi alla data e all'ora  
 Nella conversione di tipi di dati relativi alla data e all'ora, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono rifiutati tutti i valori non riconosciuti come date o orari. Per informazioni sull'utilizzo delle funzioni CAST e CONVERT con dati di data e ora, vedere [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
### <a name="converting-timen-data-type-to-other-date-and-time-types"></a>Conversione del tipo di dati time(n) in altri tipi di dati relativi a data e ora  
 In questa sezione viene descritto cosa accade quando un **ora** tipo di dati viene convertito in altri tipi di dati data e ora.  
  
 Quando la conversione viene eseguita a **Time (n)**, l'ora, minuti e secondi vengono copiati. Quando la precisione della destinazione è minore di quella dell'origine, i secondi frazionari verranno arrotondati per rispettare la precisione della destinazione. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un valore `time(3)`.  
  
```  
DECLARE @timeFrom time(4) = '12:34:54.1237';  
DECLARE @timeTo time(3) = @timeFrom;  
  
SELECT @timeTo AS 'time(3)', @timeFrom AS 'time(4)';  
  
--Results  
--time(3)      time(4)  
-------------- -------------  
--12:34:54.124 12:34:54.1237  
--  
--(1 row(s) affected)  
```  
  
 Se la conversione a  
                    **Data**, la conversione non riesce e viene generato il messaggio di errore 206: "conflitto del tipo di operando: date è incompatibile con time".  
  
 Quando la conversione viene eseguita a **datetime**, ora, minuto e secondo valori vengono copiati e il componente Data è impostato su ' 1900-01-01'. Quando la precisione dei secondi frazionari del **Time (n)** valore è maggiore di tre cifre, il **datetime** risultato verrà troncato. Nel codice seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un valore `datetime`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime datetime= @time;  
SELECT @time AS '@time', @datetime AS '@datetime';  
  
--Result  
--@time         @datetime  
--------------- -----------------------  
--12:15:04.1237 1900-01-01 12:15:04.123  
--  
--(1 row(s) affected)  
  
```  
  
 Quando la conversione viene eseguita a **smalldatetime**, la data viene impostata su ' 1900-01-01' e i valori di ora e i minuti vengono arrotondati per eccesso. mentre i secondi e i secondi frazionari vengono impostati su 0. Nel codice seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un valore `smalldatetime`.  
  
```  
-- Shows rounding up of the minute value.  
DECLARE @time time(4) = '12:15:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';   
  
--Result  
@time            @smalldatetime  
---------------- -----------------------  
12:15:59.9999    1900-01-01 12:16:00--  
--(1 row(s) affected)  
  
-- Shows rounding up of the hour value.  
DECLARE @time time(4) = '12:59:59.9999';   
DECLARE @smalldatetime smalldatetime= @time;    
  
SELECT @time AS '@time', @smalldatetime AS '@smalldatetime';  
@time            @smalldatetime  
---------------- -----------------------  
12:59:59.9999    1900-01-01 13:00:00  
  
(1 row(s) affected)  
  
```  
  
 Se la conversione a **DateTimeOffset (n)**, la data viene impostata su ' 1900-01-01' e l'ora viene copiato. La differenza di fuso orario è impostata su +00:00. Quando la precisione dei secondi frazionari del **Time (n)** è maggiore della precisione del valore di **DateTimeOffset (n)** valore, il valore viene arrotondato per eccesso per adattarla. Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un tipo `datetimeoffset(3)`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetimeoffset datetimeoffset(3) = @time;  
  
SELECT @time AS '@time', @datetimeoffset AS '@datetimeoffset';  
  
--Result  
--@time         @datetimeoffset  
--------------- ------------------------------  
--12:15:04.1237 1900-01-01 12:15:04.124 +00:00  
--  
--(1 row(s) affected)  
  
```  
  
 Durante la conversione in **datetime2**, la data viene impostata su ' 1900-01-01', viene copiato il componente di ora e differenza di fuso orario è impostata su 00:00. Quando la precisione dei secondi frazionari del **datetime2** valore è maggiore di **Time (n)** valore, il valore verrà arrotondato per eccesso per adattarla.  Nell'esempio seguente vengono illustrati i risultati della conversione di un valore `time(4)` in un valore `datetime2(2)`.  
  
```  
DECLARE @time time(4) = '12:15:04.1237';  
DECLARE @datetime2 datetime2(3) = @time;  
  
SELECT @datetime2 AS '@datetime2', @time AS '@time';  
  
--Result  
--@datetime2              @time  
------------------------- -------------  
--1900-01-01 12:15:04.124 12:15:04.1237  
--  
--(1 row(s) affected)  
```  
  
### <a name="converting-string-literals-to-timen"></a>Conversione di valori letterali stringa nel tipo di dati time(n)  
 Le conversioni da valori letterali stringa a tipi di data e ora sono consentite se tutte le parti delle stringhe hanno formati validi. In caso contrario, viene generato un errore di runtime. Le conversioni implicite o esplicite che non specificano uno stile, dai tipi di data e ora ai valori letterali stringa, saranno nel formato predefinito della sessione corrente. Nella tabella seguente vengono illustrate le regole per la conversione di una stringa letterale per il **ora** tipo di dati.  
  
|Valore letterale stringa di input|Regola di conversione|  
|--------------------------|---------------------|  
|ODBC DATE|Vengono eseguito il mapping di valori letterali stringa ODBC per la **datetime** tipo di dati. Qualsiasi operazione di assegnazione dai valori letterali di ODBC DATETIME in **ora**tipi provocheranno una conversione implicita tra **datetime** e questo tipo in base a quanto definito dalle regole di conversione.|  
|ODBC TIME|Vedere la regola per ODBC DATE descritta in precedenza.|  
|ODBC DATETIME|Vedere la regola per ODBC DATE descritta in precedenza.|  
|Solo DATE|Vengono forniti i valori predefiniti.|  
|solo TIME|Semplice|  
|solo TIMEZONE|Vengono forniti i valori predefiniti.|  
|DATE + TIME|Viene utilizzata la parte di TIME della stringa di input.|  
|DATE + TIMEZONE|Non consentiti.|  
|TIME + TIMEZONE|Viene utilizzata la parte di TIME della stringa di input.|  
|DATE + TIME + TIMEZONE|Verrà utilizzata la parte TIME di DATETIME locale.|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-comparing-date-and-time-data-types"></a>A. Confronto dei tipi di dati di data e ora  
 Nell'esempio seguente vengono confrontati i risultati dell'esecuzione del cast di una stringa a ciascun **data** e **ora** tipo di dati.  
  
```  
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
  
|Tipo di dati|Output|  
|---------------|------------|  
|**time**|12:35:29. 1234567|  
|**data**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
###  <a name="ExampleB"></a> B. Inserimento dei valori letterali stringa dell'ora validi in una colonna time(7)  
 Nella tabella seguente sono elencati i diversi valori letterali stringa che possono essere inseriti in una colonna di tipo di dati **Time (7)** con i valori che vengono quindi archiviati in tale colonna.  
  
|Tipo di formato dei valori letterali stringa|Valore letterale stringa inserito|Valore time(7) archiviato|Description|  
|--------------------------------|-----------------------------|------------------------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|01:01:01:123AM|01:01:01.1230000|Se prima della precisione frazionaria dei secondi vengono utilizzati i due punti (:), la scala non può superare tre posizioni o verrà generato un errore.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 AM'|01:01:01.1234567|Quando si specificano AM o PM, l'ora viene archiviata in formato di 24 ore senza l'AM o il PM letterale.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567 PM'|13:01:01.1234567|Quando si specificano AM o PM, l'ora viene archiviata in formato di 24 ore senza l'AM o il PM letterale.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01.1234567PM'|13:01:01.1234567|Lo spazio prima dell'indicazione AM o PM è facoltativo.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01AM'|01:00:00.0000000|Quando viene specificata solo l'ora, tutti gli altri valori sono uguali a 0.|  
|SQL Server|'01 AM'|01:00:00.0000000|Lo spazio prima dell'indicazione AM o PM è facoltativo.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|'01:01:01'|01:01:01.0000000|Quando la precisione frazionaria dei secondi non è specificata, ogni posizione definita dal tipo di dati è 0.|  
|ISO 8601|'01:01:01.1234567'|01:01:01.1234567|Per essere conforme allo standard ISO 8601, utilizzare il formato delle 24 ore, non AM o PM.|  
|ISO 8601|'01:01:01.1234567 +01:01'|01:01:01.1234567|La differenza del fuso orario facoltativa (TZD) è consentita nell'input ma non viene archiviata.|  
  
### <a name="c-inserting-time-string-literal-into-columns-of-each-date-and-time-date-type"></a>C. Inserimento del valore letterale stringa nelle colonne di ogni tipo di dati relativi a data e ora  
 Nella tabella seguente la prima colonna indica il valore letterale stringa dell'ora da inserire nella colonna della tabella del database della data o dell'ora visualizzate nella seconda colonna. La terza colonna indica il valore che verrà memorizzato nella colonna della tabella del database.  
  
|Valore letterale stringa inserito|Tipo di dati colonna|Valore archiviato nella colonna|Description|  
|-----------------------------|----------------------|------------------------------------|-----------------|  
|'12:12:12.1234567'|**time(7)**|12:12:12.1234567|Se la precisione frazionaria dei secondi supera il valore specificato per la colonna, la stringa sarà troncata senza errori.|  
|'2007-05-07'|**data**|NULL|Qualsiasi valore dell'ora genererà un errore nell'istruzione INSERT|  
|'12:12:12'|**smalldatetime**|1900-01-01 12:12:00|Qualsiasi valore della precisione frazionaria dei secondi genererà un errore nell'istruzione INSERT.|  
|'12:12:12.123'|**datetime**|1900-01-01 12:12:12.123|Qualsiasi precisione dei secondi maggiore di tre posizioni genera un errore nell'espressione INSERT.|  
|'12:12:12.1234567'|**datetime2(7)**|1900-01-01 12:12:12.1234567|Se la precisione frazionaria dei secondi supera il valore specificato per la colonna, la stringa sarà troncata senza errori.|  
|'12:12:12.1234567'|**DateTimeOffset(7)**|1900-01-01 12:12:12.1234567 +00:00|Se la precisione frazionaria dei secondi supera il valore specificato per la colonna, la stringa sarà troncata senza errori.|  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  
