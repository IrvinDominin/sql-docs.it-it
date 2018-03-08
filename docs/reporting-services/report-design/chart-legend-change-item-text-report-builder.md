---
title: Modificare il testo di un elemento legenda (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e82fa34-17ed-494f-b25d-03dcc353a21f
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 9e5b23ce9d8055822fc4d32fb4be5794e7ecf3b1
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="chart-legend---change-item-text-report-builder"></a>Legenda del grafico - Modificare il testo degli elementi (Generatore report)
  Quando un campo viene posizionato nell'area Valori del grafico, viene generato automaticamente un elemento della legenda contenente il nome di tale campo. Ogni elemento della legenda è collegato a una singola serie nel grafico, ad eccezione dei grafici con forme in cui la legenda è collegata a singoli punti dati anziché a singole serie.  
  
 Nei grafici con forme è possibile modificare il testo di un elemento della legenda in modo da visualizzare ulteriori informazioni sui singoli punti dati. Per visualizzare i valori dei punti dati come percentuali nella legenda, ad esempio, è possibile usare una parola chiave quale **#PERCENT**. Per applicare formati numerici e di data, è possibile aggiungere codici di formato .NET Framework con determinate parole chiave. Per altre informazioni sulle parole chiave, vedere [Formattazione dei punti dati di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
 ![Grafico ottimizzato](../../reporting-services/report-design/media/sharpchart.png "Grafico ottimizzato")  
  
 Nei grafici senza forme è possibile modificare il testo di un elemento della legenda. Se, ad esempio, il nome della serie è "Serie 1", è possibile modificare il testo per renderlo più descrittivo, ad esempio "Vendite anno 2008".  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-shape-chart"></a>Per modificare il testo visualizzato nella legenda in un grafico con forme  
  
1.  Fare clic con il pulsante destro del mouse su una serie o su un campo contenuto nell'area **Valori** e quindi selezionare **Proprietà serie**.  
  
2.  Fare clic su **Legenda** e digitare una parola chiave nella casella **Testo legenda personalizzato** .  
  
 La tabella seguente include esempi di parole chiave specifiche del grafico da usare per la proprietà **Testo legenda personalizzato** . Per altre informazioni sulle parole chiave, vedere [Formattazione dei punti dati di un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md).  
  
|Parola chiave|Description|Esempio di testo visualizzato nella legenda|  
|-------------|-----------------|---------------------------------------------------|  
|`#PERCENT{P1}`|Visualizza la percentuale del valore totale con una posizione decimale.|85.0%|  
|`#VALY`|Visualizza il valore numerico effettivo del campo dati.|17000|  
|`#VALY{C2}`|Visualizza il valore numerico effettivo del campo dati come valuta con due posizioni decimali.|$17000.00|  
|`#AXISLABEL (#PERCENT{P0})`|Visualizza la rappresentazione testuale del campo categoria, seguita dalla percentuale visualizzata da ogni categoria nel grafico.|Michael Blythe (85%)|  
  
> [!NOTE]  
>  La parola chiave #AXISLABEL può essere valutata solo in fase di esecuzione quando non è specificato alcun campo nell'area **Gruppi di serie** .  
  
### <a name="to-modify-the-text-that-appears-in-the-legend-on-a-non-shape-chart"></a>Per modificare il testo visualizzato nella legenda in un grafico senza forme  
  
1.  Fare clic con il pulsante destro del mouse su una serie o su un campo contenuto nell'area **Valori** e quindi selezionare **Proprietà serie**.  
  
2.  Fare clic su **Legenda** e digitare un'etichetta di legenda nella casella **Testo legenda personalizzato** . La serie verrà aggiornata con il testo specificato.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione della legenda in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Formattazione dei colori delle serie in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Nascondere elementi legenda nel grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/chart-legend-hide-items-report-builder.md)  
  
  
