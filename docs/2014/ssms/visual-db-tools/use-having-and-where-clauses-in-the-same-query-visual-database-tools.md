---
title: Usare clausole HAVING e in cui nella stessa Query (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- search criteria [SQL Server], WHERE clause
- search conditions [SQL Server], HAVING clause
- row excluded in search [SQL Server]
- search criteria [SQL Server], HAVING clause
- HAVING clause, search criteria
- search conditions [SQL Server], WHERE clause
- WHERE clause, search criteria
- excluding rows
ms.assetid: 1e07cf56-b4b7-4c49-8ddd-c276812a7148
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57b266d8b5e825e784a74e25e5801b7bd9f0cc22
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221921"
---
# <a name="use-having-and-where-clauses-in-the-same-query-visual-database-tools"></a>Utilizzo delle clausole HAVING e WHERE nella stessa query (Visual Database Tools)
  In alcuni casi può essere necessario escludere singole righe dai gruppi (utilizzando una clausola WHERE) prima di applicare una condizione ai gruppi (utilizzando una clausola HAVING).  
  
 La clausola HAVING è analoga alla clausola WHERE ma è applicabile solo ai gruppi come insieme, ossia alle righe nel set di risultati che rappresentano i gruppi, mentre la clausola WHERE è applicabile a righe singole. Una query può contenere sia una clausola WHERE che una clausola HAVING. In questo caso:  
  
-   La clausola WHERE viene applicata prima alle singole righe nelle tabelle o negli oggetti con valori di tabella nel riquadro Diagramma. Vengono raggruppate solo le righe che soddisfano le condizioni della clausola WHERE.  
  
-   Successivamente viene applicata la clausola HAVING alle righe del set di risultati. Nell'output della query saranno visualizzati solo i gruppi che soddisfano le condizioni HAVING. La clausola HAVING può essere applicata solo alle colonne presenti anche nella clausola GROUP BY o in una funzione di aggregazione.  
  
 Si supponga ad esempio di unire le tabelle `titles` e `publishers` per creare una query in cui sia visualizzato il prezzo medio dei libri per un set di editori, limitando la ricerca a un set specifico di editori, ad esempio quelli dello stato della California, e a un prezzo medio maggiore di 10 dollari.  
  
 In questo caso, prima di calcolare il prezzo medio è possibile stabilire la prima condizione con una clausola WHERE che escluda tutti gli editori che non si trovano in California. La seconda condizione richiede una clausola HAVING, in quanto la condizione è basata sui risultati del raggruppamento e del riepilogo di dati. L'istruzione SQL risultante sarà analoga alla seguente:  
  
```  
SELECT titles.pub_id, AVG(titles.price)  
FROM titles INNER JOIN publishers  
   ON titles.pub_id = publishers.pub_id  
WHERE publishers.state = 'CA'  
GROUP BY titles.pub_id  
HAVING AVG(price) > 10  
```  
  
 È possibile creare sia clausole HAVING che clausole WHERE nel riquadro Criteri. In base all'impostazione predefinita, se si specifica una condizione di ricerca per una colonna, tale condizione entrerà a far parte della clausola HAVING, ma sarà comunque possibile cambiarla in una clausola.  
  
 È possibile creare una clausola WHERE e una clausola HAVING relative alla stessa colonna. A tale scopo, è necessario aggiungere due volte la colonna nel riquadro Criteri, quindi assegnare un'istanza alla clausola HAVING e l'altra alla clausola WHERE.  
  
### <a name="to-specify-a-where-condition-in-an-aggregate-query"></a>Per specificare una condizione WHERE in una query di aggregazione  
  
1.  Specificare i gruppi per la query. Per informazioni dettagliate, vedere [Raggruppare righe nei risultati di una query &#40;Visual Database Tools&#41;](visual-database-tools.md).  
  
2.  Se necessario, aggiungere nel riquadro Criteri la colonna su cui si desidera basare la condizione WHERE.  
  
3.  Se la colonna di dati non è inclusa nella clausola GROUP BY o nella funzione di aggregazione, eliminare il contenuto della colonna **Output** .  
  
4.  Nella colonna **Filtro** specificare la condizione WHERE. La condizione verrà aggiunta alla clausola HAVING dell'istruzione SQL.  
  
    > [!NOTE]  
    >  Nella query illustrata nell'esempio della procedura vengono unite due tabelle: `titles` e `publishers`.  
  
     A questo punto della creazione della query, l'istruzione SQL contiene una clausola HAVING:  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    GROUP BY titles.pub_id  
    HAVING publishers.state = 'CA'  
    ```  
  
5.  Selezionare **Where** dall'elenco di opzioni di raggruppamento e riepilogo nella colonna **Group By** . La condizione verrà rimossa dalla clausola HAVING dell'istruzione SQL e aggiunta alla clausola WHERE.  
  
     L'istruzione SQL includerà ora una clausola WHERE:  
  
    ```  
    SELECT titles.pub_id, AVG(titles.price)  
    FROM titles INNER JOIN publishers   
       ON titles.pub_id = publishers.pub_id  
    WHERE publishers.state = 'CA'  
    GROUP BY titles.pub_id  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Ordina e raggruppa i risultati della Query &#40;Visual Database Tools&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Creare un riepilogo dei risultati di query &#40;Visual Database Tools&#41;](summarize-query-results-visual-database-tools.md)  
  
  
