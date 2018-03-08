---
title: Outer join | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outer join escape sequences [ODBC]
- escape sequences [ODBC], outer join
ms.assetid: be1a0203-5da9-4871-9566-4bd3fbc0895c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f217b7392b4db968e612f58b264e17f921a40aae
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="outer-joins"></a>Outer join
ODBC supporta SQL-92 a sinistra, la sintassi di right e full outer join. La sequenza di escape per gli outer join  
  
 **{GU** *outer join***}**  
  
 dove *outer join* è  
  
 *riferimento alla tabella* {**sinistra &#124; DESTRA &#124; FULL} OUTER JOIN** {*riferimento alla tabella* &#124; *outer join*} **ON** *condizione di ricerca*  
  
 *riferimento alla tabella* specifica un nome di tabella e *condizione di ricerca* specifica la condizione di join tra la *riferimenti alla tabella*.  
  
 Una richiesta di outer join deve essere visualizzate dopo il **FROM** (parola chiave) e prima di **dove** clausola (se presente). Per informazioni complete sulla sintassi, vedere [Outer Join sequenza di Escape](../../../odbc/reference/appendixes/outer-join-escape-sequence.md) nella grammatica SQL di appendice c:.  
  
 Ad esempio, le istruzioni SQL seguenti creano lo stesso set di risultati che elenca tutti i clienti e mostra che ha aperto gli ordini. La prima istruzione utilizza la sintassi della sequenza di escape. La seconda istruzione utilizza la sintassi nativa per Oracle e non è interoperativa.  
  
```  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM {oj Customers LEFT OUTER JOIN Orders ON Customers.CustID=Orders.CustID}  
   WHERE Orders.Status='OPEN'  
  
SELECT Customers.CustID, Customers.Name, Orders.OrderID, Orders.Status  
   FROM Customers, Orders  
   WHERE (Orders.Status='OPEN') AND (Customers.CustID= Orders.CustID(+))  
```  
  
 Per determinare i tipi di outer join che supportano un'origine dati e i driver, un'applicazione chiama **SQLGetInfo** con il SQL_OJ_CAPABILITIES flag. I tipi di outer join che potrebbero essere supportate sono sinistro, destro, completo o annidato outer join. outer join in cui i nomi di colonna nel **ON** clausola non ha lo stesso ordine i nomi di tabella corrispondente nella **OUTER JOIN** clausola; inner join in combinazione con outer join; e utilizzo di outer join qualsiasi operatore di confronto ODBC. Se il tipo di informazioni SQL_OJ_CAPABILITIES restituisce 0, non esiste una clausola outer join è supportata.
