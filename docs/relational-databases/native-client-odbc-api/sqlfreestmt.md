---
title: SQLFreeStmt | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFreeStmt function
ms.assetid: d9666d0b-3446-480e-bf1a-10b01213e411
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 56b902d8be50a1ce0a69c273d195659c3d835030
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfreestmt"></a>SQLFreeStmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  In genere   
      **SQLFreeStmt** non è consigliabile in ODBC 3.0 e versioni successive. Tuttavia se l'applicazione deve riutilizzare l'istruzione è comunque consigliabile utilizzare **SQLFreeStmt** con il **SQL_RESET_PARAMS** e **SQL_UNBIND** opzioni). È inoltre possibile utilizzare [SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md), [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md), [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md), [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md), e [ SQLFreeHandle](../../relational-databases/native-client-odbc-api/sqlfreehandle.md) per sostituiscono o duplicano la funzione di **SQLFreeStmt** e li dovrebbe usare invece.  
  
 In generale, è più efficiente riutilizzare le istruzioni di to eliminarli e allocarne di nuovi. Tuttavia in alcune situazioni, ad esempio il riutilizzo delle istruzioni, SQLFreeStmt deve essere utilizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [SQLFreeStmt-funzione](http://go.microsoft.com/fwlink/?LinkId=59346)   
 [Dettagli di implementazione di API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
