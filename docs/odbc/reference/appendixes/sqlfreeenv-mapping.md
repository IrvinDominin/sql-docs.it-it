---
title: Mapping di SQLFreeEnv | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c1ab12a975d7b9c0aba77db9af31accac398a16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618989"
---
# <a name="sqlfreeenv-mapping"></a>Mapping di SQLFreeEnv
Quando un'applicazione chiama **SQLFreeEnv** tramite un'applicazione ODBC 3*x* driver, la chiamata a  
  
```  
SQLFreeEnv(henv)   
```  
  
 viene eseguito il mapping a  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 con il *gestiscono* impostata sul valore nell'argomento *henv*.
