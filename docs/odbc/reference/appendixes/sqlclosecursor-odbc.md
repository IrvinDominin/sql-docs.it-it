---
title: SQLCloseCursor_ODBC | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLCloseCursor function [ODBC], ODBC
ms.assetid: 5e47e3f7-e1b8-451f-bf75-daa19b7c7271
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fcc680ec815afa700c00c9d8a69c5826944153a4
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="sqlclosecursorodbc"></a>SQLCloseCursor_ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 In questo argomento viene illustrato l'utilizzo del **SQLCloseCursor** funzione nella libreria di cursori. Per informazioni generali su **SQLCloseCursor**, vedere [funzione SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md).  
  
 La libreria di cursori non supporta la chiamata **SQLCloseCursor** senza un cursore aperto. Questo tentativo restituisce SQLSTATE 24000 (stato del cursore non valido). La chiamata **SQLFreeStmt** con un *opzione* di SQL_CLOSE quando nessun cursore è aperto è supportato dalla libreria di cursori.