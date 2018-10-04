---
title: Più istruzioni attive e connessioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b2a1edbf9947aff01ef6d4688959352986cf672d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745719"
---
# <a name="multiple-active-statements-and-connections"></a>Istruzioni e connessioni attive multiple
Alcuni driver e DBMS limitano il numero di istruzioni e le connessioni che possono essere attive contemporaneamente. Questi numeri possono essere ridotte come uno. Per altre informazioni, vedere le opzioni SQL_MAX_CONCURRENT_ACTIVITIES e SQL_MAX_DRIVER_CONNECTIONS nel [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione, della funzione e [istruzione gestisce](../../../odbc/reference/develop-app/statement-handles.md) e [ Handle di connessione](../../../odbc/reference/develop-app/connection-handles.md).
