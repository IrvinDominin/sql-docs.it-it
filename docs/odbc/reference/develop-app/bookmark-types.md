---
title: Segnalibro tipi | Documenti Microsoft
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
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06f720d61ae8be7b1a2c98ce2c749a4265e630d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="bookmark-types"></a>Tipi di segnalibro
Tutti i segnalibri in ODBC 3*x* sono segnalibri a lunghezza variabile. In questo modo una chiave primaria o un indice univoco associato a una tabella per essere utilizzata come segnalibro. Il segnalibro inoltre può essere un valore a 32 bit, utilizzato in ODBC 2. *x*. Per specificare che un segnalibro viene utilizzato con un cursore, un'applicazione ODBC 3*x* applicazione imposta l'attributo di istruzione SQL_ATTR_USE_BOOKMARK SQL_UB_VARIABLE. Viene usato automaticamente un segnalibro a lunghezza variabile.  
  
 Un'applicazione può chiamare **SQLColAttribute** con il *FieldIdentifier* argomento impostato su SQL_DESC_OCTET_LENGTH per ottenere la lunghezza del segnalibro. Poiché un segnalibro a lunghezza variabile può essere un valore long, un'applicazione non deve essere associato alla colonna 0 a meno che non utilizza il segnalibro per numero di righe nel set di righe.  
  
 I segnalibri di lunghezza fissa sono supportati solo per compatibilità con le versioni precedenti. Se un ODBC 2. *x* applicazione che utilizza un'applicazione ODBC 3*x* driver chiama **SQLSetStmtOption** per impostare SQL_USE_BOOKMARKS SQL_UB_ON, questo viene mappato a SQL_UB_VARIABLE in Gestione Driver . Viene utilizzato un segnalibro a lunghezza variabile, anche se vengono popolate solo 32 bit di esso. Se un driver supporta segnalibri a lunghezza fissa, saranno supportate segnalibri a lunghezza variabile. Se un'applicazione ODBC 3*x* applicazione che utilizza un ODBC 2. *x* driver chiama **SQLSetStmtAttr** per impostare SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE, questo viene mappato in Gestione Driver per SQL_UB_ON e viene utilizzato un segnalibro di 32 bit a lunghezza fissa. Quindi, l'attributo di istruzione SQL_ATTR_FETCH_BOOKMARK_PTR deve puntare a un segnalibro a 32 bit. Se i segnalibri utilizzati sono più di 32 bit, ad esempio quando le chiavi primarie vengono utilizzate come segnalibri, il cursore è necessario mappare i valori effettivi a valori a 32 bit. La stato, compilazione, ad esempio, una tabella hash di essi. Quando un'applicazione ODBC 3*x* applicazione che utilizza un ODBC 2. *x* driver associa un segnalibro, la lunghezza del buffer deve essere 4.
