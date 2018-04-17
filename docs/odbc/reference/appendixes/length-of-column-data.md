---
title: Lunghezza dei dati di colonna | Documenti Microsoft
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
- column data [ODBC]
- length of column data [ODBC]
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: c762c881-ebe0-4eac-84d5-f30281fc3eca
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a15ef8d9b58386dbd2000d23f4f762f13b368c30
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="length-of-column-data"></a>Lunghezza dei dati di colonna
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 La libreria di cursori consente di creare un buffer nella cache per ogni buffer di lunghezza/indicatore associato al set di risultati con **SQLBindCol**. Utilizza i valori in questi buffer per costruire un **dove** clausola quando emula per gli aggiornamenti posizionati o eliminare le istruzioni. Aggiorna i buffer dai buffer di set di righe durante il recupero dei dati dall'origine dei dati e quando esegue le istruzioni per gli aggiornamenti posizionati.  
  
 Se il tipo C di un buffer di dati è SQL_C_CHAR o SQL_C_BINARY e il valore di lunghezza/indicatore è SQL_NTS, la lunghezza della stringa di dati viene inserita nel buffer di lunghezza/indicatore.  
  
> [!NOTE]  
>  La libreria di cursori non aggiorna la cache per una colonna se **StrLen_or_IndPtr* nel set di righe corrispondente buffer è SQL_DATA_AT_EXEC o il risultato della macro SQL_LEN_DATA_AT_EXEC.
