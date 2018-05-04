---
title: Lunghezza del tipo di dati di intervallo | Documenti Microsoft
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
- data types [ODBC], interval data types
- length of data types [ODBC]
- interval data type [ODBC], length
ms.assetid: e9eb38d8-f9db-4401-8c62-aa394054cbbf
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e611326930b099496db893d4d46d36bbd04116ac
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="interval-data-type-length"></a>Lunghezza del tipo di dati intervallo
Le regole seguenti vengono utilizzate per determinare la lunghezza di un tipo di dati di intervallo in caratteri. Lunghezza è espressa in numero di caratteri. Il numero di byte dipende dal set di caratteri. La lunghezza include i seguenti valori aggiunti insieme:  
  
-   Due caratteri per ogni campo nell'intervallo che non è il campo iniziale.  
  
-   Per il campo iniziale, il numero di caratteri che rappresenta la precisione iniziale espressa o implicita. Se la precisione iniziale non è specificata, il valore predefinito è 2.  
  
-   Un carattere per il separatore tra i campi.  
  
-   Uno più la precisione dei secondi espressa o implicita. Se la precisione dei secondi non è specificata, il valore predefinito è 6.  
  
 I valori di lunghezza di colonna specifica per ogni tipo di dati di intervallo sono contenuti in [dimensioni della colonna](../../../odbc/reference/appendixes/column-size.md).
