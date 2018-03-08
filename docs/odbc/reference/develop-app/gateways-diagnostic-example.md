---
title: Esempio di diagnostica gateway | Documenti Microsoft
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
- diagnostic information [ODBC], examples
- gateway diagnostic [ODBC]
- error messages [ODBC], diagnostic messages
ms.assetid: e0695fac-4593-4b3d-8675-cb8f73dab966
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b14ef1e84b36a0f371f503706fca805c156f2e9d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="gateways-diagnostic-example"></a>Esempio di diagnostica di gateway
In un'architettura del gateway, un driver invia le richieste a un gateway che supporti ODBC. Il gateway invia le richieste a un sistema DBMS. Poiché si tratta del componente che si interfaccia con gestione Driver, il driver formati e restituisce gli argomenti per **SQLGetDiagRec**.  
  
 Ad esempio, se Oracle in base a Rdb un gateway Microsoft Open Data Services e se Rdb non è riuscito a trovare la tabella dipendente, il gateway potrebbe generare questo messaggio di diagnostica:  
  
```  
"[42S02][-1][DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not defined "  
   "in schema."  
```  
  
 Poiché si è verificato l'errore nell'origine dati, il gateway aggiunto un prefisso per l'identificatore dell'origine dati ([Rdb]) per il messaggio di diagnostica. Poiché il gateway è stato componente collegato con l'origine dati, aggiungerlo prefissi per il fornitore ([DEC]) e l'identificatore ([ODS Gateway]) per il messaggio di diagnostica. Inoltre aggiunto il valore SQLSTATE e il codice di errore Rdb all'inizio del messaggio di diagnostica. Questa operazione consentita per mantenere la semantica della propria struttura di messaggio e comunque fornire le informazioni di diagnostica per il driver ODBC. Il driver analizza le informazioni sull'errore associate all'istruzione error dal gateway.  
  
 Poiché il driver del gateway è il componente che si interfaccia con gestione Driver, viene utilizzato il precedente messaggio di diagnostica per formattare e restituire i valori seguenti dal **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1  
Diagnostic Msg:   "[DEC][ODS Gateway][Rdb]%SQL-F-RELNOTDEF, Table EMPLOYEE is not "  
                  "defined in schema."  
```
