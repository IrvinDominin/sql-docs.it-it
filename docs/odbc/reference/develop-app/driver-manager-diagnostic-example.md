---
title: Esempio di diagnostica di Gestione driver | Documenti Microsoft
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
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b8a63fc35dbedc1074f8fe713e8a87b207dad6c3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="driver-manager-diagnostic-example"></a>Esempio di diagnostica di Gestione driver
Gestione Driver è anche possibile generare messaggi di diagnostica. Ad esempio, se un'applicazione passata un'opzione di direzione non valida per **SQLDataSources**, gestione Driver potrebbe formattare e restituire i valori seguenti dal **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Si è verificato l'errore in Gestione Driver, aggiungere prefissi per il messaggio di diagnostica per il fornitore ([Microsoft]) e il relativo identificatore ([gestione Driver ODBC]).
