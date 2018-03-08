---
title: '@@NESTLEVEL (Transact-SQL) | Documenti Microsoft'
ms.custom: 
ms.date: 09/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f513fe1db6c1d3cea11eb2c1d52f246214fb76c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40nestlevel-transact-sql"></a>&#x40;&#x40;NESTLEVEL è (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
  
 ```
Outer Level  
-----------  
1  
  
Inner Level  
-----------  
2
```  
  
### <a name="b-calling-nestlevel"></a>B. La chiamata a @@NESTLEVEL  
 Nell'esempio seguente viene illustrata la differenza in valori restituiti da `SELECT`, `EXEC`, e `sp_executesql` quando ciascuno di essi chiama `@@NESTLEVEL`.  
  
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
  
 ```
Current Nest Level  
------------------  
1  
  
(1 row(s) affected)  
  
OneGreater  
-----------  
2  
  
(1 row(s) affected)  
  
TwoGreater  
-----------  
3  
  
(1 row(s) affected)
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di configurazione &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [Creazione di una stored procedure](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  
