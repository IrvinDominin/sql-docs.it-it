---
title: Istruzioni SQL immesse dall'utente | Documenti Microsoft
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
- user-entered SQL statements [ODBC]
- SQL statements [ODBC], constructing
- SQL statements [ODBC], entered by user
ms.assetid: 109af162-93ba-425a-8fe5-49c7dc7cc784
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0a6e8d81141c5bfbfe48a5fe234471ffe506f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sql-statements-entered-by-the-user"></a>Istruzioni SQL immesse dall'utente
Applicazioni che eseguono analisi ad hoc anche comunemente consentono all'utente di immettere istruzioni SQL direttamente. Ad esempio  
  
```  
SQLCHAR *     Statement, SqlState[6], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLSMALLINT   i, MsgLen;  
SQLINTEGER    NativeError;  
SQLRETURN     rc1, rc2;  
  
// Prompt user for SQL statement.  
GetSQLStatement(Statement);  
  
// Execute the statement directly. Because it will be executed only once,  
// do not prepare it.  
rc1 = SQLExecDirect(hstmt, Statement, SQL_NTS);  
  
// Process any errors or returned information.  
if ((rc1 == SQL_ERROR) || rc1 == SQL_SUCCESS_WITH_INFO) {  
   i = 1;  
   while ((rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
         Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState, NativeError, Msg, MsgLen);  
      i++;  
   }  
}  
```  
  
 Questo approccio semplifica la generazione di codice di applicazione; l'applicazione si basa sull'utente per compilare l'istruzione SQL e sull'origine dati per verificare la validità dell'istruzione. Poiché è difficile scrivere un'interfaccia utente grafica che adeguatamente espone gli aspetti complessi relativi a SQL, è sufficiente che chiede all'utente di immettere il testo dell'istruzione SQL può essere un'alternativa preferibile. Tuttavia, questo richiede all'utente di conoscere non solo SQL, ma anche lo schema dell'origine dati sottoposte a query. Alcune applicazioni forniscono un'interfaccia utente grafica mediante il quale l'utente può creare un'istruzione SQL di base e inoltre fornire un'interfaccia di testo con cui l'utente può modificarlo.
