---
title: OpeningPeriod (MDX) | Documenti Microsoft
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
f1_keywords: OPENINGPERIOD
dev_langs: kbMDX
helpviewer_keywords: OpeningPeriod function
ms.assetid: bebf55cf-e5c6-42b1-98f2-1d6e54093d4c
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8c9a23a96e24e454419b5ebf5c05663f188a8766
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il primo elemento di pari livello tra i discendenti di un livello specificato, facoltativamente in corrispondenza di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione è principalmente finalizzata all'utilizzo con una dimensione temporale, ma può essere utilizzata con qualsiasi dimensione.  
  
-   Se si specifica un'espressione di livello il **OpeningPeriod** funzione Usa la gerarchia che contiene il livello specificato e restituisce il primo elemento di pari livello tra i discendenti del membro predefinito al livello specificato.  
  
-   Se vengono specificate sia un'espressione di livello e un'espressione di membro, il **OpeningPeriod** funzione restituisce il primo elemento di pari livello tra i discendenti del membro specificato al livello specificato all'interno della gerarchia che contiene il livello specificato.  
  
-   Se viene specificata né un'espressione di livello né un'espressione di membro, il **OpeningPeriod** funzione utilizza il livello predefinito e un membro della dimensione con un tipo di tempo.  
  
> [!NOTE]  
>  Il [ClosingPeriod](../mdx/closingperiod-mdx.md) è simile alla funzione di **OpeningPeriod** funzione, con la differenza che il **ClosingPeriod** funzione restituisce l'ultimo elemento di pari livello anziché il primo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro FY2002 della dimensione Date (il cui tipo semantico è temporale). Viene restituito questo membro poiché il livello Fiscal Year è il primo discendente del livello [Totale], la gerarchia Fiscal è la gerarchia predefinita poiché costituisce la prima gerarchia definita dall'utente nella raccolta di gerarchie e il membro FY2002 è il primo elemento di pari livello nella gerarchia a questo livello.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro 1 luglio 2001 al livello Date.Date.Date della gerarchia dell'attributo Date.Date. Tale membro costituisce il primo elemento di pari livello del discendente del livello [Totale] nella gerarchia dell'attributo Date.Date.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro gennaio 2003, che costituisce il primo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Calendar.  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 Nell'esempio seguente viene restituito il valore predefinito della misura relativa al membro luglio 2002, che costituisce il primo elemento di pari livello del discendente del membro 2003 a livello di anno nella gerarchia definita dall'utente Fiscal.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [TopCount &#40; MDX &#41;](../mdx/topcount-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40; MDX &#41;](../mdx/firstsibling-mdx.md)  
  
  
