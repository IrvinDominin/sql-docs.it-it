---
title: NameToSet (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- NAMETOSET
dev_langs:
- kbMDX
helpviewer_keywords:
- NameToSet function
ms.assetid: e02e17d5-4309-49cb-84c7-5b445ac2bd94
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 365181e10812a1f28bf39385a75215e6be304b23
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce un set contenente il membro specificato da una stringa in formato MDX (Multidimensional Expression).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Name*  
 Espressione stringa valida che rappresenta il nome di un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Se il nome di membro specificato esiste, il **NameToSet** funzione restituisce un set contenente tale membro. In caso contrario, la funzione restituisce un set vuoto.  
  
> [!NOTE]  
>  Il nome del membro specificato deve essere costituito esclusivamente da un nome di membro e non può corrispondere a un'espressione di membro. Per usare un'espressione di membro, vedere [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito il valore predefinito della misura per il nome del membro specificato.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
