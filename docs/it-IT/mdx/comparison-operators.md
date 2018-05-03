---
title: Gli operatori di confronto | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- comparison operators [MDX]
ms.assetid: 4a4bbc76-c6a2-4b19-ae75-6ac3ac14df01
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 5a2ba472fe36b0b7a1415793c97f3b577adcb0e2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="comparison-operators"></a>Operatori di confronto
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gli operatori di confronto possono essere utilizzati solo con dati scalari. È possibile utilizzare operatori di confronto in qualsiasi espressione MDX (Multidimensional Expressions).  
  
 Per verificare una condizione, è inoltre possibile utilizzare operatori di confronto in istruzioni MDX e funzioni, ad esempio MDX [IIf](../mdx/iif-mdx.md) (funzione). Se si utilizzano operatori di confronto per verificare una condizione, sarà tuttavia necessario verificare di disporre delle autorizzazioni appropriate, prima di tentare di modificare i dati in base a tale condizione. Tutti gli utenti che hanno accesso ai dati effettivi e possono eseguire query su tali dati possono utilizzare operatori di confronto in ulteriori query, ma la possibilità di effettuare l'accesso non implica che tali utenti abbiano o dovrebbero avere le autorizzazioni appropriate per modificare i dati. Per mantenere l'integrità dei dati, è inoltre consigliabile limitare il numero degli utenti autorizzati a eseguire query e a modificare i dati.  
  
 Gli operatori di confronto restituiscono un tipo di dati Boolean, ovvero TRUE o FALSE a seconda che la condizione specificata sia soddisfatta o meno.  
  
 MDX supporta gli operatori di confronto elencati nella tabella seguente.  
  
|Operatore|Description|  
|--------------|-----------------|  
|[= (uguale a)](../mdx/equal-to-mdx.md)|Per argomenti non Null, restituisce TRUE se l'argomento a sinistra è uguale a quello a destra, FALSE in caso contrario.<br /><br /> Se uno dei due argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null, a meno che non venga eseguito il confronto `0=null`. In questo caso il valore booleano conterrà TRUE.|  
|[<> (diverso da)](../mdx/not-equal-to-mdx.md)|Per argomenti non Null, restituisce TRUE se l'argomento a sinistra è diverso da quello a destra, FALSE in caso contrario.<br /><br /> Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[> (maggiore di)](../mdx/greater-than-mdx.md)|Per argomenti non Null, restituisce TRUE se l'argomento a sinistra ha un valore maggiore di quello a destra, FALSE in caso contrario.<br /><br /> Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[>= (maggiore o uguale a)](../mdx/greater-than-or-equal-to-mdx.md)|Per argomenti non Null, restituisce TRUE se l'argomento a sinistra ha un valore maggiore o uguale a quello a destra, FALSE in caso contrario.<br /><br /> Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[< (minore di)](../mdx/less-than-mdx.md)|Per argomenti non Null, restituisce TRUE se l'argomento a sinistra ha un valore minore di quello a destra, FALSE in caso contrario.<br /><br /> Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
|[<= (minore o uguale a)](../mdx/less-than-or-equal-to-mdx.md)|Per argomenti non NULL, restituisce TRUE se l'argomento a sinistra ha un valore minore o uguale a quello a destra, FALSE in caso contrario.<br /><br /> Se uno degli argomenti o entrambi restituiscono un valore Null, l'operatore restituirà un valore Null.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [Gli operatori &#40;sintassi MDX&#41;](../mdx/operators-mdx-syntax.md)  
  
  
