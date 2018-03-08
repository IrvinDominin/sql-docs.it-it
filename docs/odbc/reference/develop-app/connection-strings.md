---
title: Le stringhe di connessione | Documenti Microsoft
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
- data sources [ODBC], connection functions
- connecting to driver [ODBC], connection strings
- functions [ODBC], data source or driver connections
- connection strings [ODBC], about connection strings
- connecting to data source [ODBC], connection strings
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: 724c7b86-300a-4fa9-ad96-4afa0fdcb3e9
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3abf812d73f780533a77a42498bfde4c299996d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connection-strings"></a>Stringhe di connessione
Una stringa di connessione contiene informazioni utilizzate per stabilire una connessione. Una stringa di connessione completa contiene tutte le informazioni necessarie per stabilire una connessione. La stringa di connessione è una serie di coppie parola chiave/valore separati da punti e virgola. (Per la sintassi completa di una stringa di connessione, vedere il [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) descrizione della funzione.) La stringa di connessione viene utilizzata da:  
  
-   **SQLDriverConnect**, che viene completata la stringa di connessione per l'interazione dell'utente.  
  
-   **SQLBrowseConnect**, che viene completata la stringa di connessione in modo iterativo con l'origine dati.  
  
 **SQLConnect** non utilizza una stringa di connessione; utilizzando **SQLConnect** è analoga alla connessione tramite una stringa di connessione con esattamente tre coppie parola chiave/valore (per nome dell'origine dati e, facoltativamente, l'utente ID e password) .
