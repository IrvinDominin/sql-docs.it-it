---
title: 'C a SQL: numerico | Documenti Microsoft'
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
- numeric data type [ODBC], converting
- data conversions from C to SQL types [ODBC], numeric
- converting data from c to SQL types [ODBC], numeric
ms.assetid: af4095ff-06c3-4b04-83bf-19f9ee098dc2
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 788a317dc58eaa83b0caadd3d2a6c02d49398d7c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="c-to-sql-numeric"></a>C a SQL: numerico
Gli identificatori per i tipi di dati C ODBC numerici sono:  
  
 SQL_C_STINYINT  
  
 SQL_C_SLONG  
  
 SQL_C_UTINYINT  
  
 SQL_C_ULONG  
  
 SQL_C_TINYINT  
  
 SQL_C_LONG  
  
 SQL_C_SSHORT  
  
 SQL_C_FLOAT  
  
 SQL_C_USHORT  
  
 SQL_C_DOUBLE  
  
 SQL_C_SHORT  
  
 SQL_C_NUMERIC  
  
 SQL_C_SBIGINT  
  
 SQL_C_UBIGINT  
  
 Nella tabella seguente viene illustrato SQL ODBC dei tipi di dati a cui possono essere convertiti i dati numerici di C. Per una spiegazione delle colonne e delle condizioni nella tabella, vedere [la conversione di dati da C a tipi di dati SQL](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md).  
  
|Identificatore di tipo SQL|Test|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|Numero di cifre < = lunghezza di colonna in byte<br /><br /> Numero di cifre > lunghezza di colonna in byte|n/d<br /><br /> 22001|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|Numero di caratteri < = lunghezza in caratteri colonna<br /><br /> Numero di caratteri > lunghezza in caratteri colonna|n/d<br /><br /> 22001|  
|SQL_DECIMAL [b]<br /><br /> SQL_NUMERIC [b]<br /><br /> SQL_TINYINT [b]<br /><br /> SQL_SMALLINT [b]<br /><br /> SQL_INTEGER [b]<br /><br /> SQL_BIGINT [b]|Dati convertiti senza troncamento o con troncamento delle cifre frazionarie<br /><br /> Convertire dati con il troncamento di cifre intere|n/d<br /><br /> 22003|  
|SQL_REAL<br /><br /> SQL_FLOAT<br /><br /> SQL_DOUBLE|Dati sono compreso nell'intervallo del tipo di dati a cui il numero viene convertito<br /><br /> Dati non rientra nell'intervallo del tipo di dati a cui il numero viene convertito|n/d<br /><br /> 22003|  
|SQL_BIT|I dati sono 0 o 1<br /><br /> Dati sono maggiori di 0, minore di 2 e non è uguale a 1<br /><br /> Dati sono minore di 0 o maggiore di o uguale a 2|n/d<br /><br /> 22001<br /><br /> 22003|  
|SQL_INTERVAL_YEAR [a]<br /><br /> SQL_INTERVAL_MONTH [a]<br /><br /> SQL_INTERVAL_DAY [a]<br /><br /> SQL_INTERVAL_HOUR [a]<br /><br /> SQL_INTERVAL_MINUTE [a]<br /><br /> SQL_INTERVAL_SECOND [a]|Dati non verranno troncati.<br /><br /> Dati troncati.|n/d<br /><br /> 22015|  
  
 [a] queste conversioni sono supportate solo per i tipi di dati numerici esatti (SQL_C_STINYINT, SQL_C_UTINYINT, SQL_C_SSHORT, SQL_C_USHORT, SQL_C_SLONG, SQL_C_ULONG o SQL_C_NUMERIC). Non sono supportati per i tipi di dati numerico approssimato (SQL_C_FLOAT o SQL_C_DOUBLE). Impossibile convertire i tipi di dati C numerici esatto a un intervallo di tipo SQL la cui precisione di intervallo non è un singolo campo.  
  
 [b] per il caso di "n/d", un driver può anche restituire SQL_SUCCESS_WITH_INFO e 01S07 quando si verifica un troncamento frazionario.  
  
 Il driver ignora il valore di lunghezza/indicatore quando si convertono i dati dai tipi di dati numerici di C e si presuppone che le dimensioni del buffer di dati sono la dimensione del tipo di dati numerico di C. Viene passato il valore di lunghezza/indicatore di *StrLen_or_Ind* argomento **SQLPutData** e nel buffer specificato con il *StrLen_or_IndPtr* argomento **SQLBindParameter**. Il buffer dei dati è specificato con il *DataPtr* argomento in **SQLPutData** e *ParameterValuePtr* argomento **SQLBindParameter**.
