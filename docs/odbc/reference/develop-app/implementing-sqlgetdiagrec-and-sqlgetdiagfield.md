---
title: Implementazione SQLGetDiagRec e SQLGetDiagField | Documenti Microsoft
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0cde15d468c3741db4230432ce5d56dbbe7ec31
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implementazione SQLGetDiagRec e SQLGetDiagField
**SQLGetDiagRec** e **SQLGetDiagField** implementate da Gestione Driver e tutti i driver. Gestione Driver ogni driver mantenere record di diagnostica per ogni ambiente, connessione, l'istruzione e handle di descrittore e liberare i record solo quando un'altra funzione viene chiamata con che handle o l'handle viene liberata.  
  
 Nonostante il responsabile di Driver e tutti i driver necessario determinare il primo record di stato in base alle classificazioni in [sequenza di record di stato](../../../odbc/reference/develop-app/sequence-of-status-records.md), gestione Driver determina la sequenza di record finale.  
  
 **SQLGetDiagRec** e **SQLGetDiagField** non registra i record di diagnostica su se stesse.  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Regole di gestione di diagnostica](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Ruolo di Gestione driver](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Ruolo del driver](../../../odbc/reference/develop-app/role-of-the-driver.md)
