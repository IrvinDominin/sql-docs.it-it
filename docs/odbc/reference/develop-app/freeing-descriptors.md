---
title: Liberazione di descrittori | Documenti Microsoft
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
- SQLFreeHandle function [ODBC]
- descriptors [ODBC], allocating and freeing
- freeing descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 317213f4-0ebb-4bf8-a37a-4d6b1313823f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: db147faaae4ad0f2713e21f9e55228cbb2b057e7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="freeing-descriptors"></a>Descrittori di rilascio
Possono essere allocata in modo esplicito i descrittori di liberate in modo esplicito, chiamando **SQLFreeHandle** con *HandleType* di SQL_HANDLE_DESC o implicito, quando l'handle di connessione viene liberata. Quando viene liberato un descrittore allocato in modo esplicito, tutti gli handle di istruzione a cui il descrittore liberato applicato automaticamente di ripristinare i descrittori allocati in modo implicito per tali.  
  
 Descrittori allocati in modo implicito possono essere liberati chiamando solo **SQLDisconnect**, che elimina tutte le istruzioni o descrittori aprire per la connessione, oppure chiamando **SQLFreeHandle** con un  *HandleType* impostato su SQL_HANDLE_STMT per liberare un handle di istruzione e i descrittori allocati in modo implicito associati all'istruzione. Un descrittore allocato in modo implicito non può essere liberato chiamando **SQLFreeHandle** con un *HandleType* di SQL_HANDLE_DESC.  
  
 Anche quando liberato, rimane valido, un descrittore allocato in modo implicito e **SQLGetDescField** può essere chiamato nei campi.
