---
title: 'C a SQL: data | Documenti Microsoft'
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
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ba2869a8fb8272251f6a23df0808b12e68ec5a59
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-date"></a>C a SQL: data
L'identificatore per il tipo di dati ODBC C data è:  
  
 SQL_C_TYPE_DATE  
  
 Nella tabella seguente viene illustrato SQL ODBC i tipi di dati a cui può essere convertito data dati C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Lunghezza in byte di colonna > = 10<br /><br /> Colonna lunghezza < 10 byte<br /><br /> Valore di dati non è una data valida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Lunghezza in caratteri colonna > = 10<br /><br /> Colonna carattere a lunghezza < 10<br /><br /> Valore di dati non è una data valida|n/d<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|Valore di dati è una data valida<br /><br /> Valore di dati non è una data valida|n/d<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|Valore di dati è una data valida [a]<br /><br /> Valore di dati non è una data valida|n/d<br /><br /> 22007|  
  
 [a] la porzione dell'ora del timestamp è impostata su zero.  
  
 Per informazioni su quali sono i valori validi in una struttura SQL_C_TYPE_DATE, vedere [tipi di dati C](../../../odbc/reference/appendixes/c-data-types.md), più indietro in questa appendice.  
  
 Quando i dati di data C viene convertiti in dati SQL di tipo carattere, i dati di caratteri risultante sono nel "*aaaa*-*mm*-*gg*" formato.  
  
 Il driver ignora il valore di lunghezza/indicatore quando la conversione dei dati dal tipo di dati Data C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati Data C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.
