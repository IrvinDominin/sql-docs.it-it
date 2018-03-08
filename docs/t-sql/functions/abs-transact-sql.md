---
title: ABS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/24/2017
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
- ABS_TSQL
- ABS
dev_langs:
- TSQL
helpviewer_keywords:
- values [SQL Server], positive
- values [SQL Server], absolute
- ABS function
- absolute positive value
ms.assetid: e2ea7a6d-3e2f-472c-afbc-437d3b835c03
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 9f96d651f179120fab6fabfb78d08cca84404bd1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="abs-transact-sql"></a>ABS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Funzione matematica che restituisce il valore assoluto (positivo) dell'espressione numerica specificata. (`ABS` modifiche negativo valori ai valori positivi. `ABS`non ha alcun effetto su zero o i valori positivi.)
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
ABS ( numeric_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
*numeric_expression*  
Espressione della categoria del tipo di dati numerici esatti o numerici approssimati.
  
## <a name="return-types"></a>Tipi restituiti  
Restituisce lo stesso tipo di *numeric_expression*.
  
## <a name="examples"></a>Esempi  
Nell'esempio seguente vengono illustrati i risultati dell'utilizzo della funzione `ABS` in tre numeri diversi.
  
```sql
SELECT ABS(-1.0), ABS(0.0), ABS(1.0);  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
---- ---- ----  
1.0  .0   1.0  
```  
  
La funzione `ABS` può produrre un errore di overflow quando il valore assoluto di un numero è maggiore del numero più alto che può essere rappresentato dal tipo di dati specificato. Il tipo di dati `int`, ad esempio, consente di archiviare solo valori compresi tra `-2,147,483,648` e `2,147,483,647`. Il calcolo del valore assoluto per il valore integer con segno `-2,147,483,648` provoca un errore di overflow, in quanto il valore assoluto corrispondente è maggiore dell'intervallo positivo per il tipo di dati `int`.
  
```sql
DECLARE @i int;  
SET @i = -2147483648;  
SELECT ABS(@i);  
GO  
```  
  
Messaggio di errore:
  
"Messaggio 8115, livello 16, stato 2, riga 3"
  
"Errore di runtime: si è verificato un errore di overflow aritmetico durante la conversione del tipo di dati da espressione a int".

  
## <a name="see-also"></a>Vedere anche
[CAST e CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[Funzioni matematiche &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
[Funzioni predefinite &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md)
  
  

