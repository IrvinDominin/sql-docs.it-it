---
title: Compatibilità del Driver di Database desktop | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], Unicode
- Unicode [ODBC], desktop database drivers
- ODBC desktop database drivers [ODBC], Unicode
- backward compatibility [ODBC], Unicode
- desktop database drivers [ODBC], Unicode
- Jet-based ODBC drivers [ODBC], Unicode
ms.assetid: dd695638-1a0b-4e27-8a6a-9510ebb5a5ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5fb1e93c996b68a3110449dab797beb5c93208b4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32899766"
---
# <a name="desktop-database-driver-compatibility"></a>Compatibilità del Driver di Database desktop
Unicode è un metodo di codifica dei caratteri software considera tutti i caratteri con una larghezza fissa di due byte. Questo metodo viene utilizzato come alternativa alla codifica dei caratteri ANSI di Windows che, poiché rappresenta i caratteri in un byte, è limitata a 256 caratteri. Perché rappresenta oltre 65.000 caratteri Unicode, supporta molte lingue i cui caratteri non sono rappresentate nella codifica ANSI.  
  
 La gestione Driver ODBC 3.5 (o versione successiva) è abilitata per Unicode. Ciò influisce su due aree principali: chiamate di funzione e tipi di dati string. Gli argomenti di stringa di gestione Driver mappe funzione e i dati stringa come richiesto dall'applicazione e driver, entrambe le quali può essere abilitata per Unicode o ANSI abilitati.  
  
 La gestione Driver ODBC 3.5 (o versioni successive) supporta l'utilizzo di un driver di Unicode con un'applicazione Unicode e un'applicazione ANSI. Supporta inoltre l'utilizzo di un driver ANSI con un'applicazione ANSI. Gestione Driver fornisce mapping Unicode-to-ANSI limitato per un'applicazione Unicode utilizzano un driver ANSI. Ciò consente l'accesso ai database Jet 3.5 e supporto di tutti i tipi di file ISAM esistenti.  
  
 Quando un'applicazione ANSI utilizza il Driver 4.0 Database Desktop ODBC e accede a Microsoft Access 4.0 o versioni successive, il driver espone il tipo di dati come SQL_CHAR, SQL_VARCHAR o SQL_LONGVARCHAR anche se Jet 4.0 supporta la versione grande. Le versioni precedenti di Jet non supportano SQL_WCHAR, SQL_WVARCHAR e SQL_WLONGVARCHAR. Questa restrizione si applica anche nei casi in cui i formati precedenti vengono utilizzati con il motore di Database Jet 4.0.  
  
 Per ulteriori informazioni relative a problemi di Unicode con ODBC, vedere [Unicode](../../odbc/reference/develop-app/unicode.md) in considerazioni di programmazione.
