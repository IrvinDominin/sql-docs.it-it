---
title: Tipi di dati C | Documenti Microsoft
ms.custom: 
ms.date: 07/12/2017
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
- data types [ODBC], C data types
- C data types [ODBC], about C data types
- C data types [ODBC]
- C buffers [ODBC]
ms.assetid: b681d260-3dbb-47df-a616-4910d727add7
caps.latest.revision: "19"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 31de2fc95be1a7ead0b61b2dde493caf8d484fe4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="c-data-types"></a>Tipi di dati C
Tipi di dati C ODBC indicano il tipo di dati di buffer C utilizzato per archiviare i dati nell'applicazione.  
  
 Tutti i driver devono supportare tutti i tipi di dati C. Ciò è fondamentale perché tutti i driver devono supportare tutti i tipi di C, a cui è possibile convertire i tipi SQL che supportano e tutti i driver supportano almeno un carattere di tipo SQL. Poiché il tipo di carattere SQL può essere convertito in e da tutti i tipi C, tutti i driver devono supportare tutti i tipi C.  
  
 Viene specificato il tipo di dati C nel **SQLBindCol** e **SQLGetData** funzioni con il *TargetType* argomento e il **SQLBindParameter**è utilizzabile con il *ValueType* argomento. Può anche essere specificato tramite la chiamata **SQLSetDescField** per impostare il campo SQL_DESC_CONCISE_TYPE di un ARD o APD, oppure chiamando **SQLSetDescRec** con il *tipo* argomento (e il *sottotipo* argomento se necessario) e *DescriptorHandle* argomento impostato per l'handle di un ARD o APD.  
  
 Nelle tabelle seguenti sono elencati gli identificatori di tipo valido per i tipi di dati C. La tabella include anche il tipo di dati C ODBC che corrisponde a ogni identificatore e la definizione di questo tipo di dati.  
  
