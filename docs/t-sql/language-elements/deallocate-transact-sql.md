---
title: DEALLOCATE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DEALLOCATE
- DEALLOCATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], cursors
- DEALLOCATE statement
- deallocations [SQL Server]
- deleting cursor references
- removing cursor references
ms.assetid: c75cf73d-0268-4c57-973d-b8a84ff801fa
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fb05fdd9da2f4f724976092bf027f5dde5edd412
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="deallocate-transact-sql"></a>DEALLOCATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove un riferimento a un cursore. Quando l'ultimo riferimento al cursore viene deallocato, le strutture di dati che includono il cursore vengono rilasciate da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DEALLOCATE { { [ GLOBAL ] cursor_name } | @cursor_variable_name }  
```  
  
## <a name="arguments"></a>Argomenti  
 *cursor_name*  
 Nome di un cursore già dichiarato. Se esiste un globali e un cursore locale con *cursor_name* per il proprio nome, *cursor_name* fa riferimento il cursore globale se viene specificato e il cursore locale se non è stato specificato.  
  
 @*cursor_variable_name*  
 È il nome di un **cursore** variabile. @*cursor_variable_name* deve essere di tipo **cursore**.  
  
## <a name="remarks"></a>Osservazioni  
 Le istruzioni che hanno effetto sui cursori utilizzano un nome di cursore o una variabile di cursore per fare riferimento al cursore. L'istruzione DEALLOCATE elimina l'associazione tra un cursore e il nome di cursore o la variabile di cursore. Se il nome o la variabile è l'ultimo riferimento al cursore, il cursore viene deallocato e le risorse da esso utilizzate vengono rilasciate. I blocchi di scorrimento utilizzati per proteggere l'isolamento delle operazioni di recupero vengono rilasciati dall'istruzione DEALLOCATE. I blocchi a livello di transazione utilizzati per proteggere gli aggiornamenti, inclusi gli aggiornamenti posizionati eseguiti con il cursore, vengono mantenuti attivi fino al termine della transazione.  
  
 L'istruzione DECLARE CURSOR consente di allocare un cursore e di associarlo a un nome di cursore.  
  
```  
DECLARE abc SCROLL CURSOR FOR  
SELECT * FROM Person.Person;  
```  
  
 Il nome associato a un cursore potrà essere utilizzato per un altro cursore dello stesso ambito (GLOBAL o LOCAL) solo dopo la deallocazione del primo cursore.  
  
 Una variabile di cursore può essere associata a un cursore in uno dei due modi seguenti:  
  
-   È possibile specificarne il nome, utilizzando un'istruzione SET che associa un cursore a una variabile di cursore.  
  
    ```  
    DECLARE @MyCrsrRef CURSOR;  
    SET @MyCrsrRef = abc;  
    ```  
  
-   È possibile creare un cursore e associarlo a una variabile senza utilizzare una precedente definizione di nome di cursore.  
  
    ```  
    DECLARE @MyCursor CURSOR;  
    SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Person.Person;  
    ```  
  
 Un'istruzione DEALLOCATE @*cursor_variable_name* istruzione rimuove solo il riferimento della variabile denominata fino al cursore. La variabile verrà deallocata solo quando non sarà più compresa nell'ambito al termine dell'esecuzione del batch, della stored procedure o del trigger. Dopo un'istruzione DEALLOCATE @*cursor_variable_name* istruzione, la variabile può essere associata a un altro cursore tramite l'istruzione SET.  
  
```  
USE AdventureWorks2012;  
GO  
  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
  
DEALLOCATE @MyCursor;  
  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
    SELECT * FROM Sales.SalesTerritory;  
GO  
```  
  
 Non è necessario deallocare una variabile di cursore in modo esplicito. La variabile viene deallocata in modo implicito quando non è più compresa nell'ambito.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni DEALLOCATE vengono assegnate per impostazione predefinita a qualsiasi utente valido.  
  
## <a name="examples"></a>Esempi  
 Nello script seguente viene illustrato come i cursori sono persistenti fino alla deallocazione dell'ultimo nome o dell'ultima variabile in cui vi viene fatto riferimento.  
  
```  
USE AdventureWorks2012;  
GO  
-- Create and open a global named cursor that  
-- is visible outside the batch.  
DECLARE abc CURSOR GLOBAL SCROLL FOR  
    SELECT * FROM Sales.SalesPerson;  
OPEN abc;  
GO  
-- Reference the named cursor with a cursor variable.  
DECLARE @MyCrsrRef1 CURSOR;  
SET @MyCrsrRef1 = abc;  
-- Now deallocate the cursor reference.  
DEALLOCATE @MyCrsrRef1;  
-- Cursor abc still exists.  
FETCH NEXT FROM abc;  
GO  
-- Reference the named cursor again.  
DECLARE @MyCrsrRef2 CURSOR;  
SET @MyCrsrRef2 = abc;  
-- Now deallocate cursor name abc.  
DEALLOCATE abc;  
-- Cursor still exists, referenced by @MyCrsrRef2.  
FETCH NEXT FROM @MyCrsrRef2;  
-- Cursor finally is deallocated when last referencing  
-- variable goes out of scope at the end of the batch.  
GO  
-- Create an unnamed cursor.  
DECLARE @MyCursor CURSOR;  
SET @MyCursor = CURSOR LOCAL SCROLL FOR  
SELECT * FROM Sales.SalesTerritory;  
-- The following statement deallocates the cursor  
-- because no other variables reference it.  
DEALLOCATE @MyCursor;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [Cursori](../../relational-databases/cursors.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
