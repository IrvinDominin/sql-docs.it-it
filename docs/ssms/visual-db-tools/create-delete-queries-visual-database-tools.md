---
title: Creare query di eliminazione (Visual Database Tools) | Microsoft Docs
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
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1538fed172283d64b2c8d5154162cf457436a476
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="create-delete-queries-visual-database-tools"></a>Creazione di query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Per eliminare tutte le righe di una tabella, è possibile usare una query di eliminazione.  
  
> [!NOTE]  
> Se si eliminano tutte le righe di una tabella, non verrà eliminata la tabella, ma solo i dati in essa contenuti. Per eliminare una tabella da un database, fare clic su di essa con il pulsante destro del mouse in Esplora oggetti, quindi scegliere **Elimina**.  
  
Quando si crea una query di eliminazione, nel riquadro Criteri vengono visualizzate le opzioni disponibili per l'eliminazione delle righe. Poiché la query di eliminazione non consente la visualizzazione di dati, vengono eliminate le colonne Output, Ordina per e Ordinamento. Vengono inoltre rimosse le caselle di controllo accanto ai nomi di colonna nel rettangolo che rappresenta la tabella o l'oggetto con valori di tabella, in quanto non è possibile specificare singole colonne da eliminare.  
  
Se in Progettazione query e Progettazione viste non è possibile eliminare una o più righe, non ne verrà eliminata alcuna e un messaggio indicherà in quali righe sono contenute informazioni che non possono essere eliminate dal database.  
  
> [!CAUTION]  
> Una volta eseguita, la query di eliminazione non potrà essere annullata. È dunque opportuno eseguire una copia di backup dei dati prima di eseguire la query di eliminazione.  
  
### <a name="to-create-a-delete-query"></a>Per creare una query di eliminazione  
  
1.  Aggiungere al riquadro Diagramma la tabella da cui eliminare le righe.  
  
2.  Scegliere **Modifica tipo** dal menu **Progettazione query**, quindi **Elimina**. **Nota** Se nel riquadro Diagramma sono visualizzate più tabelle quando si inizia a creare la query di eliminazione, in Progettazione query e Progettazione viste verrà visualizzata la finestra di dialogo [Elimina tabella](../../ssms/visual-db-tools/delete-table-dialog-box-visual-database-tools.md) , in cui è necessario specificare il nome della tabella contenente le righe da eliminare.  
  
Quando si esegue una query di eliminazione, non viene restituito alcun risultato nel [riquadro Risultati](../../ssms/visual-db-tools/results-pane-visual-database-tools.md). Viene invece visualizzato un messaggio che indica il numero di righe eliminate.  
  
## <a name="see-also"></a>Vedere anche  
[Tipi di query supportati &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