|Identificatore di tipo C|Typedef di ODBC C|Tipo C|  
|-----------------------|--------------------|------------|  
|SQL_C_CHAR|SQLCHAR *|unsigned char *|  
|SQL_C_WCHAR|SQLWCHAR *|wchar_t *|  
|SQL_C_SSHORT [j#]|SQLSMALLINT|short int|  
|SQL_C_USHORT [j#]|SQLUSMALLINT|Unsigned Integer a breve|  
|SQL_C_SLONG [j#]|SQLINTEGER|long int|  
|SQL_C_ULONG [j#]|SQLUINTEGER|unsigned long integer|  
|SQL_C_FLOAT|SQLREAL|FLOAT|  
|SQL_C_DOUBLE|SQLDOUBLE, SQLFLOAT|double|  
|SQL_C_BIT|SQLCHAR|unsigned char|  
|SQL_C_STINYINT [j#]|SQLSCHAR|char con segno|  
|SQL_C_UTINYINT [j#]|SQLCHAR|unsigned char|  
|SQL_C_SBIGINT|SQLBIGINT|_int64 [h]|  
|SQL_C_UBIGINT|SQLUBIGINT|senza segno _int64 [h]|  
|SQL_C_BINARY|SQLCHAR *|unsigned char *|  
|SQL_C_BOOKMARK [i]|SEGNALIBRO|unsigned long integer [d]|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|  
|Tutti i tipi di dati di intervallo C|SQL_INTERVAL_STRUCT|Vedere il [struttura intervallo C](../../../odbc/reference/appendixes/c-interval-structure.md) sezione più avanti in questa appendice.|  
  
 **Identificatore di tipo C** SQL_C_TYPE_DATE [c]  
  
 **Typedef di ODBC C** valore SQL_DATE_STRUCT  
  
 **Tipo C**  
  
```  
struct tagDATE_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;    
} DATE_STRUCT;[a]  
```  
  
 **Identificatore di tipo C** SQL_C_TYPE_TIME [c]  
  
 **Typedef di ODBC C** SQL_TIME_STRUCT  
  
 **Tipo C**  
  
```  
struct tagTIME_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
} TIME_STRUCT;[a]  
```  
  
 **Identificatore di tipo C** SQL_C_TYPE_TIMESTAMP [c]  
  
 **Typedef di ODBC C** SQL_TIMESTAMP_STRUCT  
  
 **Tipo C**  
  
```  
struct tagTIMESTAMP_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;[b]   
} TIMESTAMP_STRUCT;[a]  
```  
  
 **Identificatore di tipo C** SQL_C_NUMERIC  
  
 **Typedef di ODBC C** SQL_NUMERIC_STRUCT  
  
 **Tipo C**  
  
```  
struct tagSQL_NUMERIC_STRUCT {  
   SQLCHAR precision;  
   SQLSCHAR scale;  
   SQLCHAR sign[g];  
   SQLCHAR val[SQL_MAX_NUMERIC_LEN];[e], [f]   
} SQL_NUMERIC_STRUCT;  
```  
  
 **Identificatore di tipo C** SQL_C_GUID  
  
 **Typedef di ODBC C** SQLGUID  
  
 **Tipo C**  
  
```  
struct tagSQLGUID {  
   DWORD Data1;  
   WORD Data2;  
   WORD Data3;  
   BYTE Data4[8];  
} SQLGUID;[k]  
```  
  
 [a] i valori di anno, mese, giorno, ora, minuto e secondo campi nei tipi di dati datetime C devono essere conforme ai vincoli del calendario gregoriano. (Vedere [vincoli del calendario gregoriano](../../../odbc/reference/appendixes/constraints-of-the-gregorian-calendar.md) più avanti in questa appendice.)  
  
 [b] il valore del campo frazione è il numero di miliardesimi di secondo e compreso tra 0 e 999.999.999 (meno di 1 miliardo 1). Ad esempio, il valore del campo frazione per mezzo secondo è 500,000,000, per un millesimo di secondo (in uno millisecondi) sono pari a 1.000.000, per un milionesimo di secondo (un microsecondo) è 1.000 e per un miliardesimo di secondo (un nanosecondo) è 1.  
  
 [c] in ODBC 2. *x*, i tipi di dati date, time e timestamp C sono SQL_C_DATE, SQL_C_TIME e SQL_C_TIMESTAMP.  
  
 [d] ODBC 3*x* le applicazioni devono utilizzare SQL_C_VARBOOKMARK, non SQL_C_BOOKMARK. Quando un'applicazione ODBC 3*x* applicazione funziona con un'API ODBC 2. *x* driver ODBC 3*x* Driver Manager eseguirà il mapping a SQL_C_BOOKMARK SQL_C_VARBOOKMARK.  
  
 [e] un numero viene archiviato nel *val* campo della struttura di SQL_NUMERIC_STRUCT come un integer ridotto, in modalità little-endian little (il byte più a sinistra viene il byte meno significativo). Ad esempio, il numero 10,001 in base 10, con una scala pari a 4, viene ridotto a un numero intero di 100010. Poiché si tratta 186AA in formato esadecimale, il valore in SQL_NUMERIC_STRUCT sarebbe "AA 86 01 00 00... 00", con il numero di byte definito per il SQL_MAX_NUMERIC_LEN **#define**.  
  
 Per ulteriori informazioni su **SQL_NUMERIC_STRUCT**, vedere [HOWTO: recupero di dati numerici con SQL_NUMERIC_STRUCT](retrieve-numeric-data-sql-numeric-struct-kb222831.md).  
  
 [f] i campi di precisione e scala dei dati SQL_C_NUMERIC digitare areused per l'input da un'applicazione e per l'output dal driver per l'applicazione. Quando il driver scrive un valore numerico nel SQL_NUMERIC_STRUCT, predefinito specifici del driver viene utilizzata come valore per il *precisione* campo che verrà utilizzato il valore nel campo del descrittore (applicazione SQL_DESC_SCALE che per impostazione predefinita 0) per il *scala* campo. Un'applicazione può fornire i propri valori per la precisione e scala, impostare i campi SQL_DESC_PRECISION e SQL_DESC_SCALE del descrittore di applicazione.  
  
 [g] per il campo di accesso è 1 se è positivo, 0 se è negativo.  
  
 [h] _int64 potrebbe non essere fornito da alcuni compilatori.  
  
 [i] _SQL_C_BOOKMARK è stato deprecato in ODBC 3*x*.  
  
 [j#] _SQL_C_SHORT SQL_C_LONG e SQL_C_TINYINT sono stati sostituiti in ODBC da tipi signed e unsigned: SQL_C_SSHORT e SQL_C_USHORT, SQL_C_SLONG e SQL_C_ULONG, SQL_C_STINYINT e SQL_C_UTINYINT. Un'applicazione ODBC 3*x* driver che dovrebbero funzionare con ODBC 2. *x* applicazioni devono supportare SQL_C_SHORT SQL_C_LONG e SQL_C_TINYINT, perché quando vengono chiamati, gestione Driver li passa attraverso il driver.  
  
 [k] SQL_C_GUID può essere convertito solo in SQL_CHAR o SQL_WCHAR.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Strutture di interi a 64 bit](../../../odbc/reference/appendixes/64-bit-integer-structures.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati C in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)
