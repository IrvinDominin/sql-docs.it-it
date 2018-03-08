---
title: funzione Lower-case (XQuery) | Documenti Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- lower-case Function (XQuery)
- lower-case
ms.assetid: 5222c4ff-890c-4d57-8506-c065a5ebfd3e
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b03fbc55fbcf7d49e318480ab42af1339aac1be0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="functions-on-string-values---lower-case"></a>Funzioni su valori stringa - lettere minuscole
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  La funzione Lower-case converte ogni carattere di *$arg* per equivalente minuscolo. La modalità di conversione dei caratteri nell'equivalente minuscolo viene specificata dalla conversione binaria di maiuscole e minuscole di Microsoft Windows per i punti di codice Unicode. Questo standard non è identico al mapping per lo standard dei punti di codice Unicode.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn:lower-case($arg as xs:string?) as xs:string  
```  
  
## <a name="arguments"></a>Argomenti  
  
|||  
|-|-|  
|Nome|Definizione|  
|*$arg*|Valore della stringa da convertire in lettere minuscole.|  
  
## <a name="remarks"></a>Osservazioni  
 Se il valore di *$arg* è vuoto, viene restituita una stringa di lunghezza zero.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-a-string-to-upper-case"></a>A. Conversione di una stringa in lettere maiuscole  
 L'esempio seguente modifica la stringa di input ' abcDEF! @4' in lettere minuscole.  
  
```  
DECLARE @x xml = N'abcDEF!@4';  
SELECT @x.value('fn:lower-case(/text()[1])', 'nvarchar(10)');  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
 `abcdef!@4`  
  
### <a name="b-search-for-a-specific-character-string"></a>B. Ricerca di una stringa di caratteri specifica  
 In questo esempio viene illustrato come utilizzare la funzione lower-case per eseguire un ricerca senza distinzione tra maiuscole e minuscole.  
  
```  
USE AdventureWorks  
GO  
--WITH XMLNAMESPACES clause specifies the namespace prefix  
--to use.   
WITH XMLNAMESPACES ('http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
--The XQuery contains() function is used to determine whether  
--any of the text nodes below the <Summary> element contain  
--the word 'frame'. The lower-case() function makes the   
--case insensitive.  
  
SELECT ProductModelID, CatalogDescription.query('  
      <Prod>  
         { /pd:ProductDescription/@ProductModelID }  
         { /pd:ProductDescription/pd:Summary }  
      </Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
/pd:ProductDescription/pd:Summary//text()[  
          contains(lower-case(.), "FRAME")]')  = 1  
```  
  
 [!INCLUDE[ssResult](../includes/ssresult-md.md)]  
  
 `ProductModelID Result`  
  
 `-------------- ---------`  
  
 `19     <Prod ProductModelID="19">`  
  
 `<pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">Our top-of-the-line competition mountain bike.`  
  
 `Performance-enhancing options include the innovative HL Frame,`  
  
 `super-smooth front suspension, and traction for all terrain.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
 `25     <Prod ProductModelID="25">`  
  
 `<pd:Summary xmlns:pd="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">`  
  
 `<p1:p xmlns:p1="http://www.w3.org/1999/xhtml">This bike is ridden by race winners. Developed with the`  
  
 `Adventure Works Cycles professional race team, it has a extremely light`  
  
 `heat-treated aluminum frame, and steering that allows precision control.`  
  
 `</p1:p>`  
  
 `</pd:Summary>`  
  
 `</Prod>`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati XML](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
