---
title: SQLGetData (driver di Database Desktop) | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cdf875d594d84143ec45afca22805e533837c676
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (driver di Database Desktop)
Questa funzione è possibile recuperare dati da qualsiasi colonna, se sono presenti colonne associate, dopo di esso e indipendentemente dall'ordine in cui vengono recuperate le colonne.  
  
> [!NOTE]  
>  \*pcbValue in **SQLGetData** può restituire due volte come numero di caratteri effettivamente disponibili durante l'associazione a dati ANSI più di 510 caratteri in un database Jet 4.0. Valori di tipo carattere o minore di 510 restituirà il cbValue effettivo.
