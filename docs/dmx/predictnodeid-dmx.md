---
title: PredictNodeId (DMX) | Documenti Microsoft
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
f1_keywords: PredictNodeId
dev_langs: DMX
helpviewer_keywords: PredictNodeId function
ms.assetid: fb236645-ad7e-4c54-9c4c-1af47cad7ad5
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c2184534d2eccc07ef42bae3ea17f311ba63cb3e
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="predictnodeid-dmx"></a>PredictNodeId (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Viene restituito il Node_ID del nodo in cui è classificato il case.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PredictNodeId(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>Si applica a  
 Colonna scalare.  
  
## <a name="return-type"></a>Tipo restituito  
 \<espressione scalare >  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la probabilità che l'individuo specificato acquisti una bicicletta e il nodeID del nodo cui, più probabilmente, apparterranno.  
  
```  
SELECT  
  [Bike Buyer],  
  PredictNodeId([Bike Buyer])  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
 Successivamente si potrebbe utilizzare l'istruzione seguente per determinare il contenuto del nodo:  
  
```  
SELECT   
  NODE_CAPTION   
FROM   
  [TM Decision Tree].CONTENT  
WHERE NODE_UNIQUE_NAME= '00000000100'   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [DMX funzioni &#40; &#41;](../dmx/functions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
