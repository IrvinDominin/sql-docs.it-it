---
title: SQLGetData (driver di Database Desktop) | Documenti Microsoft
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
- SQLGetData function [ODBC], Desktop Database Drivers
ms.assetid: c9d9a32d-5dc2-4189-9bfb-2b008bc3d6a3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eab1073046f314de01b7542e3bd4d1efaea802ca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetdata-desktop-database-drivers"></a>SQLGetData (driver di Database Desktop)
Questa funzione è possibile recuperare dati da qualsiasi colonna, se sono presenti colonne associate, dopo di esso e indipendentemente dall'ordine in cui vengono recuperate le colonne.  
  
> [!NOTE]  
>  \*pcbValue in **SQLGetData** possono restituire due volte come numero di caratteri effettivamente disponibili durante l'associazione ai dati di ANSI più di 510 caratteri in un database Jet 4.0. Valori di tipo carattere o minore di 510 restituirà il cbValue effettivo.
