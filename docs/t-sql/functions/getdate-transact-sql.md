---
title: GETDATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GETDATE_TSQL
- GETDATE
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- GETDATE function [SQL Server]
- current date and time [SQL Server]
- time [SQL Server], current
- functions [SQL Server], time
- system date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- date and time [SQL Server], GETDATE
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: bebe3b65-2b3e-4c73-bf80-ff1132c680a7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 5750024eea12dd90e9fdb8c69677ddd554e71bb8
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="getdate-transact-sql"></a>GETDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il timestamp di sistema di database corrente come un **datetime** valore senza differenza di fuso orario del database. Questo valore deriva dal sistema operativo del computer in cui è in esecuzione l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  La precisione in secondi frazionari di SYSDATETIME e SYSUTCDATETIME è maggiore di quella di GETDATE e GETUTCDATE. SYSDATETIMEOFFSET include la differenza di fuso orario di sistema. SYSDATETIME, SYSUTCDATETIME e SYSDATETIMEOFFSET possono essere assegnate a una variabile di qualsiasi tipo di data e ora.  
  
 Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
GETDATE ( )  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **datetime**  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]le istruzioni possono fare riferimento a GETDATE ovunque possono fare riferimento a un **datetime** espressione.  
  
 GETDATE è una funzione non deterministica. Le viste e le espressioni che fanno riferimento a questa funzione in una colonna non sono indicizzabili.  
  
 Se si utilizza SWITCHOFFSET con la funzione GETDATE() è possibile che la query venga eseguita lentamente perché Query Optimizer non è in grado di ottenere stime di cardinalità corrette per il valore GETDATE. Si consiglia di precalcolare il valore GETDATE e specificare il valore nella query come illustrato nell'esempio seguente. Inoltre, utilizzare l'hint per la query OPTION (RECOMPILE) per forzare query optimizer di ricompilare un piano di query alla successiva esecuzione della stessa query. Query Optimizer otterrà le stime di cardinalità corrette per GETDATE() e produrrà un piano di query più efficiente.  
  
```  
DECLARE @dt datetimeoffset = switchoffset (CONVERT(datetimeoffset, GETDATE()), '-04:00');   
SELECT * FROM t    
WHERE c1 > @dt OPTION (RECOMPILE);  
  
```  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti sono utilizzate le sei funzioni di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che restituiscono data e ora corrente per restituire la data, l'ora o entrambe. I valori sono restituiti in serie. Pertanto, i secondi frazionari potrebbero essere diversi.  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. Recupero della data e dell'ora correnti del sistema  
  
```  
SELECT SYSDATETIME()  
    ,SYSDATETIMEOFFSET()  
    ,SYSUTCDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE()  
    ,GETUTCDATE();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="b-getting-the-current-system-date"></a>B. Recupero della data corrente del sistema  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
SYSDATETIME()          2007-05-03  
SYSDATETIMEOFFSET()    2007-05-03  
SYSUTCDATETIME()       2007-05-04  
CURRENT_TIMESTAMP      2007-05-03  
GETDATE()              2007-05-03  
GETUTCDATE()           2007-05-04
``` 
  
### <a name="c-getting-the-current-system-time"></a>C. Recupero dell'ora corrente del sistema  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, SYSDATETIMEOFFSET())  
    ,CONVERT (time, SYSUTCDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE())  
    ,CONVERT (time, GETUTCDATE());  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```
SYSDATETIME()      13:18:45.3490361  
SYSDATETIMEOFFSET()13:18:45.3490361  
SYSUTCDATETIME()   20:18:45.3490361  
CURRENT_TIMESTAMP  13:18:45.3470000  
GETDATE()          13:18:45.3470000  
GETUTCDATE()       20:18:45.3470000  
```
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 L'esempio seguente usa tre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] funzioni di sistema che restituiscono una data corrente e l'ora per restituire la data, ora o entrambi. I valori sono restituiti in serie. Pertanto, i secondi frazionari potrebbero essere diversi.  
  
### <a name="d-getting-the-current-system-date-and-time"></a>D. Recupero della data e dell'ora correnti del sistema  
  
```  
SELECT SYSDATETIME()  
    ,CURRENT_TIMESTAMP  
    ,GETDATE();  
```  
  
### <a name="e-getting-the-current-system-date"></a>E. Recupero della data corrente del sistema  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE());  
  
```  
  
### <a name="f-getting-the-current-system-time"></a>F. Recupero dell'ora corrente del sistema  
  
```  
SELECT CONVERT (time, SYSDATETIME())  
    ,CONVERT (time, CURRENT_TIMESTAMP)  
    ,CONVERT (time, GETDATE());  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
  
  

