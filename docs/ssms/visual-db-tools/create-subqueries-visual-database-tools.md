---
title: Creare sottoquery (Visual Database Tools) | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2f91c21726e659bd7a66456566d29dbf77369d2
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="create-subqueries-visual-database-tools"></a>Creazione di sottoquery (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] È possibile usare i risultati di una query come input per un'altra. I risultati di una sottoquery possono essere usati come istruzione che usa la funzione IN( ), l'operatore EXISTS o la clausola FROM.  
  
Per creare una sottoquery, immetterla direttamente nel riquadro SQL oppure copiare una query e incollarla in un'altra query.  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a>Per definire una sottoquery nel riquadro SQL  
  
1.  Creare la query primaria.  
  
2.  Selezionare l'istruzione SQL nel riquadro SQL e usare il comando **Copia** per copiare la query negli Appunti.  
  
3.  Iniziare la nuova query e usare il comando **Incolla** per spostare la prima query nella clausola WHERE o FROM della nuova query.  
  
    Si supponga ad esempio di disporre di due tabelle, `products` e `suppliers`, e di creare una query che mostri tutti i prodotti dei fornitori in Svezia. Creare la prima query sulla tabella `suppliers` per individuare tutti i fornitori svedesi:  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
    Utilizzare il comando Copia per copiare la query negli Appunti. Creare la seconda query utilizzando la tabella `products` , in cui sono elencate tutte le informazioni necessarie sui prodotti:  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
    Nel riquadro SQL aggiungere una clausola WHERE alla seconda query, quindi incollare la prima query dagli Appunti. Racchiudere fra parentesi la prima query, in modo da ottenere un risultato analogo al seguente:  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a>Vedere anche  
[Tipi di query supportati &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Specifica dei criteri di ricerca &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
