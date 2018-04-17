---
title: Operatori di XQuery per il tipo di dati xml | Documenti Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- XQuery, operators
- operators [XQuery]
- xml data type [SQL Server], XQuery
ms.assetid: 39ca3d2e-e928-4333-872b-75c4ccde8e79
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ac5a80100f76b63286d0744503427f9f58bc0750
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="xquery-operators-against-the-xml-data-type"></a>Operatori di XQuery per il tipo di dati xml
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery supporta gli operatori seguenti:  
  
-   Operatori numerici (+, -, *, div, mod)  
  
-   Operatori di confronto per i valori (eq, ne, lt, gt, le, ge)  
  
-   Operatori di confronto generali (=,! =, \<, >, \<=, > =)  
  
 Per ulteriori informazioni su questi operatori, vedere [espressioni di confronto &#40;XQuery&#41;](../xquery/comparison-expressions-xquery.md)  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-general-operators"></a>A. Utilizzo degli operatori generali  
 La query seguente illustra l'utilizzo degli operatori generali validi per le sequenze e inoltre per le sequenze di confronto. La query recupera una sequenza di numeri di telefono per ogni cliente dal **AdditionalContactInfo** colonna il **contatto** tabella. La sequenza viene quindi confrontata con la sequenza di due numeri di telefono ("111-111-1111", "222-2222").  
  
 La query utilizza il **=** operatore di confronto. Ogni nodo della sequenza a destra del **=** operatore viene confrontato con ogni nodo nella sequenza sul lato sinistro. Se i nodi corrispondono, il confronto è **TRUE**. Viene quindi convertito in un tipo di dati int e confrontato con 1, quindi la query restituisce l'ID del cliente.  
  
```  
WITH XMLNAMESPACES (  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo' AS ACI,  
'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes' AS ACT)  
SELECT ContactID   
FROM   Person.Contact  
WHERE  AdditionalContactInfo.value('  
      //ACI:AdditionalContactInfo//ACT:telephoneNumber/ACT:number =   
          ("111-111-1111", "222-2222")',  
      'bit')= cast(1 as bit)  
```  
  
 È possibile osservare il funzionamento della query precedente: ogni valore di numero telefonico telefono recuperati il **AdditionalContactInfo** colonna viene confrontata con il set di due numeri di telefono. Se il numero è presente nel set, nel risultato viene restituito il cliente.  
  
### <a name="b-using-a-numeric-operator"></a>B. Utilizzo di un operatore numerico  
 L'operatore + nella query è un operatore per i valori, perché viene applicato a un singolo elemento. Ad esempio, il valore 1 viene aggiunto alle dimensioni di un lotto restituite dalla query:  
  
```  
SELECT ProductModelID, Instructions.query('  
     declare namespace   
 AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     for $i in (/AWMI:root/AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"  
                   LotSize  = "{  number($i/@LotSize) }"  
                   LotSize2 = "{ number($i/@LotSize) + 1 }"  
                   LotSize3 = "{ number($i/@LotSize) + 2 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
### <a name="c-using-a-value-operator"></a>C. Utilizzo di un operatore per valori  
 La query seguente recupera gli elementi <`Picture`> per un modello di prodotto per cui le dimensioni dell'immagine sono "small":  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $P in /PD:ProductDescription/PD:Picture[PD:Size eq "small"]  
     return  
           $P  
    ') as Result  
FROM Production.ProductModel  
where ProductModelID=19  
```  
  
 Poiché entrambi gli operandi di **eq** operatore sono valori atomici, l'operatore di valore viene utilizzato nella query. È possibile scrivere la stessa query utilizzando l'operatore di confronto generali ( **=** ).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni XQuery per il tipo di dati xml](../xquery/xquery-functions-against-the-xml-data-type.md)   
 [Dati XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Riferimento al linguaggio XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
