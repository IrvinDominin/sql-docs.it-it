---
title: EXP (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 401560f260064a7d09ab2e34dde01a21aa655d9c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce il valore esponenziale dell'oggetto specificato **float** espressione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *argomento float_expression*  
 È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di tipo **float** o di un tipo che può essere convertito in modo implicito in **float**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **float**  
  
## <a name="remarks"></a>Osservazioni  
 La costante **e** (2.718281 …) è la base dei logaritmi naturali.  
  
 L'esponente di un numero è la costante **e** elevato alla potenza del numero. Ad esempio, EXP(1.0) = e^1.0 = 2.71828182845905 ed EXP(10) = e^10 = 22026.4657948067.  
  
 Il valore esponenziale del logaritmo naturale di un numero è il numero stesso: EXP (LOG (*n*)) =  *n* . E il logaritmo naturale dell'esponenziale di un numero è il numero stesso: LOG (EXP (*n*)) =  *n* .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. Ricerca dell'esponente di un numero  
 Nell'esempio seguente viene dichiarata una variabile e viene restituito il valore esponenziale della variabile specificata (`10`) con un testo descrittivo.  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>B. Ricerca di valori esponenziali e logaritmi naturali  
 Nell'esempio seguente viene restituito il valore esponenziale del logaritmo naturale di `20` e il logaritmo naturale del valore esponenziale di `20`. Poiché si tratta di funzioni inverse, il valore restituito in entrambi i casi è `20`.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>C. Ricerca dell'esponente di un numero  
 L'esempio seguente restituisce il valore esponenziale del valore specificato (`10`).  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. Ricerca di valori esponenziali e logaritmi naturali  
 Nell'esempio seguente viene restituito il valore esponenziale del logaritmo naturale di `20` e il logaritmo naturale del valore esponenziale di `20`. Poiché si tratta di funzioni inverse, il valore restituito in entrambi i casi è `20`.  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40; Transact-SQL &#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [LOG &#40; Transact-SQL &#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40; Transact-SQL &#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  

