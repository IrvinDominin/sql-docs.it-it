---
title: '@@FETCH_STATUS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 353d6e64d11a7365689b5f57aaab3b5ba93de690
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703069"
---
# <a name="x40x40fetchstatus-transact-sql"></a>&#x40;&#x40;FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce lo stato dell'ultima istruzione FETCH eseguita su qualsiasi cursore attualmente aperto dalla connessione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>Tipo restituito  
 **integer**  
  
## <a name="return-value"></a>Valore restituito  
  
|Valore restituito|Descrizione|  
|------------------|-----------------|  
|&nbsp;0|L'istruzione FETCH ha avuto esito positivo.|  
|-1|L'istruzione FETCH ha avuto esito negativo oppure la riga non è compresa nel set di risultati.|  
|-2|La riga recuperata è mancante.|
|-9|Il cursore non sta eseguendo un'operazione di recupero.|  
  
## <a name="remarks"></a>Remarks  
Dato che `@@FETCH_STATUS` è globale per tutti i cursori di una connessione, usare questa funzione con attenzione. Dopo l'esecuzione di un'istruzione FETCH, è necessario eseguire il test di `@@FETCH_STATUS` prima di eseguire qualsiasi altra istruzione FETCH su un altro cursore. Il valore di `@@FETCH_STATUS` viene definito solo dopo l'esecuzione di operazioni di recupero sulla connessione.  
  
Un utente, ad esempio, può eseguire un'istruzione FETCH da un cursore e chiamare quindi una stored procedure che apre ed elabora i risultati da un altro cursore. Quando la stored procedure chiamata restituisce il controllo, in `@@FETCH_STATUS` è riportato il risultato dell'ultima istruzione FETCH eseguita nella stored procedure, non dell'istruzione FETCH eseguita prima della chiamata della stored procedure.  
  
Per recuperare l'ultimo stato di un cursore specifico, eseguire una query nella colonna **fetch_status** della DMF **sys.dm_exec_cursors**.  
  
## <a name="examples"></a>Esempi  
Questo esempio usa `@@FETCH_STATUS` per controllare le attività del cursore in un ciclo `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni per i cursori &#40;Transact-SQL&#41;](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  
