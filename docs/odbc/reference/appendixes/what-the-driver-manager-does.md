---
title: Quali la gestione di Driver non | Documenti Microsoft
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
- driver manager [ODBC], backward compatibility
- compatibility [ODBC], driver manager
- ODBC driver manager [ODBC]
- backward compatibility [ODBC], driver manager
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a4d94cc3308964a97e5355de0f68306dcd375058
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="what-the-driver-manager-does"></a>Funzionamento di gestione Driver
Nella tabella seguente sono riepilogati come ODBC 3*x* gestione Driver mapping delle chiamate a ODBC 2. *x* mentre ODBC 3*x* driver.  
  
|Funzione o<br /><br /> attributo di istruzione|Commenti|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Punta al segnalibro da utilizzare con **SQLFetchScroll**. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione configura questa impostazione in un ODBC 2. *x* driver ODBC 3*x* gestione Driver memorizza nella cache. Dereferenzia il puntatore e passa il valore per ODBC 2. *x* driver il *FetchOffset* argomento di **SQLExtendedFetch** quando **SQLFetchScroll** viene chiamato in un secondo momento dall'applicazione.<br />-Quando un'applicazione imposta in un'applicazione ODBC 3*x* driver ODBC 3*x* gestione Driver passa la chiamata al driver.|  
|VENGONO IMPOSTATI SQL_ATTR_ROW_STATUS_PTR|Punti nella matrice di stato di riga vengono immesse **SQLFetch**, **SQLFetchScroll**, **SQLBulkOperations**, e **SQLSetPos**. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione configura questa impostazione in un ODBC 2. *x* driver ODBC 3*x* gestione Driver memorizza nella cache il relativo valore. Passa il valore di ODBC 2. *x* driver il *RowStatusArray* argomento di **SQLExtendedFetch** quando **SQLFetchScroll** o **SQLFetch** viene chiamato.<br />-Quando un'applicazione imposta in un'applicazione ODBC 3*x* driver ODBC 3*x* gestione Driver passa la chiamata al driver.<br />-Nello stato S6, se un'applicazione imposta SQL_ATTR_ROW_STATUS_PTR e quindi chiama **SQLBulkOperations** (con un *operazione* di SQL_ADD) o **SQLSetPos** senza prima chiamare **SQLFetch** o **SQLFetchScroll**, SQLSTATE HY011 (Impossibile impostare l'attributo ora) viene restituito.|  
|SQL_ATTR_ROWS_FETCHED_PTR|Punta al buffer in cui **SQLFetch** e **SQLFetchScroll** restituire il numero di righe recuperate. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione configura questa impostazione in un ODBC 2. *x* driver ODBC 3*x* gestione Driver memorizza nella cache il relativo valore. Passa il valore di ODBC 2. *x* driver il *RowCountPtr* argomento di **SQLExtendedFetch** quando **SQLFetch** o **SQLFetchScroll** viene chiamato dall'applicazione.<br />-Quando un'applicazione imposta in un'applicazione ODBC 3*x* driver ODBC 3*x* gestione Driver passa la chiamata al driver.|  
|SQL_ATTR_ROW_ARRAY_SIZE|Imposta le dimensioni del set di righe. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione configura questa impostazione in un ODBC 2. *x* driver ODBC 3*x* Driver Manager esegue il mapping all'attributo di istruzione SQL_ROWSET_SIZE.<br />-Quando un'applicazione imposta in un'applicazione ODBC 3*x* driver ODBC 3*x* gestione Driver passa la chiamata al driver.<br />-Quando un'applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLSetScrollOptions**, SQL_ROWSET_SIZE è impostata sul valore di *RowsetSize* argomento se sottostante il driver non supporta **SQLSetScrollOptions**.|  
|SQL_ROWSET_SIZE|Imposta le dimensioni del set di righe utilizzate da **SQLExtendedFetch** quando **SQLExtendedFetch** viene chiamato da un'API ODBC 2*x* dell'applicazione. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione imposta, ODBC 3*x* gestione Driver passa la chiamata al driver, indipendentemente dalla versione del driver.<br />-Quando un'applicazione che utilizza un ODBC 2. *x* driver chiama **SQLSetScrollOptions**, SQL_ROWSET_SIZE è impostata sul valore di **RowsetSize** argomento.|  
|**SQLBulkOperations**|Esegue un inserimento, operazione o update, delete o recupero da operazioni di segnalibro. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione chiama **SQLBulkOperations** con un *operazione* di SQL_ADD in un'API ODBC 2. *x* driver ODBC 3*x* Driver Manager esegue il mapping a **SQLSetPos** con un *operazione* di SQL_ADD.<br />-Quando si lavora con un ODBC 2. *x* driver che non supporta **SQLSetPos** con un *operazione* di SQL_ADD, ODBC 3*x* gestione Driver non esegue il mapping **SQLSetPos** con un *operazione* di SQL_ADD a **SQLBulkOperations** con un *operazione* di SQL_ADD. In questo modo **SQLBulkOperations** non può essere chiamato in stato S7, quali in 2 di ODBC. *x* è l'unico stato in cui **SQLSetPos** potrebbe essere chiamato.<br />-Se l'applicazione chiama **SQLBulkOperations** con un *operazione* di SQL_ADD in un'API ODBC 2. *x* driver prima di chiamare **SQLFetchScroll**, ODBC 3*x* gestione Driver restituisce un errore.|  
|**SQLExtendedFetch.**|Restituisce il set di righe specificato. Ad eccezione di restrizione appena indicata, ODBC 3*x* gestione Driver passa le chiamate a **SQLExtendedFetch** al driver, indipendentemente dalla versione del driver.|  
|**SQLFetch**|Restituisce il set di righe successivo. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione chiama **SQLFetch** in un'API ODBC 2. *x* driver ODBC 3*x* Driver Manager esegue il mapping a **SQLExtendedFetch**. Il *FetchOrientation* argomento di **SQLExtendedFetch** è impostato su SQL_FETCH_NEXT. Gestione Driver utilizza il valore memorizzato nella cache dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR il *RowStatusArray* argomento e il valore memorizzato nella cache dell'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione per il  *RowCountPtr* argomento.<br />-Un'applicazione ODBC 3*x* applicazione è possibile combinare le chiamate a **SQLFetch** e **SQLFetchScroll** in un'API ODBC 2. *x* driver perché ODBC 3*x* esegue il mapping di gestione Driver **SQLFetch** a **SQLExtendedFetch** quando un'applicazione viene chiamata in un ODBC 2. *x* driver.<br />-Se un ODBC 2. *x* driver non supporta **SQLExtendedFetch**, ODBC 3*x* gestione Driver non esegue il mapping **SQLFetch** o  **SQLFetchScroll** a **SQLExtendedFetch** quando un'applicazione chiama in tale driver. Se l'applicazione tenta di impostare SQL_ATTR_ROW_ARRAY_SIZE su un valore maggiore di 1, HYC00 SQLSTATE (funzionalità facoltativa non implementata) viene restituito.<br />-Tranne che per le restrizioni appena indicate, ODBC 3*x* gestione Driver passa le chiamate a **SQLFetch** al driver, indipendentemente dalla versione del driver.|  
|**SQLFetchScroll**|Restituisce il set di righe specificato. Di seguito sono indicati i dettagli di implementazione:<br /><br /> -Quando un'applicazione chiama **SQLFetchScroll** in un'API ODBC 2. *x* driver ODBC 3*x* Driver Manager esegue il mapping a **SQLExtendedFetch**. Viene utilizzato il valore dell'attributo di istruzione vengono impostati SQL_ATTR_ROW_STATUS_PTR memorizzati nella cache il *RowStatusArray* argomento e il valore memorizzato nella cache dell'attributo SQL_ATTR_ROWS_FETCHED_PTR istruzione per il *RowCountPtr* argomento. Se il *FetchOrientation* argomento **SQLFetchScroll** è impostato su SQL_FETCH_BOOKMARK, viene utilizzato il valore dell'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR memorizzati nella cache il *FetchOffset*  argomento e restituisce un errore se il *FetchOffset* argomento di **SQLFetchScroll** è non da 0.<br />-Quando un'applicazione chiama questo in un'applicazione ODBC 3*x* driver ODBC 3*x* gestione Driver passa la chiamata al driver.|  
|**SQLSetPos**|Esegue diverse operazioni posizionate. ODBC 3*x* gestione Driver passa le chiamate a **SQLSetPos** al driver, indipendentemente dalla versione del driver.|  
|**SQLSetScrollOptions**|Quando esegue il mapping di gestione Driver **SQLSetScrollOptions** per un'applicazione che utilizza un'applicazione ODBC 3*x* driver che non supporta **SQLSetScrollOptions**, il Driver Manager imposta l'opzione dell'istruzione SQL_ROWSET_SIZE, non l'attributo di istruzione SQL_ATTR_ROW_ARRAY_SIZE sul *RowsetSize* argomento **SQLSetScrollOption**. Di conseguenza, **SQLSetScrollOptions** non può essere utilizzato da un'applicazione durante il recupero di più righe da una chiamata a **SQLFetch** o **SQLFetchScroll**. E può essere utilizzato solo quando più recupero righe da una chiamata a **SQLExtendedFetch**.|
