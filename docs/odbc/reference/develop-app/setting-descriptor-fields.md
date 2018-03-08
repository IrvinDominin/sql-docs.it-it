---
title: L'impostazione di campi di descrizione | Documenti Microsoft
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
helpviewer_keywords: descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fc02690bd62802f9d356851cd85522328107a707
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setting-descriptor-fields"></a>L'impostazione di campi di descrizione
Per modificare i campi di un descrittore, un'applicazione può chiamare **SQLSetDescField**. Alcuni campi sono di sola lettura e non possono essere impostate. (Vedere il [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) descrizione della funzione.)  
  
 I campi del record del descrittore sono impostati con un numero di record (*RecNumber*) di 1 o versione successiva, mentre i campi di intestazione di descrizione vengono impostati con un numero di record di 0. Un numero di record pari a 0 viene anche utilizzato per impostare i campi di segnalibro, in base alla convenzione che i segnalibri sono contenuti nella colonna 0. Questo potrebbe rendere l'impressione che sono contenuti i campi di segnalibro all'interno dell'intestazione del descrittore, ma questo non avviene. Segnalibro campi sono diversi dai campi di intestazione.  
  
 Quando l'impostazione dei singoli campi, l'applicazione deve seguire la sequenza definita [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). L'impostazione di alcuni campi, il driver impostare altri campi. Ciò garantisce che il descrittore sia sempre pronto per l'uso dopo l'applicazione è specificato un tipo di dati. Quando l'applicazione imposta il campo SQL_DESC_TYPE, il driver verifica che i campi che specificano il tipo siano validi e coerenti.  
  
 Se una chiamata di funzione che è possibile impostare un campo di descrizione non riesce, il contenuto del campo del descrittore è definito dopo la chiamata di funzione non riuscita.
