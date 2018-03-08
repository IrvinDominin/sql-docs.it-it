---
title: 'Passaggio 6: Disconnettersi dall''origine dati | Documenti Microsoft'
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
- application process [ODBC], disconnecting from data source
- data sources [ODBC], disconnecting
- disconnecting from data source [ODBC]
ms.assetid: 6ad759ba-4721-4d8f-9b26-de976d4fc1a0
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d76d3b3061dded62c7230e4a8d02a4312c8152f9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="step-6-disconnect-from-the-data-source"></a>Passaggio 6: Disconnettersi dall'origine dati
Il passaggio finale consiste nel disconnettere dall'origine dati, come illustrato nella figura seguente. In primo luogo, l'applicazione rilascia tutti gli handle di istruzione chiamando **SQLFreeHandle**. Per ulteriori informazioni, vedere [liberare l'Handle di istruzione](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md).  
  
 ![Mostra la disconnessione da un'origine dati](../../../odbc/reference/develop-app/media/pr17.gif "pr17")  
  
 Successivamente, l'applicazione si disconnette dall'origine dati con **SQLDisconnect** e rilascia l'handle di connessione con **SQLFreeHandle**. Per ulteriori informazioni, vedere [disconnessione da un'origine dati o il Driver](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md).  
  
 Infine, l'applicazione rilascia l'handle di ambiente con **SQLFreeHandle** e scaricato da Gestione Driver. Per ulteriori informazioni, vedere [allocare l'Handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).
