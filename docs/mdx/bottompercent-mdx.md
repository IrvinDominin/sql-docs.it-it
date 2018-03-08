---
title: BottomPercent (MDX) | Documenti Microsoft
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
f1_keywords: BOTTOMPERCENT
dev_langs: kbMDX
helpviewer_keywords: BottomPercent function
ms.assetid: c04866e6-e6dd-4ed1-ae79-c718c194930c
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 078221baa088e0375af381e1e4ef5579280a2cb3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Dispone un set in ordine crescente e restituisce un set di tuple con i valori più bassi il cui totale cumulativo è uguale o maggiore della percentuale specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Percentuale*  
 Espressione numerica valida che specifica la percentuale di tuple da restituire.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Remarks  
 Il **BottomPercent** funzione calcola la somma dell'espressione numerica specificata valutata su un set specificato, disponendo il set in ordine crescente. La funzione restituisce quindi gli elementi con i valori più bassi la cui percentuale cumulativa del valore sommato totale corrisponde almeno alla percentuale specificata. La funzione restituisce il subset più piccolo di un set il cui totale cumulativo corrisponde almeno alla percentuale specificata. Gli elementi restituiti sono ordinati dal più grande al più piccolo.  
  
> [!IMPORTANT]  
>  Il **BottomPercent** funzione, come il [TopPercent](../mdx/toppercent-mdx.md) funzione, non rispetta mai la gerarchia. Per ulteriori informazioni, vedere la funzione Order.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito per la categoria Bike il set più piccolo di membri del livello City nella gerarchia Geography della dimensione Geography per l'anno fiscale 2003 il cui totale cumulativo utilizzando la misura Reseller Sales Amount corrisponde almeno al 15% del totale cumulativo (a partire dai membri di questo set con il numero di vendite più basso).  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
