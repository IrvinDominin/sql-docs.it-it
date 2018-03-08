---
title: Predecessori (MDX) | Documenti Microsoft
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
f1_keywords: ASCENDANTS
dev_langs: kbMDX
helpviewer_keywords: Ascendants function
ms.assetid: a2baf4a2-7d66-4766-b708-739a3c21b09e
caps.latest.revision: "39"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: a8f2d48317bb6cb0fb5a066348ae1beed8a0f35f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="ascendants-mdx"></a>Ascendants (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set dei predecessori del membro specificato, incluso il membro stesso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Ascendants(Member_Expression)  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **predecessori** funzione restituisce tutti i predecessori di un membro del membro nella parte superiore della gerarchia del membro; in particolare, esegue un attraversamento post-ordine della gerarchia per il membro specificato e restituisce tutti i predecessori correlati al membro, incluso se stesso, in un set. È in contrasto con la [predecessore](../mdx/ancestor-mdx.md) funzione che restituisce un membro di predecessori specifico o predecessore, a un livello specifico.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce il numero di ordini dei rivenditori per il `[Sales Territory].[Northwest]` membro e tutti i predecessori di tale membro dal **Adventure Works** cubo. Il **predecessori** funzione costruisce il set che include il `[Sales Territory].[Northwest]` membro e i relativi predecessori per l'asse ROWS.  
  
```  
SELECT  
   Measures.[Reseller Order Count] ON COLUMNS,  
   Order(  
      Ascendants(  
         [Sales Territory].[Northwest]  
      ),  
      DESC  
   ) ON ROWS  
FROM  
   [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
