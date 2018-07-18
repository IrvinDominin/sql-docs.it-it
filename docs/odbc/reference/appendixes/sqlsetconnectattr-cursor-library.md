---
title: La funzione SQLSetConnectAttr (libreria di cursori) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d10356488b0a590fb065c49a36a05f0e9b976991
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectattr-cursor-library"></a>Funzione SQLSetConnectAttr (libreria di cursori)
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLSetConnectAttr** funzione nella libreria di cursori. Per informazioni generali su **SQLSetConnectAttr**, vedere [funzione SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
 Un'applicazione chiama **SQLSetConnectAttr** con l'attributo SQL_ATTR_ODBC_CURSORS per specificare se la libreria di cursori viene sempre utilizzata, utilizzata se il driver non supporta i cursori scorrevoli o mai utilizzata. La libreria di cursori si presuppone che un driver supporta i cursori scorrevoli se restituisce SQL_CA1_RELATIVE per il tipo di informazioni SQL_STATIC_CURSOR_ATTRIBUTES1 in **SQLGetInfo**.  
  
 L'applicazione deve chiamare **SQLSetConnectAttr** per specificare l'utilizzo della libreria di cursori dopo aver chiamato **SQLAllocHandle** con un *HandleType* impostato su SQL_HANDLE_DBC per allocare la connessione e prima che si connetta all'origine dati. Se un'applicazione chiama **SQLSetConnectAttr** con l'attributo SQL_ATTR_ODBC_CURSORS durante la connessione è ancora attiva, la libreria di cursori restituisce un errore.  
  
 Per impostare un attributo di istruzione supportato dalla libreria di cursori per tutte le istruzioni associata a una connessione, un'applicazione deve chiamare **SQLSetConnectAttr** per l'attributo dopo la connessione all'origine dati e prima dell'istruzione Apre il cursore. Se un'applicazione chiama **SQLSetConnectAttr** con un'istruzione attributo e un cursore è aperto in un'istruzione associata alla connessione, l'attributo di istruzione non essere applicato a tale istruzione fino a quando il cursore è chiuso e riaperto.
