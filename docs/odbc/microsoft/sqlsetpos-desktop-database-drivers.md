---
title: SQLSetPos (driver di Database Desktop) | Documenti Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLSetPos function [ODBC], Desktop Database Drivers
ms.assetid: 8ef027ec-8512-48fe-8fe2-2ff7cd81e331
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dfeea1fe0ef6cbffd2090142e19df9a0f40afbf4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetpos-desktop-database-drivers"></a>SQLSetPos (driver di Database Desktop)
La semantica di blocco del modello per **SQLSetPos** chiama con il *irow* argomento uguale a 0 sono supportati.  
  
 SQL_LOCK_NO_CHANGE è supportato per *gruppo*. SQL_LOCK_EXCLUSIVE e SQL_LOCK_UNLOCK non sono supportati.  
  
 **SQLSetPos** supporta join aggiornabile. (Per ulteriori informazioni, vedere il *manuale del programmatore di Microsoft Jet Database Engine*.)
