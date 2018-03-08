---
title: Divisione (MDX) | Documenti Microsoft
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
ms.assetid: 9fe4a47b-d5e8-4dc7-ad4a-3e47ab463f03
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7b6be129e35812c2e9f22534a0f9229ec6db6203
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="divide-mdx"></a>Divisione (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue una divisione e restituisce il risultato alternativo o BLANK() della divisione per 0.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Divide (<numerator>, <denominator> [,<alternateresult>])  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeratore*  
 Dividendo o numero da dividere.  
  
 *denominatore*  
 Divisore o numero per cui dividere.  
  
 *alternateresult*  
 (Facoltativo) Il valore restituito se la divisione per zero genera un errore. Se non viene fornito, il valore predefinito è BLANK().  
  
## <a name="remarks"></a>Osservazioni  
 Il risultato alternativo nelle divisione per 0 deve essere una costante.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
