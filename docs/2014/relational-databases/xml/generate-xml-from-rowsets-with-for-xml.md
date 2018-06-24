---
title: Generazione di XML da set di righe con FOR XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML clause, generating XML from rowsets
ms.assetid: d061c0f1-3de9-4ad1-bbca-ce45d064b6c8
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 163b33618f6d303d3ab08e078ee2b06096dc2ad8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36062816"
---
# <a name="generate-xml-from-rowsets-with-for-xml"></a>Generazione di XML da set di righe con FOR XML
  È possibile generare un `xml` istanza del tipo di dati da un set di righe utilizzando FOR XML con il nuovo **tipo** direttiva.  
  
 Il risultato può essere assegnato a un `xml` colonna, variabile o parametro del tipo di dati. L'istruzione FOR XML può essere inoltre nidificata, consentendo di creare qualsiasi tipo di struttura gerarchica. Le istruzioni FOR XML nidificate sono molto più facili da scrivere rispetto a FOR XML EXPLICIT, ma forniscono prestazioni inferiori in caso di gerarchie con numerosi livelli. L'istruzione FOR XML introduce inoltre una nuova modalità PATH, che specifica il percorso dell'albero XML in cui compare un determinato valore di colonna.  
  
 La nuova direttiva **FOR XML TYPE** consente di definire visualizzazioni XML in sola lettura su dati relazionali con la sintassi SQL. Su tale vista è possibile eseguire query utilizzando istruzioni SQL e istruzioni XQuery incorporate, come illustrato nell'esempio seguente. È possibile fare riferimento a tali viste SQL anche nelle stored procedure.  
  
## <a name="example-sql-view-returning-generated-xml-data-type"></a>Esempio: visualizzazione SQL che restituisce un tipo di dati xml generato  
 La definizione di vista SQL seguente crea una visualizzazione XML su una colonna relazionale, utilizzando la chiave primaria e gli autori dei libri recuperati da una colonna XML:  
  
```  
CREATE VIEW V (xmlVal) AS  
SELECT pk, xCol.query('/book/author')  
FROM   T  
FOR XML AUTO, TYPE  
```  
  
 La vista V contiene una singola riga con un singolo columnxmlVal di tipo XML`.` è possibile eseguire query come un normale `xml` istanza del tipo di dati. La query seguente, ad esempio, restituisce il nome dell'autore, "David":  
  
```  
SELECT xmlVal.query('//author[first-name = "David"]')  
FROM   V  
```  
  
 Le definizioni delle viste SQL sono analoghe alle visualizzazioni XML create utilizzando schemi con annotazioni, ma esistono alcune differenze importanti. La definizione della vista SQL è in modalità di sola lettura e deve essere modificata tramite istruzioni XQuery incorporate. Le viste XML vengono create utilizzando schemi con annotazioni. Inoltre, in una vista SQL il risultato XML viene materializzato prima di applicare l'espressione XQuery, mentre le query XPath sulle viste XML restituiscono query SQL sulle tabelle sottostanti.  
  
## <a name="see-also"></a>Vedere anche  
 [FOR XML &#40;SQL Server&#41;](for-xml-sql-server.md)  
  
  