---
title: Operatori di confronto (DMX) | Documenti Microsoft
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
dev_langs: DMX
helpviewer_keywords: comparison operators [DMX]
ms.assetid: eea3cf90-9683-4453-b1f3-da740f3a4885
caps.latest.revision: "17"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 80c969bb4c5b8f6d6ac288279af6d8ce28905f68
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="operators---comparison"></a>Operatori di confronto-
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  È possibile utilizzare gli operatori di confronto con dati scalari in qualsiasi espressione di Data Mining Extensions (DMX) [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Questi operatori restituiscono un tipo di dati Boolean, ovvero TRUE o FALSE a seconda che venga soddisfatta o meno la condizione specificata.  
  
 Gli operatori di confronto supportati da DMX sono indicati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[&#60; &#40; Minore di &#41; &#40; DMX &#41;](../dmx/less-than-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62; &#40; Maggiore di &#41; &#40; DMX &#41;](../dmx/greater-than-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore di quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[= &#40; Uguale a &#41; &#40; DMX &#41;](../dmx/equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60; &#62; &#40; Non uguale a &#41; &#40; DMX &#41;](../dmx/not-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è diverso da quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#60; = &#40; Minore o uguale a &#41; &#40; DMX &#41;](../dmx/less-than-or-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è minore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[&#62; = &#40; Maggiore o uguale a &#41; &#40; DMX &#41;](../dmx/greater-than-or-equal-to-dmx.md)|Per gli argomenti che restituiscono valori non Null, restituisce TRUE se il valore dell'argomento a sinistra è maggiore o uguale a quello dell'argomento a destra, FALSE in caso contrario. Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
  
 Nelle istruzioni e nelle funzioni DMX è possibile utilizzare gli operatori di confronto anche per stabilire se una condizione è verificata o meno.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../dmx/data-mining-extensions-dmx-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento (funzione)](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento agli operatori](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Data Mining Extensions &#40; DMX &#41; Convenzioni della sintassi](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40; DMX &#41; Elementi della sintassi](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Espressioni &#40; DMX &#41;](../dmx/expressions-dmx.md)   
 [Funzioni di stima generale &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [Operatori &#40; DMX &#41;](../dmx/operators-dmx.md)   
 [Struttura e l'utilizzo di query di stima DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Informazioni sull'istruzione DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
