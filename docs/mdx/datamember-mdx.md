---
title: DataMember (MDX) | Documenti Microsoft
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
f1_keywords: DATAMEMBER
dev_langs: kbMDX
helpviewer_keywords: DataMember function
ms.assetid: 65bf21e8-1cb2-4ae8-bfbe-bb4d72589557
caps.latest.revision: "30"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 8ebc7c203eeb0ca365f7c61dbc827082c6bf9234
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="datamember-mdx"></a>DataMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il membro dei dati generato dal sistema associato a un membro non foglia di una dimensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Remarks  
 Questa funzione agisce sui membri non foglia in una gerarchia qualsiasi e può essere utilizzata dal [UPDATE CUBE Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) per i dati writeback per un membro non foglia direttamente, anziché per i discendenti del membro foglia.  
  
> [!NOTE]  
>  Restituisce il membro specificato se tale membro è un membro foglia o se al membro non foglia non è associato alcun membro dei dati.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa il **DataMember** funzione in una misura calcolata per mostrare la quota di vendite per ogni singolo dipendente:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)   
 [Concetti chiave di MDX &#40; Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
