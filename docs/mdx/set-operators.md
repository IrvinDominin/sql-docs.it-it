---
title: Operatori sui set | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: kbMDX
helpviewer_keywords: set operators [MDX]
ms.assetid: 83500d2e-44b3-49eb-a221-3ce5a58277a5
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 612312b3c295e2b9b3f45c4fdba9049036fd7b19
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="set-operators"></a>Operatori sui set
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Nel linguaggio MDX (Multidimensional Expressions) gli operatori sui set eseguono operazioni su membri o set e restituiscono set. Gli operatori sui set vengono spesso utilizzati come alternativa a molte funzioni sui set nelle espressioni MDX.  
  
 MDX supporta gli operatori sui set elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[- (Eccezione)](../mdx/except-mdx-operator.md)|Restituisce le differenze tra due set, rimuovendo i membri duplicati.<br /><br /> Questo operatore equivale al [tranne](../mdx/except-mdx-function.md) (funzione).|  
|[* (Crossjoin)](../mdx/crossjoin-mdx-operator-reference.md)|Restituisce il prodotto incrociato di due set.<br /><br /> Questo operatore equivale al [Crossjoin](../mdx/crossjoin-mdx.md) (funzione).|  
|[: (intervallo)](../mdx/range-mdx.md)|Restituisce un set disposto in ordine naturale, in cui i due membri specificati costituiscono gli endpoint e tutti i membri compresi tra questi ultimi vengono inclusi come membri del set.|  
|[+ (Unione)](../mdx/union-mdx-operator-reference.md)|Restituisce l'unione di due set, escludendo i membri duplicati.<br /><br /> Questo operatore equivale al [unione &#40; MDX &#41; ](../mdx/union-mdx.md) (funzione).|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Operatori &#40; La sintassi MDX &#41;](../mdx/operators-mdx-syntax.md)  
  
  
