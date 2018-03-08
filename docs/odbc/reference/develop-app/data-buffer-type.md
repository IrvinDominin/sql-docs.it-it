---
title: Tipo di Buffer di dati | Documenti Microsoft
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
- data types [ODBC], buffers
- data buffers [ODBC], types
- buffers [ODBC], data
- C data types [ODBC], buffers
ms.assetid: 58bea3e9-d552-447f-b3ad-ce1dab213b72
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6b37e2294a22eadffad1302452d74b72a94891f5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="data-buffer-type"></a>Tipo di Buffer di dati
Il tipo di dati C di un buffer specificato dall'applicazione. Con una singola variabile, questo errore si verifica quando l'applicazione alloca la variabile. Con generici per la memoria, vale a dire memoria a cui fa riferimento un puntatore di tipo void, questo errore si verifica quando l'applicazione esegue il cast della memoria per un particolare tipo. Il driver individua questo tipo in due modi:  
  
-   **Argomento di tipo di dati del buffer.** Usata per trasferire i valori dei parametri e dati di set di risultati, ad esempio il buffer associato al buffer *TargetValuePtr* in **SQLBindCol**, in genere presente un argomento di tipo associato, ad esempio il  *TargetType* argomento **SQLBindCol**. In questo argomento, l'applicazione passa l'identificatore di tipo C che corrisponde al tipo di buffer. Ad esempio, nella chiamata seguente a **SQLBindCol**, il valore SQL_C_TYPE_DATE indica al driver di *data* buffer è un valore SQL_DATE_STRUCT:  
  
    ```  
    SQL_DATE_STRUCT Date;  
    SQLINTEGER  DateInd;  
    SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &Date, 0, &DateInd);  
    ```  
  
     Per ulteriori informazioni sugli identificatori di tipo, vedere il [tipi di dati ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md) sezione più avanti in questa sezione.  
  
-   **Tipo predefinito.** Buffer utilizzato per inviare e recuperare le opzioni o attributi, ad esempio il buffer a cui fa riferimento il *InfoValuePtr* argomento **SQLGetInfo**, includere un tipo predefinito dipende dall'opzione specificata. Il driver presuppone che il buffer dei dati di questo tipo. è responsabilità dell'applicazione per allocare un buffer di questo tipo. Ad esempio, nella chiamata seguente a **SQLGetInfo**, il driver presuppone che il buffer è un intero a 32 bit perché questo è ciò che l'opzione SQL_STRING_FUNCTIONS richiede:  
  
    ```  
    SQLUINTEGER StringFuncs;  
    SQLGetInfo(hdbc, SQL_STRING_FUNCTIONS, (SQLPOINTER) &StringFuncs, 0,  
                NULL);  
    ```  
  
 Il driver utilizza il tipo di dati C per interpretare i dati nel buffer.
