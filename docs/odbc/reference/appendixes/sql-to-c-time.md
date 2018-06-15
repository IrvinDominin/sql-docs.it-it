---
title: 'SQL a c: ora | Documenti Microsoft'
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
- converting data from SQL to C types [ODBC], time
- time data type [ODBC]
- data conversions from SQL to C types [ODBC], time
ms.assetid: 6dc59973-7bb5-40f1-87c8-5bf68b3bf2ee
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b66aeca41cd705a21e7d6aa6d306a9032e86bba9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32908596"
---
# <a name="sql-to-c-time"></a>SQL a c: ora
L'identificatore per l'ora in cui il tipo di dati SQL ODBC è:  
  
 SQL_TYPE_TIME  
  
 Nella tabella seguente viene illustrato come ODBC C a cui possono essere convertiti i dati SQL ora i tipi di dati. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da SQL a tipi di dati C](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|Identificatore di tipo C|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > lunghezza in byte di caratteri<br /><br /> *9* <= *BufferLength* < = lunghezza in byte di caratteri<br /><br /> *BufferLength* < 9|data<br /><br /> Dati troncati [a]<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > lunghezza in caratteri<br /><br /> *9* <= *BufferLength* < = lunghezza in caratteri<br /><br /> *BufferLength* < 9|data<br /><br /> Dati troncati [a]<br /><br /> Non definito|Lunghezza dei dati in caratteri<br /><br /> Lunghezza dei dati in caratteri<br /><br /> Non definito|n/d<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|Lunghezza in byte dei dati < = *BufferLength*<br /><br /> Lunghezza in byte dei dati > *BufferLength*|data<br /><br /> Non definito|Lunghezza in byte dei dati<br /><br /> Non definito|n/d<br /><br /> 22003|  
|SQL_C_TYPE_TIME|Nessuna [b]|data|6 [d]|n/d|  
|SQL_C_TYPE_TIMESTAMP|Nessuna [b]|Dati [c]|16 [d]|n/d|  
  
 [a] vengono troncati i secondi frazionari del tempo.  
  
 [b] il valore di *BufferLength* viene ignorata per la conversione. Il driver presuppone che le dimensioni di **TargetValuePtr* è la dimensione del tipo di dati C.  
  
 [c] i campi data della struttura di timestamp vengono impostati sulla data corrente e il campo secondi frazionari della struttura di timestamp è impostato su zero.  
  
 [d] è la dimensione del tipo di dati C corrispondente.  
  
 Quando i dati SQL ora vengono convertiti in dati di tipo carattere C, la stringa risultante è il "*hh*:*mm*:*ss*" formato. Questo formato non è interessato dalla configurazione dell'impostazione di paese Windows®.
