---
title: Numero di versione | Documenti Microsoft
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
- version number supported [ODBC]
- interoperability [ODBC], version number supported
ms.assetid: 6eccacdf-b837-4b66-bd48-ba31771acecb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b41b5c89818a5be57a129ef9739f115100f36f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="version-number"></a>Numero di versione
Esistono diverse versioni di ODBC, ognuna con diverse funzionalità. Un'applicazione determina quale versione ODBC Driver Manager e un driver specifico supportano chiamando **SQLGetInfo** con le opzioni SQL_ODBC_VER e SQL_DRIVER_ODBC_VER.
