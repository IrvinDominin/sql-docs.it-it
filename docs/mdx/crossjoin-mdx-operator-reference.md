---
title: '* (Crossjoin) (MDX) | Documenti Microsoft'
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
f1_keywords: '*'
dev_langs: kbMDX
helpviewer_keywords:
- '* (crossjoin operator)'
- crossjoin operator (*)
ms.assetid: e00cb260-0189-4c4e-b3d2-088f4421337b
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: e192e0eacd926cde2c6548392b1523cfc3d0af12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - riferimento agli operatori MDX
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione sui set che restituisce il prodotto incrociato di due set.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>Parametro  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="return-value"></a>Valore restituito  
 Set che contiene il prodotto incrociato di entrambi i parametri specificati.  
  
## <a name="remarks"></a>Osservazioni  
 Il  **\* (Crossjoin)** è funzionalmente equivalente all'operatore di [Crossjoin](../mdx/crossjoin-mdx.md) (funzione).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
