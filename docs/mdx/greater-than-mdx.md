---
title: '&gt; (Maggiore di) (MDX) | Documenti Microsoft'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0b7eb0cdcfbe6a22a18236362b4a2277eb42eb42
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740200"
---
# <a name="gt-greater-than-mdx"></a>&gt; (Maggiore di) (MDX)


  Esegue un'operazione di confronto che determina se il valore di un'espressione MDX (Multidimensional Expression) è maggiore di quello di un'altra espressione MDX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MDX_Expression > MDX_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *MDX_Expression*  
 Espressione MDX valida.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano basato sulle condizioni seguenti:  
  
-   **true** se entrambi i parametri sono non null e il primo parametro è un valore che è maggiore del valore del secondo parametro.  
  
-   **false** se entrambi i parametri sono non null e il primo parametro è un valore che è uguale o inferiore al valore del secondo parametro.  
  
-   Null se uno o entrambi i parametri restituiscono un valore Null.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio di query seguente viene illustrato l'utilizzo di questo operatore.  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is more than 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] > .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
