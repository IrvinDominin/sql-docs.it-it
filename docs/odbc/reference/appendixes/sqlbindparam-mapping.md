---
title: Mapping SQLBindParam | Documenti Microsoft
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
- SQLBindparam function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLBindParam
ms.assetid: 375f8f24-36de-4946-916e-c75abc6f070d
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c2ca8ae4b0b7b522259677b252e2b0d24d14b5d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlbindparam-mapping"></a>Mapping di SQLBindParam
**SQLBindParam** non può essere realmente chiamato deprecato perché non era presente in ODBC; tuttavia, ancora rappresenta funzionalità duplicate, gestione Driver deve essere esportato perché ISO e aprire compatibile con gruppo di applicazioni verranno utilizzato. Poiché **SQLBindParameter** contiene tutte le funzionalità di **SQLBindParam**, **SQLBindParam** verrà eseguito il mapping in cima **SQLBindParameter** (quando il driver sottostante è un'applicazione ODBC 3*x* driver). Un'applicazione ODBC 3*x* driver non è necessario implementare **SQLBindParam**.  
  
## <a name="remarks"></a>Osservazioni  
 Quando la chiamata seguente a **SQLBindParam** diventa:  
  
```  
SQLBindParam(   StatementHandle,    ParameterNumber,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    StrLen_or_IndPtr)  
```  
  
 le chiamate di gestione Driver **SQLBindParameter** nel driver come indicato di seguito:  
  
```  
SQLBindParameter(   StatementHandle,    ParameterNumber,    SQL_PARAM_INPUT,    ValueType,    ParameterType,    ColumnSize,    DecimalDigits,    ParameterValuePtr,    BufferLength,    StrLen_or_IndPtr)  
```  
  
 Vedere [informazioni ODBC a 64 Bit](../../../odbc/reference/odbc-64-bit-information.md), se l'applicazione verrà eseguita in un sistema operativo a 64 bit.  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di funzioni deprecate](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)
