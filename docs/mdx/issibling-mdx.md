---
title: IsSibling (MDX) | Documenti Microsoft
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
f1_keywords: ISSIBLING
dev_langs: kbMDX
helpviewer_keywords: IsSibling function
ms.assetid: 12f302f0-141e-4ec0-ad5f-329aade17a4d
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8a318fd05502dfc9051c51542dcf864fe914d915
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="issibling-mdx"></a>IsSibling (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Indica se il membro specificato è di pari livello rispetto a un altro membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IsSibling(Member_Expression1, Member_Expression2)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
 *Member_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **IsSibling** risultato della funzione **true** se il primo membro specificato è un elemento di pari livello del secondo membro specificato. In caso contrario, la funzione restituisce **false**.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito TRUE se il membro corrente della gerarchia Fiscal nella dimensione Date è un elemento di pari livello di luglio 2002:  
  
 `WITH MEMBER MEASURES.ISSIBLINGDEMO AS`  
  
 `IsSibling([Date].[Fiscal].CURRENTMEMBER, [Date].[Fiscal].[Month].&[2002]&[7])`  
  
 `SELECT {MEASURES.ISSIBLINGDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
