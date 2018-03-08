---
title: Tipi di dati di parametro | Documenti Microsoft
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
- data types [ODBC], parameters
- parameter data type [ODBC]
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: fd7e99d8-d26a-408c-9733-6ffccde99f75
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1deb0723864a0ed27f639a5060cc17afe886b9e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="parameter-data-types"></a>Tipi di dati di parametro
Anche se ogni parametro specificato con **SQLBindParameter** viene definito utilizzando un tipo di dati SQL, i parametri in un'istruzione SQL non sono intrinseci dati digitare. Di conseguenza, i marcatori di parametro possono essere inclusi in un'istruzione SQL solo se i tipi di dati possono essere dedotto da un altro operando nell'istruzione. Ad esempio, in un'espressione aritmetica, ad esempio? + COLUMN1, il tipo di dati del parametro può essere dedotto dal tipo di dati della colonna denominata rappresentato da COLUMN1. Se non è possibile determinare il tipo di dati, un'applicazione non è possibile utilizzare un marcatore di parametro.  
  
 La tabella seguente descrive come un tipo di dati viene determinato per diversi tipi di parametri, in conformità con SQL-92. Per una specifica più completa di inferenza il tipo di parametro quando si utilizzano altre clausole SQL, vedere la specifica di SQL-92.  
  
|Posizione del parametro|Si presuppone che il tipo di dati|  
|---------------------------|-----------------------|  
|Un operando di un operatore di confronto o aritmetici binario|Come l'altro operando|  
|Il primo operando in un **BETWEEN** clausola|Identico a quello del secondo operando|  
|Il secondo o terzo operando in un **BETWEEN** clausola|Il primo operando uguale|  
|Un'espressione utilizzata con **IN**|Uguale al primo valore o la colonna di risultati della sottoquery|  
|Valore utilizzato con **IN**|Diverso da quello dell'espressione o il primo valore nel caso di un marcatore di parametro nell'espressione|  
|Utilizzato con un valore di motivo **come**|VARCHAR|  
|Utilizzato con un valore di aggiornamento **aggiornare**|Stessi valori di aggiornamento|
