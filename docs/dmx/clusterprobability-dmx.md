---
title: ClusterProbability (DMX) | Documenti Microsoft
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
ms.topic: language-reference
f1_keywords: ClusterProbability
dev_langs: DMX
helpviewer_keywords: ClusterProbability function
ms.assetid: a6447b3c-94ce-4122-a3eb-6f3827598d8f
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d4b85f18478d1cc34050804845f62e2283b57462
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="clusterprobability-dmx"></a>ClusterProbability (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce la probabilità che il case di input appartenga al cluster specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
ClusterProbability([<Node_Caption>])  
```  
  
## <a name="applies-to"></a>Si applica a  
 È possibile utilizzare questa funzione solo se il modello di data mining sottostante supporta il clustering.  
  
## <a name="return-type"></a>Tipo restituito  
 Valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 La sintassi seguente utilizza il set di righe dello schema relativo al contenuto del modello di data mining per restituire le didascalie dei nodi esistenti nel modello di data mining.  
  
```  
SELECT NODE_CAPTION FROM <model>.CONTENT  
```  
  
 Per ulteriori informazioni sull'utilizzo di questa sintassi, vedere [modello SELECT FROM &#60; &#62;. DMX contenuto &#40; &#41; ](../dmx/select-from-model-content-dmx.md). Per ulteriori informazioni sul set di righe dello schema del contenuto del modello data mining, vedere [set di righe DMSCHEMA_MINING_MODEL_CONTENT](../analysis-services/schema-rowsets/data-mining/dmschema-mining-model-content-rowset.md).  
  
 Se un \<didascalia del nodo > non è specificato, la funzione restituisce la probabilità che i case di input appartengano al cluster più probabile. Utilizzare il **Cluster** funzione per restituire il cluster più probabile.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la probabilità che il case specificato esista nel cluster con etichetta Cluster 2.  
  
```  
SELECT  
  ClusterProbability('Cluster 2')  
From  
  [TM Clustering]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>Vedere anche  
 [DMX cluster &#40; &#41;](../dmx/cluster-dmx.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
