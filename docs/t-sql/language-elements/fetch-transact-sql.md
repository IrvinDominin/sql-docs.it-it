---
title: FETCH (Transact-SQL) | Microsoft Docs
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
- FETCH
- FETCH_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- cursors [SQL Server], fetching
- Transact-SQL cursors, fetching and scrolling
- retrieving rows
- fetching [SQL Server]
- SCROLL option
- row fetching [SQL Server]
ms.assetid: 5d68dac2-f91b-4342-bb4e-209ee132665f
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: fae1e085c26c2bcbc6b2605187b4554dba414642
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="fetch-transact-sql"></a>FETCH (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Recupera una riga specifica da un cursore server [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FETCH   
          [ [ NEXT | PRIOR | FIRST | LAST   
                    | ABSOLUTE { n | @nvar }   
                    | RELATIVE { n | @nvar }   
               ]   
               FROM   
          ]   
{ { [ GLOBAL ] cursor_name } | @cursor_variable_name }   
[ INTO @variable_name [ ,...n ] ]   
```  
  
## <a name="arguments"></a>Argomenti  
 NEXT  
 Restituisce la riga del set di risultati successiva alla riga corrente e imposta la riga corrente sulla riga restituita. Se FETCH NEXT è la prima operazione di recupero eseguita con un cursore, viene restituita la prima riga del set di risultati. NEXT è l'opzione di recupero predefinita del cursore.  
  
 PRIOR  
 Restituisce la riga del set di risultati precedente alla riga corrente e imposta la riga corrente sulla riga restituita. Se FETCH PRIOR è la prima operazione di recupero eseguita con un cursore, non viene restituita alcuna riga e il cursore rimane nella posizione che precede la prima riga.  
  
 FIRST  
 Restituisce la prima riga nel cursore, che diventa la riga corrente.  
  
 LAST  
 Restituisce l'ultima riga nel cursore, che diventa la riga corrente.  
  
 ASSOLUTO {  *n* | @*nvar*}  
 Se  *n*  o @*nvar* è positivo, restituisce la riga  *n*  righe dall'inizio del cursore e imposta la riga restituita come nuova riga corrente. Se  *n*  o @*nvar* è negativo, restituisce la riga  *n*  righe prima della fine del cursore e imposta la riga restituita come nuova riga corrente. Se  *n*  o @*nvar* è 0, viene restituita alcuna riga. *n*deve essere una costante integer e @*nvar* deve essere **smallint**, **tinyint**, o **int**.  
  
 RELATIVO {  *n* | @*nvar*}  
 Se  *n*  o @*nvar* è positivo, restituisce la riga  *n*  righe successive alla riga corrente e imposta la riga restituita come nuova riga corrente. Se  *n*  o @*nvar* è negativo, restituisce la riga  *n*  righe precedenti alla riga corrente e imposta la riga restituita come nuova riga corrente. Se  *n*  o @*nvar* è 0, restituisce la riga corrente. Se si specifica FETCH RELATIVE con  *n*  o @*nvar* impostato su numeri negativi o su 0 per la prima operazione di recupero eseguita in un cursore, viene restituita alcuna riga. *n*deve essere una costante integer e @*nvar* deve essere **smallint**, **tinyint**, o **int**.  
  
 GLOBAL  
 Specifica che *cursor_name* fa riferimento a un cursore globale.  
  
 *cursor_name*  
 Nome del cursore aperto dal quale deve essere eseguita l'operazione di recupero. Se esiste un globali e un cursore locale con *cursor_name* per il proprio nome, *cursor_name* fino al cursore globale se viene specificato e il cursore locale se non è stato specificato.  
  
 @*cursor_variable_name*  
 Nome di una variabile di cursore che fa riferimento al cursore da cui deve essere eseguita l'operazione di recupero.  
  
 INTO @*nome_variabile*[,... *n*]  
 Consente di inserire in variabili locali i dati delle colonne ottenute da un'operazione di recupero. Ogni variabile dell'elenco, da sinistra a destra, è associata alla colonna corrispondente nel set di risultati del cursore. A ogni variabile deve essere associato lo stesso tipo di dati o un tipo di dati che supporti la conversione implicita dal tipo di dati della colonna corrispondente nel set di risultati. Il numero di variabili deve corrispondere al numero di colonne dell'elenco di selezione del cursore.  
  
## <a name="remarks"></a>Osservazioni  
 Se nell'istruzione ISO DECLARE CURSOR l'opzione SCROLL non è specificata, NEXT è l'unica opzione FETCH supportata. In caso contrario, sono supportate tutte le opzioni FETCH.  
  
 Quando vengono utilizzate le estensioni del cursore DECLARE di [!INCLUDE[tsql](../../includes/tsql-md.md)], vengono applicate le regole seguenti:  
  
-   Se è specificata l'opzione FORWARD-ONLY o FAST_FORWARD, NEXT è l'unica opzione FETCH supportata.  
  
-   Se le opzioni DYNAMIC, FORWARD_ONLY o FAST_FORWARD sono state omesse ed è specificato KEYSET, STATIC o SCROLL, tutte le opzioni FETCH sono supportate.  
  
-   I cursori DYNAMIC SCROLL supportano tutte le opzioni FETCH, ad eccezione di ABSOLUTE.  
  
 Il @@FETCH_STATUS funzione segnala lo stato dell'ultima istruzione FETCH. Le stesse informazioni vengono registrate nella colonna fetch_status del cursore restituito dalla stored procedure sp_describe_cursor. In base a queste informazioni sullo stato, è necessario determinare la validità dei dati restituiti da un'istruzione FETCH prima di eseguire qualsiasi operazione con i dati. Per ulteriori informazioni, vedere [@@FETCH_STATUS &#40; Transact-SQL &#41; ](../../t-sql/functions/fetch-status-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni per l'istruzione FETCH vengono assegnate per impostazione predefinita a qualsiasi utente valido.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-fetch-in-a-simple-cursor"></a>A. Utilizzo dell'istruzione FETCH in un cursore semplice  
 Nell'esempio seguente viene dichiarato un cursore semplice per le righe della tabella `Person.Person` contenenti un cognome che inizia per `B`. Viene inoltre utilizzata l'istruzione `FETCH NEXT` per la riproduzione delle varie righe. Le istruzioni `FETCH` restituiscono il valore delle colonne specificate nell'istruzione `DECLARE CURSOR`, come set di risultati a riga singola.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch.  
FETCH NEXT FROM contact_cursor;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="b-using-fetch-to-store-values-in-variables"></a>B. Utilizzo dell'istruzione FETCH per archiviare valori nelle variabili  
 L'esempio seguente è simile all'esempio A, con la sola differenza che il risultato delle istruzioni `FETCH` viene archiviato in variabili locali anziché essere restituito direttamente al client. L'istruzione `PRINT` combina le variabili in un'unica stringa e le restituisce al client.  
  
```  
USE AdventureWorks2012;  
GO  
-- Declare the variables to store the values returned by FETCH.  
DECLARE @LastName varchar(50), @FirstName varchar(50);  
  
DECLARE contact_cursor CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
WHERE LastName LIKE 'B%'  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Perform the first fetch and store the values in variables.  
-- Note: The variables are in the same order as the columns  
-- in the SELECT statement.   
  
FETCH NEXT FROM contact_cursor  
INTO @LastName, @FirstName;  
  
-- Check @@FETCH_STATUS to see if there are any more rows to fetch.  
WHILE @@FETCH_STATUS = 0  
BEGIN  
  
   -- Concatenate and display the current values in the variables.  
   PRINT 'Contact Name: ' + @FirstName + ' ' +  @LastName  
  
   -- This is executed as long as the previous fetch succeeds.  
   FETCH NEXT FROM contact_cursor  
   INTO @LastName, @FirstName;  
END  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
### <a name="c-declaring-a-scroll-cursor-and-using-the-other-fetch-options"></a>C. Dichiarazione di un cursore SCROLL e utilizzo delle altre opzioni FETCH  
 Nell'esempio seguente viene creato un cursore `SCROLL` per supportare funzioni di scorrimento complete attraverso le opzioni `LAST`, `PRIOR`, `RELATIVE` e `ABSOLUTE`.  
  
```  
USE AdventureWorks2012;  
GO  
-- Execute the SELECT statement alone to show the   
-- full result set that is used by the cursor.  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
-- Declare the cursor.  
DECLARE contact_cursor SCROLL CURSOR FOR  
SELECT LastName, FirstName FROM Person.Person  
ORDER BY LastName, FirstName;  
  
OPEN contact_cursor;  
  
-- Fetch the last row in the cursor.  
FETCH LAST FROM contact_cursor;  
  
-- Fetch the row immediately prior to the current row in the cursor.  
FETCH PRIOR FROM contact_cursor;  
  
-- Fetch the second row in the cursor.  
FETCH ABSOLUTE 2 FROM contact_cursor;  
  
-- Fetch the row that is three rows after the current row.  
FETCH RELATIVE 3 FROM contact_cursor;  
  
-- Fetch the row that is two rows prior to the current row.  
FETCH RELATIVE -2 FROM contact_cursor;  
  
CLOSE contact_cursor;  
DEALLOCATE contact_cursor;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
