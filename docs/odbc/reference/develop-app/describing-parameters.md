---
title: Che descrive i parametri | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLBindParameter function [ODBC], describing parameters
ms.assetid: 118d0f47-2afd-4955-bb47-38b1e2c2f38f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f746b7df2ac3ef4de73e54c6d78df02e0c64ec34
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="describing-parameters"></a>Che descrive i parametri
**SQLBindParameter** dispone di argomenti che descrivono il parametro: il tipo SQL, precisione e scala. Il driver utilizza queste informazioni, o *metadati,* per convertire il valore del parametro nel tipo richiesto dall'origine dati. A prima vista, potrebbe sembrare che il driver è in una posizione migliore per conoscere i metadati dei parametri rispetto all'applicazione; Dopo tutto, il driver può individuare facilmente i metadati per un risultato di set di colonne. In realtà, ciò non avviene. In primo luogo, la maggior parte delle origini dati non forniscono un modo per il driver individuare i metadati del parametro. In secondo luogo, la maggior parte delle applicazioni conoscono già i metadati.  
  
 Se un'istruzione SQL è hardcoded nell'applicazione, il writer dell'applicazione conosce già il tipo di ogni parametro. Se viene costruita un'istruzione SQL dall'applicazione in fase di esecuzione, l'applicazione può determinare i metadati durante la compilazione dell'istruzione. Ad esempio, quando l'applicazione crea la clausola  
  
```  
WHERE OrderID = ?  
```  
  
 è possibile chiamare **SQLColumns** per la colonna OrderID.  
  
 L'unico caso in cui l'applicazione non è facile determinare i metadati dei parametri è quando l'utente immette un'istruzione con parametri. In questo caso, l'applicazione chiama **SQLPrepare** per preparare l'istruzione, **SQLNumParams** per determinare il numero di parametri, e **SQLDescribeParam** per descrivere ogni parametro. Tuttavia, come indicato in precedenza, la maggior parte delle origini dati non forniscono un modo per individuare i metadati del parametro, pertanto il driver **SQLDescribeParam** è ampiamente supportato.
