---
title: Gli identificatori di tipo SQL | Documenti Microsoft
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
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 98c78940a3e01943da03b92f5791dc8f146b14c7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-type-identifiers"></a>Identificatori di tipo SQL
Ogni origine dati definisce i propri tipi di dati SQL. ODBC definisce gli identificatori di tipo e vengono descritte le caratteristiche generali dei tipi di dati SQL che potrebbero essere mappate a ogni identificatore di tipo. È come ogni tipo di dati nell'origine dati sottostante viene eseguito il mapping a un identificatore di tipo SQL ODBC specifiche del driver.  
  
 Ad esempio, SQL_CHAR è l'identificatore di tipo per una colonna di tipo carattere a lunghezza fissa, in genere compreso tra 1 e 254 caratteri. Queste caratteristiche corrispondono al tipo di dati CHAR a molte origini dati SQL, vedere. Pertanto, quando un'applicazione rileva che l'identificatore di tipo per una colonna è SQL_CHAR, può presupporre che è probabile che occupa una colonna CHAR. Tuttavia, è necessario controllare ancora la lunghezza in byte della colonna prima di presumere che si è compreso tra 1 e 254 caratteri. il driver per un'origine dati non SQL, ad esempio, può eseguire il mapping una colonna di tipo carattere a lunghezza fissa di 500 caratteri SQL_CHAR o SQL_LONGVARCHAR, perché non è una corrispondenza esatta.  
  
 ODBC definisce un'ampia gamma di identificatori di tipo SQL. Tuttavia, il driver non è necessario utilizzare tutti gli identificatori. Utilizza invece solo tali identificatori che deve esporre tipi di dati SQL supportati dall'origine dati sottostante. Se l'origine dati sottostante supporta i tipi di dati SQL per cui alcun identificatore di tipo non corrispondente, il driver è possibile definire identificatori di tipo aggiuntivo. Per ulteriori informazioni, vedere [tipi di dati specifici del Driver, descrittore di tipi, tipi di informazioni, tipi di diagnostica e gli attributi](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Per una descrizione completa degli identificatori di tipo SQL, vedere [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md) appendice d: tipo di dati.
