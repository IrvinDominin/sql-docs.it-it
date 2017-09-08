---
title: '@@NESTLEVEL (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@NESTLEVEL'
- '@@NESTLEVEL_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@NESTLEVEL function'
- nesting stored procedures
- stored procedure nesting levels [SQL Server]
ms.assetid: 8c0b2134-8616-44f6-addc-6583c432fb62
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ce6980ba008189a1588dc87e955a26125dc6a30d
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="nestlevel-transact-sql"></a>@@NESTLEVEL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il livello di nidificazione dell'esecuzione corrente di stored procedure (il livello iniziale è 0) nel server locale.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
@@NESTLEVEL  
```  
  
## <a name="return-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta che una stored procedure ne richiama un'altra oppure esegue codice gestito tramite un riferimento a una routine CLR, un tipo CLR o una funzione di aggregazione CLR, il livello di nidificazione viene incrementato. Quando viene superato il livello massimo pari a 32, la transazione viene interrotta.  
  
 Quando @@NESTLEVEL viene eseguita all'interno di un [!INCLUDE[tsql](../../includes/tsql-md.md)] stringa, il valore restituito è 1 + corrente livello di nidificazione. Quando @@NESTLEVEL viene eseguita in modo dinamico utilizzando sp_executesql il valore restituito è 2 + il livello di nidificazione corrente.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-nestlevel-in-a-procedure"></a>A. Tramite@NESTLEVEL in una stored procedure  
 Nell'esempio seguente vengono create due procedure: una procedura che richiama l'altra e una che visualizza le impostazioni della funzione `@@NESTLEVEL` di ciascuna procedura.  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID (N'usp_OuterProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_OuterProc;  
GO  
IF OBJECT_ID (N'usp_InnerProc', N'P')IS NOT NULL  
    DROP PROCEDURE usp_InnerProc;  
GO  
CREATE PROCEDURE usp_InnerProc AS   
    SELECT @@NESTLEVEL AS 'Inner Level';  
GO  
CREATE PROCEDURE usp_OuterProc AS   
    SELECT @@NESTLEVEL AS 'Outer Level';  
    EXEC usp_InnerProc;  
GO  
EXECUTE usp_OuterProc;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Outer Level`  
  
 `-----------`  
  
 `1`  
  
 `Inner Level`  
  
 `-----------`  
  
 `2`  
  
### <a name="b-calling-nestlevel"></a>B. La chiamata a @@NESTLEVEL  
 Nell'esempio seguente viene illustrata la differenza dei valori restituiti dalle istruzioni `SELECT`, `EXEC` e `sp`_`executesql` quando ogni istruzione richiama la funzione `@@NESTLEVEL`.  
  
```  
CREATE PROC usp_NestLevelValues AS  
    SELECT @@NESTLEVEL AS 'Current Nest Level';  
EXEC ('SELECT @@NESTLEVEL AS OneGreater');   
EXEC sp_executesql N'SELECT @@NESTLEVEL as TwoGreater' ;  
GO  
EXEC usp_NestLevelValues;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Current Nest Level`  
  
 `------------------`  
  
 `1`  
  
 `(1 row(s) affected)`  
  
 `OneGreater`  
  
 `-----------`  
  
 `2`  
  
 `(1 row(s) affected)`  
  
 `TwoGreater`  
  
 `-----------`  
  
 `3`  
  
 `(1 row(s) affected)`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Creazione di una stored procedure](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  