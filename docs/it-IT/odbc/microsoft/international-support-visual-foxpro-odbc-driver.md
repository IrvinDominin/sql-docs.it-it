---
title: Supporto internazionale, Driver ODBC di Visual FoxPro | Documenti Microsoft
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
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd98a8ee7fe88ed30a9d909f7205989302f56cd6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>Supporto internazionale (Driver ODBC di Visual FoxPro)
Il Driver ODBC Microsoft Visual FoxPro supporta:  
  
-   Double-byte character set (DBCS)  
  
-   Più sequenze di confronto  
  
 Definisce una sequenza di confronto di *ordinamento* per i dati archiviati in un database o tabella di Visual FoxPro. Per impostazione predefinita, il driver è configurato per utilizzare le sequenze di confronto che supportano la lingua del sistema operativo.  
  
 Per un elenco di sequenze di confronto supportate, vedere [SET COLLATE](../../odbc/microsoft/set-collate-command.md).  
  
## <a name="locale"></a>impostazioni locali  
 Il set di informazioni che corrisponde a una determinata lingua e paese/area geografica. Impostazioni locali indica le impostazioni specifiche, ad esempio i separatori decimali, date e formati di ora e ordinamento dei caratteri.  
  
## <a name="sort-order"></a>ordinamento  
 Gli ordinamenti incorporano le regole di ordinamento di diverse *internazionali*s, che consente di ordinare correttamente i dati in tali lingue. In Visual FoxPro, dell'ordinamento corrente determina i risultati dei confronti di espressione di caratteri e l'ordine in cui i record visualizzati nella indicizzate o tabelle di ordinamento.
