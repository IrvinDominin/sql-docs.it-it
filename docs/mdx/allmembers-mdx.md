---
title: AllMembers (MDX) | Documenti Microsoft
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
f1_keywords: ALLMEMBERS
dev_langs: kbMDX
helpviewer_keywords: AllMembers function
ms.assetid: 202e81d4-d2ee-4ec1-a019-4835eb19f446
caps.latest.revision: "44"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 67b0b2071e03d3b66daa1a34a6af4159cee89cea
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Valuta un'espressione di gerarchia o di livello e restituisce un set che contiene tutti i membri della gerarchia o del livello specificato, inclusi tutti i membri calcolati in tale gerarchia o livello.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
## <a name="remarks"></a>Osservazioni  
 Il **AllMembers** funzione restituisce un set contenente tutti i membri, che include i membri calcolati, la gerarchia o livello specificato. Il **AllMembers** funzione restituisce i membri calcolati, anche se la gerarchia o livello specificato non contiene membri visibili.  
  
> [!IMPORTANT]  
>  Quando una dimensione contiene una sola gerarchia visibile, è possibile fare riferimento alla gerarchia con il nome della dimensione o della gerarchia poiché in questo caso il nome della dimensione viene risolto in base all'unica gerarchia visibile che contiene. `Measures.AllMembers` è ad esempio un'espressione MDX valida perché esegue la risoluzione nell'unica gerarchia nella dimensione Measures.  
  
> [!NOTE]  
>  Il **AllMembers** funzione è semanticamente simile al [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md) (funzione).  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce tutti i membri di [`Date].[Calendar Year]` gerarchia dell'attributo sull'asse delle colonne, inclusi i membri calcolati e il set di tutti gli elementi figlio del `[Product].[Model Name]` attributo gerarchia sull'asse delle righe dal **Adventure Works** cubo.  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 L'esempio seguente restituisce tutti i membri il **misure** dimensione sull'asse delle colonne, inclusi tutti i membri calcolati e il set di tutti gli elementi figlio del `[Product].[Model Name]` gerarchia sull'asse delle righe dell'attributo di **Adventure Works** cubo.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [AddCalculatedMembers &#40; MDX &#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Gli elementi figlio &#40; MDX &#41;](../mdx/children-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
