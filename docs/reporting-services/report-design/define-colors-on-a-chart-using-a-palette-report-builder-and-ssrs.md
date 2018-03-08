---
title: Definire i colori in un grafico mediante la tavolozza (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d95efc22-5a32-43d4-9bd2-12753e7fd395
caps.latest.revision: "6"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 97e3ca3df260a3c2e09a12ae920a96be0154191c
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="define-colors-on-a-chart-using-a-palette-report-builder-and-ssrs"></a>Definire i colori in un grafico mediante la tavolozza (Generatore report e SSRS)
  È possibile modificare la tavolozza colori per un grafico selezionando una tavolozza predefinita o definendo una tavolozza personalizzata. Le tavolozze personalizzate sono specifiche dei report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-colors-on-the-chart-using-a-built-in-color-palette"></a>Per modificare i colori nel grafico utilizzando una tavolozza colori predefinita  
  
1.  Aprire il riquadro Proprietà.  
  
2.  Nell'area di progettazione fare clic sul grafico. Le proprietà dell'oggetto grafico verranno visualizzate nel riquadro Proprietà.  
  
     Il nome dell'oggetto (**Chart1** per impostazione predefinita) viene visualizzato nell'elenco a discesa nella parte superiore del riquadro Proprietà.  
  
3.  Nella sezione **Grafico** selezionare nell'elenco a discesa una nuova tavolozza per la proprietà Palette.  
  
    > [!NOTE]  
    >  Una tavolozza predefinita non consente di modificare o di ordinare i colori.  
  
### <a name="to-define-your-own-colors-on-the-chart-using-a-custom-color-palette"></a>Per definire colori personalizzati nel grafico utilizzando una tavolozza colori personalizzata  
  
1.  Aprire il riquadro Proprietà.  
  
2.  Nell'area di progettazione fare clic sul grafico. Le proprietà dell'oggetto grafico verranno visualizzate nel riquadro Proprietà.  
  
3.  Nella sezione **Grafico** selezionare **Personalizzata** per la proprietà **Tavolozza**.  
  
4.  Nella proprietà CustomPaletteColors fare clic sul pulsante Modifica raccolta (**…**). Verrà visualizzata la finestra di dialogo **Editor raccolte ReportColorExpression** .  
  
5.  Fare clic su **Aggiungi** per aggiungere un colore. Selezionare un colore dall'elenco a discesa oppure selezionare Espressione e specificare un valore esadecimale per un colore specifico, ad esempio ff6600 per l'arancione.  
  
     Per ulteriori informazioni sui valori esadecimali, vedere la [tabella dei colori](http://go.microsoft.com/fwlink/?linkid=9258) su MSDN.  
  
6.  Fare clic su **Aggiungi** per aggiungere altri colori alla tavolozza.  
  
7.  Al termine dell'operazione scegliere **OK**.  
  
 Se si utilizza una tavolozza personalizzata, è possibile modificare l'ordine dei colori per modificare il colore di diverse serie nel grafico.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione dei colori delle serie in un grafico &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Specificare i colori coerenti in più grafici con forme &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/specify-consistent-colors-across-multiple-shape-charts-report-builder-and-ssrs.md)  
  
  
