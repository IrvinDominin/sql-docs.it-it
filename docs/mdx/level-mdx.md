---
title: Livello (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LEVEL
dev_langs:
- kbMDX
helpviewer_keywords:
- Level function
ms.assetid: 10bbe4ac-44bc-45c7-81a1-85423fbeaab1
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 017ffb731cd0104da7a818bad837bc7b121182d4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="level-mdx"></a>Level (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il livello di un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Level  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
### <a name="examples"></a>Esempi  
 L'esempio seguente usa il **livello** funzione per restituire tutti i mesi nel cubo Adventure Works.  
  
```  
SELECT[Date].[Fiscal].[Month].[February 2002].Level.Members ON 0,  
[Measures].[Internet Sales Amount] ON 1  
FROM [Adventure Works]  
```  
  
 L'esempio seguente usa il **livello** funzione per restituire il nome del livello per il supporto All-Purpose Bike nella gerarchia dell'attributo nome del modello nel cubo Adventure Works.  
  
```  
WITH MEMBER Measures.x AS   
   [Product].[Model Name].[All-Purpose Bike Stand].Level.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
