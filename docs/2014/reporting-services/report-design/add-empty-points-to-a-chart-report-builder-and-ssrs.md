---
title: Aggiunta di punti vuoti al grafico (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b056119-439f-494f-83cf-ee0c05dc6487
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 942da7aa8b4db6e6f54b80f941856185bc03758d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36168016"
---
# <a name="add-empty-points-to-the-chart-report-builder-and-ssrs"></a>Aggiunta di punti vuoti al grafico (Generatore report e SSRS)
  Nel grafico i valori Null vengono visualizzati come spazi o intervalli vuoti tra punti dati in una serie. I punti vuoti sono punti dati che possono essere inseriti nello spazio vuoto creato dai valori Null.  
  
 Per impostazione predefinita i punti vuoti vengono calcolati considerando la media tra il punto dati precedente e quello successivo che contiene un valore. È possibile modificare questa situazione in modo che tutti i punti vuoti vengano inseriti nella posizione zero.  
  
 Per altre informazioni, vedere [Punti dati vuoti e Null nei grafici &#40;Generatore report e SSRS&#41;](charts-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-empty-points-on-a-chart"></a>Per specificare punti vuoti in un grafico  
  
1.  Aprire il riquadro Proprietà.  
  
2.  Nell'area di progettazione fare clic con il pulsante destro del mouse sulla serie che contiene valori Null. Le proprietà della serie verranno visualizzate nel riquadro Proprietà.  
  
3.  Espandere il nodo **EmptyPoint** .  
  
4.  Selezionare un valore del colore per la proprietà Color.  
  
5.  Nel nodo **EmptyPoint** espandere il nodo Marker.  
  
6.  Selezionare un tipo di marcatore per la proprietà MarkerType.  
  
    > [!NOTE]  
    >  È necessario selezionare un tipo di marcatore per aggiungere punti vuoti a una barra, a una colonna oppure a un grafico a dispersione. Per i grafici ad area, a linee e radar, tuttavia, la selezione di un tipo di marcatore è facoltativa poiché nel grafico lo spazio vuoto o l'intervallo viene riempito senza che sia necessario specificare un marcatore.  
  
7.  Impostare il valore del punto vuoto.  
  
    1.  Nel riquadro Proprietà espandere il nodo **CustomAttributes** .  
  
    2.  Impostare la proprietà EmptyPointValue. Per inserire punti vuoti in una posizione relativa alla media dei punti dati precedente e successivo, selezionare **Media**. Per inserire punti vuoti nella posizione zero, selezionare **Zero**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Tipi di grafico &#40;Generatore report e SSRS&#41;](chart-types-report-builder-and-ssrs.md)   
 [Aggiungere cambi di scala a un grafico &#40;Generatore report e SSRS&#41;](add-scale-breaks-to-a-chart-report-builder-and-ssrs.md)   
 [Grafici &#40;SSRS e Generatore Report&#41;](charts-report-builder-and-ssrs.md)  
  
  