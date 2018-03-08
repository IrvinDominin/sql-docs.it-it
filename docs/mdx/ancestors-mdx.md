---
title: I predecessori (MDX) | Documenti Microsoft
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
f1_keywords: ANCESTORS
dev_langs: kbMDX
helpviewer_keywords: Ancestors function
ms.assetid: abdf2e9c-72c8-4f2e-a823-d42efc4cc7d5
caps.latest.revision: "46"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3bf406938a92ec3b3c8829b3e1cb59098ea62524
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="ancestors-mdx"></a>Ancestors (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Funzione che restituisce il set di tutti i predecessori di un membro specificato al livello specificato oppure alla distanza specificata dal membro. Con [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], il set restituito sarà sempre costituito da un singolo membro, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] non supporta più elementi padre per un singolo membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Level syntax  
Ancestors(Member_Expression, Level_Expression)  
  
Numeric syntax  
Ancestors(Member_Expression, Distance)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Distanza*  
 Espressione numerica valida che specifica la distanza dal membro specificato.  
  
## <a name="remarks"></a>Osservazioni  
 Con il **predecessori** funzione, si specifica la funzione con un'espressione di membro MDX e quindi un'espressione MDX di un livello è un predecessore di tale membro oppure un'espressione numerica che rappresenta il numero di livelli di sopra di tale membro. Con queste informazioni, il **predecessori** funzione restituisce il set di membri (che sarà un set costituito da un membro) a tale livello.  
  
> [!NOTE]  
>  Per restituire un membro predecessore, anziché un set di predecessori, utilizza il [predecessore](../mdx/ancestor-mdx.md) (funzione).  
  
 Se si specifica un'espressione di livello il **predecessori** funzione restituisce il set di tutti i predecessori del membro specificato al livello specificato. Se il membro specificato non è incluso nella stessa gerarchia del livello specificato, la funzione restituisce un errore.  
  
 Se viene specificata una distanza, la **predecessori** funzione restituisce il set di tutti i membri che sono il numero di passaggi specificato nella gerarchia specificata dall'espressione di membro. Un membro può essere specificato come membro di una gerarchia dell'attributo, una gerarchia definita dall'utente o, in alcuni casi, una gerarchia padre-figlio. Con il numero 1 viene restituito il set di membri al livello padre, mentre con il numero 2 viene restituito il set di membri al livello dell'elemento padre del padre, se esistente. Il numero 0 restituisce il set contenente soltanto il membro stesso.  
  
> [!NOTE]  
>  Utilizzare questo modulo del **predecessori** funzione per i casi in cui il livello dell'elemento padre è sconosciuto o non può essere rinominato.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente usa il **predecessori** funzione per restituire la misura Internet Sales Amount per un membro padre e il relativo elemento padre del padre. Nell'esempio vengono utilizzate espressioni di livello per specificare i livelli da restituire. I livelli sono contenuti nella stessa gerarchia del membro specificato nell'espressione di membro.  
  
```  
SELECT {  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Category]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Subcategory]),  
    Ancestors([Product].[Product Categories].[Product].[Mountain-100 Silver, 38],[Product].[Product Categories].[Product])  
    } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 L'esempio seguente usa il **predecessori** funzione per restituire la misura Internet Sales Amount per un membro padre e il relativo elemento padre del padre. Nell'esempio vengono utilizzate espressioni numeriche per specificare i livelli restituiti. I livelli sono contenuti nella stessa gerarchia del membro specificato nell'espressione di membro.  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],2  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],1  
      ),  
   Ancestors(  
      [Product].[Product Categories].[Product].[Mountain-100 Silver, 38],0  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM  [Adventure Works]  
```  
  
 L'esempio seguente usa il **predecessori** funzione per restituire la misura Internet Sales Amount per l'elemento padre di un membro di una gerarchia dell'attributo. Nell'esempio viene utilizzata un'espressione numerica per specificare il livello restituito. Poiché il membro dell'espressione di membro è membro di una gerarchia dell'attributo, il relativo elemento padre è costituito dal livello [Totale].  
  
```  
SELECT {  
   Ancestors(  
      [Product].[Product].[Mountain-100 Silver, 38],1  
      )  
   } ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
