---
title: Mapping di SQLTransact | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5cf669883ce81528adbe1fbd8faeff2ed716218
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656177"
---
# <a name="sqltransact-mapping"></a>Mapping di SQLTransact
**SQLTransact** è stata sostituita dal **SQLEndTran**. La differenza principale tra le due funzioni è che **SQLEndTran** contiene un argomento *HandleType*, che consente di specificare l'ambito delle operazioni da eseguire. Il *HandleType* argomento può specificare l'ambiente o l'handle di connessione. La chiamata seguente a **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 viene eseguito il mapping a  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* non è uguale a SQL_NULL_HDBC. Il *ConnectionHandle* è impostato sul valore di argomento *hdbc*.  
  
 **SQL_Transact** viene mappato a  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Se *ConnectionHandle* è uguale a SQL_NULL_HDBC. Il *EnvironmentHandle* è impostato sul valore di argomento *henv*.  
  
 In entrambi i casi precedenti, il *CompletionType* argomento è impostato sullo stesso valore di *fType*.
