---
title: Punti dati vuoti e Null nei grafici (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: faddd29d-4cc1-4c2c-8e29-d3d9918fe22a
caps.latest.revision: "10"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 627e71fcbd48a533a61abbbf29f4db20c2f5d6e3
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="empty-and-null-data-points-in-charts-report-builder-and-ssrs"></a>Punti dati vuoti e Null nei grafici (Generatore report e SSRS)

  Quando si visualizzano campi con valori vuoti o Null nel grafico, è possibile che il grafico impaginato di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] non presenti l'aspetto previsto. I valori vuoti vengono elaborati in modo diverso a seconda del tipo di grafico specificato:  
  
-   Se il grafico è di tipo lineare (grafico a barre, a dispersione, a linee, ad area, con intervalli o istogramma) i valori vuoti vengono visualizzati come spazi vuoti o "gap". Se si desidera identificare i punti vuoti, è necessario aggiungere segnaposti di punti vuoti. Per altre informazioni, vedere [Aggiungere punti vuoti a un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   Se il grafico è di tipo lineare contiguo (ad area, a barre, a linee, a dispersione o istogramma), vengono aggiunti punti dati vuoti per mantenere la continuità nella serie.  
  
-   Se il grafico è di tipo non lineare (polare, a torta, ad anello, a imbuto o a piramide), i valori vuoti non vengono visualizzati.  
  
-   Nei tipi di grafico con forme i valori Null vengono omessi.  
  
 Un esempio di grafico con punti dati vuoti è disponibile come report di esempio. Per altre informazioni sul download di questo e di altri report di esempio, vedere la pagina relativa ai [report di esempio per Generatore report e Progettazione report](http://go.microsoft.com/fwlink/?LinkId=198283).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="removing-empty-or-null-values"></a>Rimozione di valori vuoti o Null  
 Per evitare che dati importanti risultino nascosti, rimuovere i valori vuoti dal set di dati. Per filtrare i valori Null, è possibile usare la clausola NOT IS NULL nella query. In alternativa, è possibile aggiungere un'espressione di filtro per specificare che si desidera visualizzare solo i valori diversi da zero. Per altre informazioni, vedere [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md).  
  
## <a name="fields-with-no-values-in-a-chart"></a>Campi senza valori in un grafico  
 Se un campo non contiene valori nel set di dati restituito, verrà visualizzato un grafico vuoto senza punti dati, ma con l'aggiunta del nome della serie (solitamente il nome del campo) come elemento della legenda.  
  
 Questo comportamento è diverso dal caso in cui il set di dati restituito non contiene alcuna riga di dati, che può verificarsi quando il report include parametri e il valore selezionato restituisce un set di risultati vuoto. Se la query del set di dati non restituisce alcuna riga di dati, in fase di esecuzione verrà visualizzato un messaggio indicante che non è possibile visualizzare dati. È possibile personalizzare questo messaggio modificando la didascalia NoDataMessage per il report nel riquadro **Proprietà** . Per altre informazioni, vedere [Set di dati condivisi e incorporati del report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  

## <a name="next-steps"></a>Passaggi successivi

[Grafici](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
[Formattazione di un grafico](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
[Aggiungere un grafico a un report](../../reporting-services/report-design/add-a-chart-to-a-report-report-builder-and-ssrs.md)   
[Risolvere i problemi relativi ai grafici](../../reporting-services/report-design/troubleshoot-charts-report-builder-and-ssrs.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
