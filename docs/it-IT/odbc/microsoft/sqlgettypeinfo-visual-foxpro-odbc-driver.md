---
title: SQLGetTypeInfo (Driver ODBC di Visual FoxPro) | Documenti Microsoft
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
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e1b8fb199de1c902983b09f6538a10b8dde1bef
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Driver ODBC di Visual FoxPro)
> [!NOTE]  
>  In questo argomento contiene informazioni specifiche del Driver ODBC Visual FoxPro. Per informazioni generali su questa funzione, vedere l'argomento appropriato in [riferimento all'API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Supporto: completo  
  
 Conformità di API ODBC: Livello 1  
  
 Restituisce informazioni sui tipi di dati supportati da un'origine dati. Il driver restituisce le informazioni in un set di risultati SQL. Nella tabella seguente sono elencati i tipi di dati ODBC e il tipo di dati Visual FoxPro corrispondente.  
  
|Tipo ODBC|Tipo di Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Non supportato. Tipo non è a 64 bit di Visual FoxPro.|  
|SQL_BIT|Logico|  
|SQL_CHAR|Carattere|  
|SQL_DATE|Data|  
|SQL_DECIMAL|Numeric|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Memo (binario)|  
|SQL_LONGVARCHAR|Memo|  
|SQL_NUMERIC|Numerico *, valuta, Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|Non supportato. Non vi è alcun Visual FoxPro *ora* tipo.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|Memo (binario) *, generale|  
|SQL_VARCHAR|Carattere|  
  
 * Tipo predefinito  
  
 Per ulteriori informazioni sui tipi di dati Visual FoxPro, vedere [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Per ulteriori informazioni su questa funzione, vedere [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) nel *riferimento per programmatori ODBC*.
