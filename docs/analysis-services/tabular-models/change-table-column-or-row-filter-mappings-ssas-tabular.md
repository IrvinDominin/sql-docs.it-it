---
title: Modificare i mapping dei filtri di riga, colonna o tabella | Documenti Microsoft
ms.custom: 
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 361cdea7d72a02c455ccf3f5b6d21255473b937e
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="change-table-column-or-row-filter-mappings"></a>Modificare i mapping di filtri tabella, colonna o riga 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In questo articolo viene descritto come modificare i mapping dei filtri di riga, colonna o tabella utilizzando il **Modifica proprietà tabella** nella finestra di dialogo [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].  
  
 Le opzioni disponibili nella finestra di dialogo **Modifica proprietà tabella** sono diverse, a seconda che i dati siano stati originariamente importati selezionando tabelle da un elenco o usando una query SQL. Se i dati sono stati originariamente importati selezionandoli da un elenco, nella finestra di dialogo **Modifica proprietà tabella** viene visualizzata la modalità Anteprima tabella. Questa modalità consente di visualizzare solo un subset limitato alle prime cinquanta righe della tabella di origine. Se i dati sono stati originariamente importati usando un'istruzione SQL, nella finestra di dialogo **Modifica proprietà tabella** viene visualizzata solo un'istruzione SQL. Utilizzando un'istruzione di query SQL è possibile recuperare un subset di righe progettando un filtro o modificando manualmente l'istruzione SQL.  
  
 Se per l'origine si imposta una tabella con colonne diverse rispetto alla tabella corrente, viene visualizzato un messaggio indicante che le colonne sono diverse. Sarà necessario quindi selezionare le colonne che si desidera inserire nella tabella corrente e fare clic su **Salva**. Selezionando la casella di controllo a sinistra della tabella è possibile sostituire l'intera tabella.  
  
> [!NOTE]  
>  Se nella tabella è presente più di una partizione, non è possibile utilizzare la finestra di dialogo Modifica proprietà tabella per modificare i mapping del filtro di riga. Per modificare i mapping del filtro di riga per le tabelle con più partizioni, utilizzare Gestione partizioni. Per ulteriori informazioni, vedere [partizioni](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-change-table-column-or-row-filter-mappings"></a>Per modificare i mapping dei filtri tabella, colonna o riga  
  
1.  In Progettazione modelli fare clic su una tabella e quindi scegliere **Proprietà tabella** dal menu **Tabella**.  
  
2.  Nella finestra di dialogo **Modifica proprietà tabella** individuare la colonna in cui sono contenuti i criteri in base ai quali si vuole filtrare e quindi fare clic sulla freccia GIÙ a destra dell'intestazione di colonna.  
  
3.  Nel menu **Filtro automatico** effettuare uno dei passaggi seguenti:  
  
    -   Nell'elenco di valori delle colonne selezionare o deselezionare uno o più valori da utilizzare come filtri, quindi fare clic su OK.  
  
         Se il numero di valori è estremamente elevato, singoli elementi potrebbero non essere visualizzati nell'elenco. Verrà invece visualizzato il messaggio, "Troppi elementi da visualizzare".  
  
    -   Fare clic su **Filtri per numeri** o su **Filtri per testo** (a seconda del tipo di colonna) e quindi fare clic su uno dei comandi di operatore di confronto (ad esempio Uguale a) o su Filtro personalizzato. Nella finestra di dialogo **Filtro personalizzato** creare il filtro, quindi fare clic su **OK**.  
  
         Se si commette un errore ed è necessario ricominciare, fare clic su **Cancella filtri di riga**.  
  
  
  
