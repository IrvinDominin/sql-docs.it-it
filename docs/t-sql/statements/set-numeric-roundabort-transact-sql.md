---
title: SET NUMERIC_ROUNDABORT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NUMERIC_ROUNDABORT
- SET_NUMERIC_ROUNDABORT_TSQL
- SET NUMERIC_ROUNDABORT
- NUMERIC_ROUNDABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- rounding expressions
- precision [SQL Server], rounded expressions
- expressions [SQL Server], rounding
- NUMERIC_ROUNDABORT
- SET NUMERIC_ROUNDABORT statement
ms.assetid: d20e74f1-b8da-466c-b180-9d8a8b851a77
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4f5a5369321999a980835a502a730bfe383aefd
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="set-numericroundabort-transact-sql"></a>SET NUMERIC_ROUNDABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Specifica il livello di segnalazione degli errori generato quando l'arrotondamento in un'espressione comporta una perdita di precisione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Sintassi

```

SET NUMERIC_ROUNDABORT { ON | OFF }
```
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione SET NUMERIC_ROUNDABORT è impostata su ON, viene generato un errore dopo che si verifica una perdita di precisione in un'espressione. Quando l'opzione è impostata su OFF, in seguito alla perdita di precisione non viene visualizzato alcun messaggio di errore e il risultato viene arrotondato alla precisione della colonna o della variabile in cui viene archiviato.  
  
 La perdita di precisione si verifica quando si tenta di archiviare un valore con precisione fissa in una colonna o variabile con grado di precisione inferiore.  
  
 Se l'opzione SET NUMERIC_ROUNDABORT è impostata su ON, l'opzione SET ARITHABORT determina la gravità dell'errore generato. In questa tabella vengono descritti i risultati ottenuti con le due impostazioni quando si verifica una perdita di precisione.  
  
|Impostazione|SET NUMERIC_ROUNDABORT ON|SET NUMERIC_ROUNDABORT OFF|
|-------------|--------------------------------|---------------------------------|
|SET ARITHABORT ON|Viene generato un errore, senza la restituzione di alcun set di risultati.|Nessun errore o avviso, arrotondamento del risultato.|  
|SET ARITHABORT OFF|Viene restituito un avviso e l'espressione restituisce NULL.|Nessun errore o avviso, arrotondamento del risultato.|  

 L'opzione SET NUMERIC_ROUNDABORT viene impostata in fase di esecuzione, non in fase di analisi.

 È necessario che l'opzione SET NUMERIC_ROUNDABORT sia impostata su OFF quando vengono creati o modificati indici in colonne calcolate o viste indicizzate. Se l'opzione SET NUMERIC_ROUNDABORT è ON, CREATE, le istruzioni UPDATE, INSERT e DELETE nelle tabelle con indici su colonne calcolate o viste indicizzate esito negativo. Per ulteriori informazioni sulle impostazioni dell'opzione SET necessarie con viste indicizzate e indici in colonne calcolate, vedere "Considerazioni quando si usa delle istruzioni SET" in [istruzioni SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query seguente:
  
```  
DECLARE @NUMERIC_ROUNDABORT VARCHAR(3) = 'OFF';  
IF ( (8192 & @@OPTIONS) = 8192 ) SET @NUMERIC_ROUNDABORT = 'ON';  
SELECT @NUMERIC_ROUNDABORT AS NUMERIC_ROUNDABORT;  
  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono illustrati due valori con una precisione di quattro cifre decimali che vengono aggiunti e archiviati in una variabile con una precisione di due cifre decimali. Le espressioni illustrano il risultato ottenuto con le diverse impostazioni delle opzioni `SET NUMERIC_ROUNDABORT` e `SET ARITHABORT`.  
  
```  
-- SET NOCOUNT to ON,   
-- SET NUMERIC_ROUNDABORT to ON, and SET ARITHABORT to ON.  
SET NOCOUNT ON;  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to ON and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT ON';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT ON;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to ON.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT ON';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT ON;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234 ;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
  
-- SET NUMERIC_ROUNDABORT to OFF and SET ARITHABORT to OFF.  
PRINT 'SET NUMERIC_ROUNDABORT OFF';  
PRINT 'SET ARITHABORT OFF';  
SET NUMERIC_ROUNDABORT OFF;  
SET ARITHABORT OFF;  
GO  
DECLARE @result DECIMAL(5, 2),  
   @value_1 DECIMAL(5, 4),   
   @value_2 DECIMAL(5, 4);  
SET @value_1 = 1.1234;  
SET @value_2 = 1.1234;  
SELECT @result = @value_1 + @value_2;  
SELECT @result;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHABORT &#40; Transact-SQL &#41;](../../t-sql/statements/set-arithabort-transact-sql.md)  
  
  
