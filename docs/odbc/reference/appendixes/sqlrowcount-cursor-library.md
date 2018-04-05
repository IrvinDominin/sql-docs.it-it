---
title: SQLRowCount (libreria di cursori) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 868f7e45a6f10ce6aa76e84117c5c605c6321d89
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLRowCount** funzione nella libreria di cursori. Per informazioni generali su **SQLRowCount**, vedere [SQLRowCount-funzione](../../../odbc/reference/syntax/sqlrowcount-function.md).  
  
 Quando un'applicazione chiama **SQLRowCount** con l'istruzione associata con il cursore, la libreria di cursori restituisce il numero di righe di dati che sono recuperati dal driver.  
  
 Quando un'applicazione chiama **SQLRowCount** con l'istruzione associata a un'istruzione delete o un aggiornamento posizionato, la libreria di cursori restituisce il numero di righe interessate dall'istruzione.  
  
 Quando un'applicazione chiama **SQLRowCount** dopo un **selezionare** istruzione, la libreria di cursori restituisce – 1.
