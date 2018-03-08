---
title: Inizializzazione di campi di descrizione | Documenti Microsoft
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
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9798d84c3f06449637160d75b2e53bc41b70486a
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="initialization-of-descriptor-fields"></a>Inizializzazione di campi di descrizione
Quando viene allocato un descrittore della riga di applicazione, i relativi campi ricevono i valori iniziali come indicato nella [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Il valore iniziale del campo SQL_DESC_TYPE è SQL_DEFAULT. Ciò consente un trattamento dei dati di database per la presentazione all'applicazione standard. L'applicazione può specificare diversi trattamento dei dati impostando i campi di record del descrittore.  
  
 Il valore iniziale di SQL_DESC_ARRAY_SIZE nell'intestazione del descrittore è 1. L'applicazione può modificare questo campo per abilitare un recupero più righe.  
  
 Il concetto di un valore predefinito non è valido per i campi di un'implementazione. Un'applicazione può accedere ai campi di un IRD solo se è presente un'istruzione preparata o eseguita è associata.  
  
 Alcuni campi di un IPD sono definiti solo dopo il IPD sono popolate automaticamente dal driver. Se non sono definiti. Questi campi sono SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED e SQL_DESC_LOCAL_TYPE_NAME.
