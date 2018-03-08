---
title: Connessione con SQLDriverConnect | Documenti Microsoft
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
- functions [ODBC], data source or driver connections
- connecting to data source [ODBC], SQLDriverConnect
- connecting to driver [ODBC], SQLDriverConnect
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], functions
- SQLDriverConnect function [ODBC], connecting
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: e46e959f-d3c5-4ddb-810a-107bfcb83fd2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d9f6177b384da8866c8140cc30f1d32bca0bb635
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connecting-with-sqldriverconnect"></a>Connessione con SQLDriverConnect
**SQLDriverConnect** viene utilizzato per connettersi a un'origine dati utilizzando una stringa di connessione. **SQLDriverConnect** viene usata invece di **SQLConnect** per i motivi seguenti:  
  
-   Per consentire l'applicazione di utilizzare le informazioni di connessione specifici del driver.  
  
-   Per specificare che il driver deve richiedere all'utente le informazioni di connessione.  
  
-   Per connettersi senza specificare un'origine dati.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Informazioni di connessione specifiche del driver](../../../odbc/reference/develop-app/driver-specific-connection-information.md)  
  
-   [Chiedere all'utente informazioni di connessione](../../../odbc/reference/develop-app/prompting-the-user-for-connection-information.md)  
  
-   [Connessione tramite origini dati dei file](../../../odbc/reference/develop-app/connecting-using-file-data-sources.md)  
  
-   [Connessione diretta ai driver](../../../odbc/reference/develop-app/connecting-directly-to-drivers.md)
