---
title: Visualizzare la Formula per una serie temporale (Data Mining) modello | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7dc0ec5be4d6a0189e844ddfa24595b0cadade24
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>Visualizzare la formula per un modello Time Series (Data Mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Se è stato creato un modello Time Series con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Data Mining, il modo più semplice per visualizzare l'equazione di regressione per il modello è usare la **Legenda data mining** del [Visualizzatore Microsoft Time Series](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md), che presenta tutte le costanti in un formato leggibile.  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>Per visualizzare la formula di regressione ARTXP per un modello Time Series  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]selezionare il modello Time Series da visualizzare e fare clic su **Sfoglia**.  
  
     -oppure-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare il modello Time Series e fare clic sulla scheda **Visualizzatore modello di data mining** .  
  
2.  Fare clic sulla scheda **Modello** .  
  
3.  Se il modello contiene più alberi, selezionare un solo albero nell'elenco a discesa **Albero** .  
  
    > [!NOTE]  
    >  In presenza di più serie di dati un modello presenta sempre più alberi. Tuttavia, il numero di alberi visualizzati nel **Visualizzatore Time Series** non sarà uguale a quello degli alberi visualizzati in [Microsoft Generic Content Tree Viewer](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c), in quanto nel primo caso le informazioni ARIMA e ARTXP di ogni serie di dati vengono combinate in una sola rappresentazione.  
  
4.  Fare clic su un nodo foglia dell'albero.  
  
     I nodi identificati come **Serie di dati** sono sempre nodi foglia e possono contenere un'equazione. Se un nodo **(Tutto)** non presenta nodi figlio, può contenere anch'esso un'equazione.  
  
5.  Se **Legenda data mining** non è disponibile, fare clic con il pulsante destro del mouse sul nodo e scegliere **Mostra legenda**.  
  
     La formula ARTXP viene visualizzata nella prima metà di **Legenda data mining**come **Equazione nodo dell'albero**.  
  
     ![visualizzazione della formula time series nella legenda](../../analysis-services/data-mining/media/ssdm-timeserieslegend.png "visualizzazione della formula time series nella legenda")  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>Per visualizzare la formula ARIMA per un modello Time Series  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]selezionare il modello Time Series da visualizzare e fare clic su **Sfoglia**.  
  
     -oppure-  
  
     In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]selezionare il modello Time Series e fare clic sulla scheda **Visualizzatore modello di data mining** .  
  
2.  Fare clic sulla scheda **Modello** .  
  
3.  Se il modello contiene più alberi, selezionare un solo albero nell'elenco a discesa **Albero** .  
  
    > [!NOTE]  
    >  Se vengono incluse più serie di dati, il modello presenta sempre più alberi.  
  
4.  Fare clic su un nodo dell'albero.  
  
     La formula ARIMA viene visualizzata nella seconda metà di **Legenda data mining**come **Equazione ARIMA**.  
  
5.  Se **Legenda data mining** non è disponibile, fare clic con il pulsante destro del mouse sul nodo e scegliere **Mostra legenda**.  
  
### <a name="to-get-the-coefficients-and-terms-for-the-equation"></a>Per ottenere i coefficienti e i termini dell'equazione  
  
1.  Per ottenere i termini e i coefficienti della formula di regressione per un modello Time Series è anche possibile creare un **query contenuto** sul contenuto del modello.  
  
     Per altre informazioni, vedere [Esempi di query sul modello di serie temporale](../../analysis-services/data-mining/time-series-model-query-examples.md)  
  
2.  È anche possibile esplorare modelli Time Series e trovare i termini e coefficienti tramite il [Microsoft Generic Content Tree Viewer](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).  
  
     Per altre informazioni, vedere [Contenuto dei modelli di data mining per i modelli Time Series &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
    > [!NOTE]  
    >  Se si esplora il contenuto di un modello misto che usa modelli sia ARIMA che ARTXP, i due modelli si troveranno in alberi separati, uniti nel nodo radice che rappresenta il modello. Anche se i modelli ARIMA e ARTXP vengono presentati in un unico visualizzatore per comodità, le strutture sono molto diverse, così come le equazioni, le quali non possono essere combinate o confrontate. L'albero ARTXP è più simile a un albero delle decisioni, mentre l'albero ARIMA rappresenta una serie di medie mobili.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Visualizzare un modello utilizzando il visualizzatore Microsoft Time Series](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-time-series-viewer.md)  
  
  
