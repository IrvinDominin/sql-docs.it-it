---
title: Membri (Set) (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742690"
---
# <a name="members-set-mdx"></a>Members (Set) (MDX)


  Restituisce il set di membri di una dimensione, di un livello o di una gerarchia.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
## <a name="remarks"></a>Remarks  
 Se viene specificata un'espressione di gerarchia, il **Members (Set)** funzione restituisce il set di tutti i membri all'interno della gerarchia specificata, esclusi i membri calcolati. Per ottenere il set di tutti i membri, calcolata o in caso contrario, in una gerarchia di [AllMembers &#40;MDX&#41; ](../mdx/allmembers-mdx.md) (funzione)  
  
 Se si specifica un'espressione di livello il **Members (Set)** funzione restituisce il set di tutti i membri all'interno del livello specificato.  
  
> [!IMPORTANT]  
>  Quando una dimensione contiene una sola gerarchia visibile, è possibile fare riferimento alla gerarchia con il nome della dimensione o della gerarchia poiché in questo scenario il nome della dimensione viene risolto in base all'unica gerarchia visibile che contiene. Measures.Members è ad esempio un'espressione MDX valida perché esegue la risoluzione nell'unica gerarchia nella dimensione Measures.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il set di tutti i membri contenuti nella gerarchia Calendar Year del cubo Adventure Works.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 Nell'esempio seguente vengono restituiti i quantitativi ordinati per il 2003 per ogni membro del livello `[Product].[Products].[Product Line]`. Il **membri** e restituisce un set che rappresenta tutti i membri nel livello.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
