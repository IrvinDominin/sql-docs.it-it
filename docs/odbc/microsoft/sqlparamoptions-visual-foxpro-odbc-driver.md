---
title: SQLParamOptions (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb73b760a0d63dcf1aa57ea0448dece6cb58b3f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Consente a un'applicazione specificare più valori per il set di parametri assegnato da [SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md). La possibilità di specificare più valori per un set di parametri è utile per gli inserimenti bulk e altre operazioni che richiedono l'origine dati per elaborare la stessa istruzione SQL più volte con diversi valori di parametro. Ad esempio, un'applicazione può specificare tre set di valori per il set di parametri associati un **inserire** istruzione e quindi eseguire il **inserire** istruzione una sola volta per eseguire le tre insert operazioni.  
  
 Per ulteriori informazioni, vedere [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md) nel *riferimento per programmatori ODBC*.
