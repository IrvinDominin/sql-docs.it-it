---
title: Usare query FOR XML annidate | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a804585f215b7328890d2f0400c77307af7b1b4b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211141"
---
# <a name="use-nested-for-xml-queries"></a>Utilizzo di query FOR XML nidificate
  Il `xml` tipo di dati e la [direttiva TYPE nelle query FOR XML](type-directive-in-for-xml-queries.md) Abilita l'elaborazione del XML restituito dalle query FOR XML sul server che sul client.  
  
## <a name="processing-with-xml-type-variables"></a>Elaborazione con variabili di tipo XML  
 È possibile assegnare il risultato di una query FOR XML a una variabile di tipo `xml` oppure utilizzare XQuery per eseguire query sul risultato, quindi assegnare tale risultato a una variabile di tipo `xml` per un'ulteriore elaborazione.  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 È inoltre possibile elaborare il codice XML restituito nella variabile `@x`, usando uno del `xml` metodi con tipo di dati. Ad esempio, è possibile recuperare il valore dell'attributo `ProductModelID` usando il [metodo value()](/sql/t-sql/xml/value-method-xml-data-type).  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 Nell'esempio seguente il risultato della query `FOR XML` viene restituito come tipo `xml`, perché nella clausola `TYPE` è specificata la direttiva `FOR XML`.  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 Risultato:  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 Poiché il risultato è di `xml` tipo, è possibile specificare uno del `xml` metodi direttamente al valore XML, con tipo di dati come illustrato nella query seguente. Nella query viene usato il [metodo query() con tipo di dati XML](/sql/t-sql/xml/query-method-xml-data-type) per recuperare il primo elemento <`row`> figlio dell'elemento <`myRoot`>.  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 Risultato:  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a>Restituzione di risultati della query FOR XML interna a query esterne come istanze di tipo XML  
 È possibile scrivere annidato `FOR XML` le query in cui il risultato della query interna viene restituito come un `xml` tipo per la query esterna. Esempio:  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 Dalla query precedente si noti quanto segue:  
  
-   Il valore XML generato dalla query `FOR XML` interna viene aggiunto al valore XML generato dalla query `FOR XML`esterna.  
  
-   Nella query interna viene specificata la direttiva `TYPE` . I dati restituiti dalla query interna sono pertanto di tipo `xml` . Se non si specifica la direttiva TYPE, il risultato della query `FOR XML` interna viene restituito come `nvarchar(max)` e i dati XML vengono sostituiti con entità.  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a>Controllo della forma dei dati XML risultanti  
 Le query FOR XML nidificate consentono di avere un maggior controllo nella definizione della forma dei dati XML risultanti. È possibile utilizzare query FOR XML nidificate per costruire valori XML che siano parzialmente incentrati sugli attributi e parzialmente sugli elementi.  
  
 Per altre informazioni su come specificare valori XML incentrati sia sugli attributi sia sugli elementi con query FOR XML nidificate, vedere [Query FOR XML e query nidificata FOR XML a confronto](../xml/for-xml-query-compared-to-nested-for-xml-query.md) e [Determinare la struttura dei valori XML tramite query nidificate FOR XML](../xml/shape-xml-with-nested-for-xml-queries.md).  
  
 È possibile generare gerarchie XML che includono elementi di pari livello eseguendo query FOR XML nidificate in modalità AUTO. Per altre informazioni, vedere [Generare elementi di pari livello tramite query nidificate in modalità AUTO](../xml/generate-siblings-with-a-nested-auto-mode-query.md).  
  
 Indipendentemente dalla modalità utilizzata, le query FOR XML nidificate consentono un maggior controllo nella definizione della forma dei valori XML risultanti e possono essere utilizzate in sostituzione delle query in modalità EXPLICIT.  
  
## <a name="examples"></a>Esempi  
 Negli argomenti seguenti vengono forniti esempi di query FOR XML nidificate.  
  
 [Query FOR XML e query nidificata FOR XML a confronto](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 Confronto di una query FOR XML con un solo livello con una query FOR XML nidificata. In questo esempio è inclusa una dimostrazione di come specificare valori XML incentrati sia sugli attributi sia sugli elementi come risultato della query.  
  
 [Generare elementi di pari livello tramite query nidificate in modalità AUTO](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 Procedura di generazione di elementi di pari livello tramite query nidificate in modalità AUTO  
  
 [Utilizzo di query FOR XML nidificate in ASP.NET](use-nested-for-xml-queries-in-asp-net.md)  
 Dimostrazione del modo in cui un'applicazione ASPX può utilizzare FOR XML per restituire XML da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Determinare la struttura dei valori XML tramite query nidificate FOR XML](../xml/shape-xml-with-nested-for-xml-queries.md)  
 Utilizzo di query FOR XML nidificate per controllare la struttura di un documento XML creato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
