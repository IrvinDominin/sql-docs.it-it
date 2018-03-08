---
title: La lettura dei dati in una tabella (esercitazione) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- reading data in a table
ms.assetid: 532232c9-3d41-45cd-9150-de67a1cbfcf5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 37d35412e052c6b47ef08ece1f861fcd3c44b88e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="lesson-1-4---reading-the-data-in-a-table"></a>Lezione 1-4-la lettura dei dati in una tabella
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]Utilizzare l'istruzione SELECT per leggere i dati in una tabella. L'istruzione SELECT è una delle più importanti istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] e la relativa sintassi presenta numerose variazioni. Ai fini di questa esercitazione ne verranno utilizzate cinque semplici versioni.  
  
### <a name="to-read-the-data-in-a-table"></a>Per leggere i dati archiviati in una tabella  
  
1.  Per leggere i dati archiviati nella tabella `Products` , digitare ed eseguire le istruzioni seguenti.  
  
    ```  
    -- The basic syntax for reading data from a single table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
    GO  
  
    ```  
  
2.  È possibile utilizzare un asterisco per selezionare tutte le colonne della tabella. Si tratta di una tecnica utilizzata spesso nelle query ad hoc. È consigliabile specificare l'elenco delle colonne nel codice permanente in modo che l'istruzione restituisca le colonne previste anche se viene successivamente aggiunta una nuova colonna alla tabella.  
  
    ```  
    -- Returns all columns in the table  
    -- Does not use the optional schema, dbo  
    SELECT * FROM Products  
    GO  
  
    ```  
  
3.  È possibile omettere le colonne che non si desidera vengano restituite. Le colonne verranno restituite nell'ordine specificato.  
  
    ```  
    -- Returns only two of the columns from the table  
    SELECT ProductName, Price  
        FROM dbo.Products  
    GO  
  
    ```  
  
4.  Utilizzare una clausola `WHERE` per limitare le righe restituite.  
  
    ```  
    -- Returns only two of the records in the table  
    SELECT ProductID, ProductName, Price, ProductDescription  
        FROM dbo.Products  
        WHERE ProductID < 60  
    GO  
  
    ```  
  
5.  È possibile utilizzare i valori nelle colonne quando vengono restituiti. L'esempio seguente esegue un'operazione matematica sulla colonna `Price` . Alle colonne modificate in questo modo non verrà assegnato un nome a meno che non se ne specifichi uno utilizzando la parola chiave `AS` .  
  
    ```  
    -- Returns ProductName and the Price including a 7% tax  
    -- Provides the name CustomerPays for the calculated column  
    SELECT ProductName, Price * 1.07 AS CustomerPays  
        FROM dbo.Products  
    GO  
    ```  
  
## <a name="functions-that-are-useful-in-a-select-statement"></a>Funzioni utili in un'istruzione SELECT  
Per informazioni su alcune funzioni che consentono di utilizzare i dati in un'istruzione SELECT, vedere gli argomenti seguenti:  
  
|||  
|-|-|  
|[Funzioni stringa &#40;Transact-SQL&#41;](../t-sql/functions/string-functions-transact-sql.md)|[Funzioni e tipi di dati di data e ora &#40;Transact-SQL&#41;](../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)|  
|[Funzioni matematiche &#40;Transact-SQL&#41;](../t-sql/functions/mathematical-functions-transact-sql.md)|[Funzioni per i valori text e image &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)|  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Riepilogo: Creazione di oggetti di database](../t-sql/lesson-1-5-summary-creating-database-objects.md)  
  
## <a name="see-also"></a>Vedere anche  
[SELECT &#40;Transact-SQL&#41;](../t-sql/queries/select-transact-sql.md)  
  
  
  
