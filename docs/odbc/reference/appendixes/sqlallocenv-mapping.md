---
title: Mapping SQLAllocEnv | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 75c17775183ba1bcb3164015679adf49a76f6828
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlallocenv-mapping"></a>Mapping di SQLAllocEnv
Quando un'applicazione chiama **SQLAllocEnv** tramite un'applicazione ODBC 3*x* driver, la chiamata a **SQLAllocEnv**(*phenv*) viene eseguito il mapping a **SQLAllocHandle** come indicato di seguito:  
  
1.  Gestione Driver alloca un handle di ambiente e lo restituisce all'applicazione. Le chiamate di gestione Driver **SQLSetEnvAttr** per impostare l'attributo di ambiente SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Quando l'applicazione consente di stabilire la prima connessione a un driver, Driver Manager chiama  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     nel driver con *OutputHandlePtr* impostato su *phenv*.
