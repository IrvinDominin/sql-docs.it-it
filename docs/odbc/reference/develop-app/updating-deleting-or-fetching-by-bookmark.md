---
title: L'aggiornamento, eliminazione o recupero dal segnalibro | Documenti Microsoft
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
- updating by bookmarks [ODBC]
- result sets [ODBC], bookmarks
- fetches [ODBC], by bookmarks [ODBC]
- deleting by bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: e2ee58d7-c28f-435f-b537-06207215dd2f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 520d33c12b88fd6cd1c03cd7fd64ec254662ae3d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="updating-deleting-or-fetching-by-bookmark"></a>L'aggiornamento, eliminazione o recupero dal segnalibro
Segnalibri possono essere utilizzati per identificare i dati da aggiornare nel set di risultati, eliminato dal risultato impostata o recuperata dal set di risultati come buffer di set di righe. Queste operazioni vengono eseguite da una chiamata a **SQLBulkOperations** con un *opzione* argomento SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK o SQL_FETCH_BY_BOOKMARK. I segnalibri utilizzati in queste operazioni vengono archiviati nella colonna 0 dei buffer di set di righe. Durante l'aggiornamento dal segnalibro, vengono aggiornati i dati che generano un set di colonne a cui viene recuperato dai buffer di set di righe. Per ulteriori informazioni, vedere [aggiornamento dei dati con SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md).
