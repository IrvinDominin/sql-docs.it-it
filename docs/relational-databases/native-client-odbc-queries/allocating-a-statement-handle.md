---
title: Allocare un Handle di istruzione | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc701ff4419fdb60f2b954333aa2af7ec9845521
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="allocating-a-statement-handle"></a>Allocazione di un handle di istruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Prima che un'applicazione possa eseguire un'istruzione, deve allocare un handle di istruzione. A tale scopo, viene chiamata **SQLAllocHandle** con il *HandleType* parametro impostato su SQL_HANDLE_STMT e *InputHandle* che punta a un handle di connessione.  
  
 Gli attributi di istruzione sono caratteristiche dell'handle di istruzione. Attributi di istruzione di esempio possono includere l'utilizzo di segnalibri e il tipo di cursore da utilizzare con il set di risultati dell'istruzione. Gli attributi di istruzione sono impostati con [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md), e le relative impostazioni correnti vengono recuperate tramite [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md). Non vi è alcun requisito che stabilisce che un'applicazione debba impostare tutti gli attributi di istruzione. Per tutti gli attributi di istruzione sono disponibili valori predefiniti, alcuni dei quali specifici del driver.  
  
 Prestare particolare attenzione nell'utilizzare molte delle opzioni di istruzione e connessione ODBC. La chiamata [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) con *fOption* impostare ai controlli SQL_ATTR_LOGIN_TIMEOUT il tempo di attesa di un tentativo di connessione al timeout di un'applicazione durante l'attesa per stabilire una connessione (0 Specifica un'attesa infinita). Per i siti con tempi di risposta prolungati è possibile impostare un valore elevato per garantire che le connessioni dispongano di tempo sufficiente per il completamento. L'intervallo, tuttavia, deve essere sempre sufficientemente ridotto per consentire all'utente di ricevere una risposta entro un periodo di tempo ragionevole se il driver non è in grado di connettersi.  
  
 La chiamata **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_QUERY_TIMEOUT imposta un intervallo di timeout di query per proteggere il server e l'utente da query con esecuzione prolungata.  
  
 La chiamata **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_MAX_LENGTH limita la quantità di **testo** e **immagine** dati che un singola istruzione può recuperare. La chiamata **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_MAX_ROWS limita inoltre un set di righe al primo  *n*  righe se sono tutti l'applicazione richiede. Si noti che impostando SQL_ATTR_MAX_ROWS, il driver esegue un'istruzione SET ROWCOUNT nel server. Ciò influisce su tutti [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istruzioni, inclusi aggiornamenti e i trigger.  
  
 Utilizzare particolare attenzione quando si impostano queste opzioni. È preferibile che tutti gli handle di istruzione in un handle di connessione specifichino le stesse impostazioni per SQL_ATTR_MAX_LENGTH e SQL_ATTR_MAX_ROWS. Se il driver passa da un handle di istruzione a un altro con valori diversi per queste opzioni, il driver deve generare le istruzioni SET TEXTSIZE e SET ROWCOUNT appropriate per modificare le impostazioni. Il driver non può inserire queste istruzioni nello stesso batch dell'istruzione SQL dell'utente perché l'istruzione SQL dell'utente può contenere un'istruzione che deve essere la prima in un batch. Il driver deve inviare le istruzioni SET TEXTSIZE e SET ROWCOUNT in un batch distinto, che genera automaticamente un round trip aggiuntivo al server.  
  
## <a name="see-also"></a>Vedere anche  
 [L'esecuzione di query &#40; ODBC &#41;](../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
  
