---
title: Mapping SQLParamOptions | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLParamOptions
- SQLParamOptions function [ODBC], mapping
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8eef03c0fa72c123b5447a7067be42ec38699942
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlparamoptions-mapping"></a>Mapping SQLParamOptions
Quando un'applicazione chiama **SQLParamOptions** tramite un'applicazione ODBC 3*x* driver, la chiamata  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 verrà eseguito il mapping alle due chiamate di **SQLSetStmtAttr** come indicato di seguito:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```
