---
title: PARSE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PARSE
- PARSE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PARSE function
ms.assetid: 6a2dbf10-f692-471b-9458-24d246963049
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3e172a7d68edc212ce4803103dc1f975e4bf89db
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="parse-transact-sql"></a>PARSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Restituisce il risultato di un'espressione, convertito nel tipo di dati richiesto in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PARSE ( string_value AS data_type [ USING culture ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *valore_stringa*  
 **nvarchar**valore (4000) che rappresenta il valore formattato da analizzare nel tipo di dati specificato.  
  
 *valore_stringa* deve essere una rappresentazione valida del tipo di dati richiesto o contrario PARSE genera un errore.  
  
 *data_type*  
 Valore letterale che rappresenta il tipo di dati richiesto per il risultato.  
  
 *impostazioni cultura*  
 Stringa facoltativa che identifica le impostazioni cultura in cui *valore_stringa* viene formattato.  
  
 Se il *delle impostazioni cultura* argomento non viene specificato, quindi viene utilizzata la lingua della sessione corrente. Tale lingua viene impostata in modo implicito o in modo esplicito tramite l'istruzione SET LANGUAGE. *impostazioni cultura* accetta qualsiasi impostazione cultura supportata da .NET Framework; non è limitato alle lingue supportate in modo esplicito da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se il *delle impostazioni cultura* argomento non è valido, PARSE genera un errore.  
  
## <a name="return-types"></a>Tipi restituiti  
 Restituisce il risultato dell'espressione, convertito nel tipo di dati richiesto.  
  
## <a name="remarks"></a>Osservazioni  
 Eventuali valori Null passati come argomenti a PARSE vengono trattati in due modalità:  
  
1.  Se viene passata una costante Null, viene generato un errore. Un valore Null non può essere analizzato in un tipo di dati diverso in modo consapevole.  
  
2.  Se viene passato un parametro con valore Null in fase di esecuzione, viene restituito un valore Null per evitare di annullare l'intero batch.  
  
 Utilizzare PARSE solo per la conversione da stringa a data/ora e tipi di numero. Per le conversioni di tipi generali, continuare a utilizzare CAST o CONVERT. È opportuno ricordare che si verifica un sovraccarico nelle prestazioni durante l'analisi del valore stringa.  
  
 ANALISI si basa sulla presenza di .NET Framework Common Language Runtime (CLR).  
  
 Questa funzione non sarà eseguita in modalità remota poiché dipende dalla presenza di CLR. L'esecuzione in modalità remota di una funzione che richiede CLR provocherebbe un errore sul server remoto.  
  
 **Ulteriori informazioni sul parametro data_type**  
  
 I valori per il *data_type* parametro sono limitati ai tipi mostrati nella tabella seguente, insieme con gli stili. Le informazioni sugli stili vengono fornite per determinare i tipi di modelli consentiti. Per ulteriori informazioni sugli stili, vedere la documentazione di .NET Framework per la **System.Globalization.NumberStyles** e **DateTimeStyles** enumerazioni.  
  
|Category|Tipo|Tipo .NET Framework|Stili utilizzati|  
|--------------|----------|-------------------------|-----------------|  
|Numeric|bigint|Int64|NumberStyles.Number|  
|Numeric|int|Int32|NumberStyles.Number|  
|Numeric|smallint|Int16|NumberStyles.Number|  
|Numeric|tinyint|Byte|NumberStyles.Number|  
|Numeric|decimal|Decimal|NumberStyles.Number|  
|Numeric|numeric|Decimal|NumberStyles.Number|  
|Numeric|float|Double|NumberStyles.Float|  
|Numeric|real|Single|NumberStyles.Float|  
|Numeric|smallmoney|Decimal|NumberStyles.Currency|  
|Numeric|money|Decimal|NumberStyles.Currency|  
|Data e ora|data|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Data e ora|time|TimeSpan|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Data e ora|datetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Data e ora|smalldatetime|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Data e ora|datetime2|DateTime|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
|Data e ora|datetimeoffset|DateTimeOffset|DateTimeStyles.AllowWhiteSpaces &#124; DateTimeStyles.AssumeUniversal|  
  
 **Ulteriori informazioni sul parametro delle impostazioni cultura**  
  
 Nella tabella seguente vengono mostrati i mapping dai linguaggi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle impostazioni cultura di .NET Framework.  
  
|Nome completo|Alias|LCID|Impostazioni cultura specifiche|  
|---------------|-----------|----------|----------------------|  
|us_english|Inglese|1033|it-IT|  
|Deutsch|Tedesco|1031|de-DE|  
|Français|Francese|1036|fr-FR|  
|日本語|Giapponese|1041|ja-JP|  
|Dansk|Danese|1030|da-DK|  
|Español|Spagnolo|3082|es-ES|  
|Italiano|Italiano|1040|it-IT|  
|Nederlands|Olandese|1043|nl-NL|  
|Norsk|Norvegese|2068|nn-NO|  
|Português|Portoghese|2070|pt-PT|  
|Suomi|Finlandese|1035|fi|  
|Svenska|Svedese|1053|sv-SE|  
|Čeština|Ceco|1029|Cs-CZ|  
|magyar|Ungherese|1038|Hu-HU|  
|polski|Polacco|1045|Pl-PL|  
|română|Romeno|1048|Ro-RO|  
|hrvatski|Croato|1050|hr-HR|  
|slovenčina|Slovacco|1051|Sk-SK|  
|slovenski|Sloveno|1060|Sl-SI|  
|ΕΛΛΗΝΙΚΆ|Greco|1032|El-GR|  
|БЪЛГАРСКИ|Bulgaro|1026|bg-BG|  
|РУССКИЙ|Russo|1049|Ru-RU|  
|Türkçe|Turco|1055|Tr-TR|  
|British|Inglese (Regno Unito)|2057|en-GB|  
|eesti|Estone|1061|Et-EE|  
|latviešu|Lettone|1062|lv-LV|  
|lietuvių|Lituano|1063|lt-LT|  
|Português (Brasile)|Portoghese (Brasile)|1046|pt-BR|  
|繁體中文|Cinese tradizionale|1028|zh-TW|  
|한국어|Coreano|1042|Ko-KR|  
|简体中文|Cinese semplificato|2052|zh-CN|  
|Arabo|Arabo|1025|ar-SA|  
|ไทย|Thai|1054|Th-TH|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-parse-into-datetime2"></a>A. PARSE in datetime2  
  
```  
SELECT PARSE('Monday, 13 December 2010' AS datetime2 USING 'en-US') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-13 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
### <a name="b-parse-with-currency-symbol"></a>B. PARSE con simbolo di valuta  
  
```  
SELECT PARSE('€345,98' AS money USING 'de-DE') AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
345.98  
  
(1 row(s) affected)  
```  
  
### <a name="c-parse-with-implicit-setting-of-language"></a>C. PARSE con impostazione implicita di linguaggio  
  
```  
-- The English language is mapped to en-US specific culture  
SET LANGUAGE 'English';  
SELECT PARSE('12/16/2010' AS datetime2) AS Result;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------  
2010-12-16 00:00:00.0000000  
  
(1 row(s) affected)  
```  
  
  
