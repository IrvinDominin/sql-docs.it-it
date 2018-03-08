---
title: "Proprietà di Data Mining | Documenti Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- ClusterCount property
- AllowedProvidersInOpenRowset property
- MinimumSeriesValue property
- ScoreMethod property
- MinimumImportance property
- ModellingCardinality property
- BrentTolerance property
- ComplexityPenalty property
- MaximumItemsetCount property
- MinimumSupport property
- AllowSessionMiningModels property
- HoldoutPercentage property
- ClusterCountPrior property
- MaximumSequenceStates property
- OptimizedPredictionCount property
- data mining [Analysis Services], properties
- MaximumStates property
- MaximumContinuousInputAttributes property
- MaximumOutputAttributes property
- AllowAdHocOpenRowsetQueries property
- Enabled property
- HistoricModelGap property
- SampleSize property
- MaximumInputAttributes property
- PeriodicityHint property
- MissingValueSubstitution property
- SplitMethod property
- ForceRegressor property
- MaximumBucketsForContinuousSplit property
- MaxConcurrentPredictionQueries property
- MinimumItemsetSize property
- AcyclicGraph property
- HoldoutMethod property
- StoppingTolerance property
- properties [data mining]
- AutoDetectPeriodicity property
- HoldoutTolerance property
- MinimumLeafCases property
- HoldoutSeed property
- MinimumClusterCases property
- ClusterCountDeviation property
- MinimumDependencyProbability property
- ClusteringMethod property
- MaximumItemsetSize property
- HiddenNodeRatio property
- MaximumSeriesValue property
ms.assetid: 9bc9abed-180a-4bd8-b2eb-89c62fa88110
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dbe16e3f40b82ab59e7bb74e411c2bc6cc22d97e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="data-mining-properties"></a>Proprietà di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta le proprietà di data mining del server elencate nelle tabelle seguenti. Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Si applica a:** solo in modalità server multidimensionale  
  
## <a name="non-specific-category"></a>Categoria Non-Specific  
 **AllowSessionMiningModels**  
 Proprietà booleana che indica se è possibile creare modelli di data mining di sessione.  
  
 Il valore predefinito di questa proprietà è False per indicare che i modelli di data mining di sessione non possono essere creati.  
  
 **AllowAdHocOpenRowsetQueries**  
 Proprietà booleana che indica se sono consentite query ad hoc su set di righe aperti.  
  
 Il valore predefinito di questa proprietà è False per indicare che le query su set di righe aperti non sono consentite durante una sessione.  
  
 **AllowedProvidersInOpenRowset**  
 Proprietà stringa che indica i provider ammessi in un set di righe aperto; comprende un elenco separato da virgole/punti e virgola di ProgID di provider o il valore [All].  
  
 **MaxConcurrentPredictionQueries**  
 Proprietà a Signed Integer a 32 bit che definisce il numero massimo di query di stima simultanee.  
  
## <a name="algorithms-category"></a>Categoria Algorithms  
 **Microsoft_Association_Rules\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Association_Rules è attivato.  
  
 **Microsoft_Clustering\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Clustering è attivato.  
  
 **Microsoft_Decision_Trees\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_DecisionTrees è attivato.  
  
 **Microsoft_Naive_Bayes\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_ Naive_Bayes è attivato.  
  
 **Microsoft_Neural_Network\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Neural_Network è attivato.  
  
 **Microsoft_Sequence_Clustering\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Sequence_Clustering è attivato.  
  
 **Microsoft_Time_Series\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Time_Series è attivato.  
  
 **Microsoft_Linear_Regression\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Linear_Regression è attivato.  
  
 **Microsoft_Logistic_Regression\ Enabled**  
 Proprietà booleana che indica se l'algoritmo Microsoft_Logistic_Regression è attivato.  
  
> [!NOTE]  
>  Oltre alle proprietà che definiscono i servizi data mining disponibili nel server, esistono proprietà di data mining che definiscono il comportamento di algoritmi specifici. Configurare tali proprietà quando si crea un modello di data mining singolo, non a livello di server. Per altre informazioni, vedere [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura fisica &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)   
 [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
