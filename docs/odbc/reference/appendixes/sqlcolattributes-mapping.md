---
title: Mapping SQLColAttributes | Documenti Microsoft
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
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6cae6f9aebff24efde3b198c887bd9b769704bf9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcolattributes-mapping"></a>Mapping di SQLColAttributes
Quando un'applicazione chiama **SQLColAttributes** tramite un'applicazione ODBC 3*x* driver, la chiamata a **SQLColAttributes** viene eseguito il mapping a **SQLColAttribute** come indicato di seguito:  
  
> [!NOTE]  
>  Il prefisso utilizzato *FieldIdentifier* valori in ODBC 3*x* è stato modificato da tali utilizzati in ODBC 2. *x*. Il prefisso è "SQL_DESC"; il prefisso precedente era "SQL_COLUMN".  
  
1.  Se l'applicazione è un'API ODBC 2. *x* applicazione *fDescType* è SQL_COLUMN_TYPE e il tipo restituito è un tipo DATETIME conciso, le mappe di gestione Driver la restituzione di valori per i codici di date, time e timestamp.  
  
2.  Se *fDescType* è SQL_COLUMN_NAME, SQL_COLUMN_NULLABLE o SQL_COLUMN_COUNT, le chiamate di gestione Driver **SQLColAttribute** nel driver con la *FieldIdentifier* argomento con mappata a SQL_DESC_NAME, SQL_DESC_NULLABLE o SQL_DESC_COUNT, come appropriato*.* Tutti gli altri valori di *fDescType* vengono passati al driver.  
  
 Un'applicazione ODBC 3*x* driver deve supportare tutti i 3 ODBC*x* *FieldIdentifiers* elencati per **SQLColAttribute**.  
  
 Un'applicazione ODBC 3*x* driver deve supportare SQL_COLUMN_PRECISION e SQL_DESC_PRECISION, SQL_COLUMN_SCALE e SQL_DESC_SCALE, SQL_COLUMN_LENGTH e SQL_DESC_LENGTH. Questi valori sono diversi perché precisione, scala e lunghezza vengono definite in modo diverso in ODBC 3*x* rispetto alle API ODBC 2. *x*. Per ulteriori informazioni, vedere [dimensioni di colonna, cifre decimali, trasferimento ottetto lunghezza e dimensioni di visualizzazione](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) appendice d: tipo di dati.
