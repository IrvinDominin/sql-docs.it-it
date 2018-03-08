---
title: GIORNO (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/30/2017
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
- DAY_TSQL
- DAY
dev_langs:
- TSQL
helpviewer_keywords:
- date and time [SQL Server], DAY
- dates [SQL Server], functions
- DAY function [SQL Server]
- dates [SQL Server], days
- functions [SQL Server], date and time
- dateparts [SQL Server], day
ms.assetid: 2f4410ea-fd3e-4d69-ac4b-3b0091a084bc
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 444df60a2cfe3adae045020b3db8d673946dccb1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="day-transact-sql"></a>DAY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Restituisce un intero che rappresenta il giorno (giorno del mese) dell'oggetto specificato *data*.
  
Per una panoramica di tutti i [!INCLUDE[tsql](../../includes/tsql-md.md)] tipi di dati data e ora e funzioni, vedere [data e ora i tipi di dati e funzioni &#40; Transact-SQL &#41; ](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DAY ( date )  
```  
  
## <a name="arguments"></a>Argomenti  
*data*  
È un'espressione che può essere risolta in un **ora**, **data**, **smalldatetime**, **datetime**, **datetime2**, o **datetimeoffset** valore. Il *data* argomento può essere un'espressione, l'espressione di colonna, variabile definita dall'utente o valore letterale stringa.
  
## <a name="return-type"></a>Tipo restituito  
**int**
  
## <a name="return-value"></a>Valore restituito  
DAY restituisce lo stesso valore di [DATEPART](../../t-sql/functions/datepart-transact-sql.md) (**giorno**, *data*).
  
Se *data* contiene solo una parte dell'ora, il valore restituito è 1, il giorno di base.
  
## <a name="examples"></a>Esempi  
L'istruzione seguente restituisce `30`. Si tratta del numero del giorno.
  
```sql
SELECT DAY('2015-04-30 01:01:01.1234567');  
```  
  
L'istruzione seguente restituisce `1900, 1, 1`. L'argomento per *data* è il numero `0`. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `0` viene interpretato come 1 gennaio 1900.
  
```sql
SELECT YEAR(0), MONTH(0), DAY(0);  
```  
  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  


