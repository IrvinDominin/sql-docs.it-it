---
title: Moduli SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL modules [ODBC]
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], modules
- modules [ODBC]
- SQL statements [ODBC], modules
ms.assetid: 07551472-87ee-4765-951f-1364ed32f0c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30c116878049c4f6a8f36e988731ab641e03c6d7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47834749"
---
# <a name="sql-modules"></a>Moduli SQL
La seconda tecnica per l'invio di istruzioni SQL per il sistema DBMS è tramite moduli. In breve, un modulo è costituito da un gruppo di procedure che vengono chiamati dall'host di linguaggio di programmazione. Ogni routine contiene un'unica istruzione SQL e dati vengono passati da e verso la procedura con parametri.  
  
 Un modulo può essere considerato come una libreria di oggetti che è collegata al codice dell'applicazione. Tuttavia, esattamente come le procedure e il resto dell'applicazione sono collegati è dipendente dall'implementazione. Ad esempio, le procedure potrebbero essere compilate in codice oggetto e collegate direttamente al codice dell'applicazione, può essere compilati e archiviati nel DBMS e le chiamate a identificatori piano inseriti nel codice dell'applicazione di accesso o potrebbe essere interpretati in fase di esecuzione.  
  
 Il vantaggio principale dei moduli è che consentono di separare chiaramente istruzioni SQL dal linguaggio di programmazione. In teoria, dovrebbe essere possibile modificare senza modificare l'altro e semplicemente ricollegate.
