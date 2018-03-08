---
title: Gli elementi figlio (MDX) | Documenti Microsoft
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
f1_keywords: CHILDREN
dev_langs: kbMDX
helpviewer_keywords: Children function
ms.assetid: ce2c3069-914c-44a3-8a4c-5cbd4fb71e4c
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3227019749138eebef54da7da2a7bb8b85b51ccf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="children-mdx"></a>Children (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce il set di membri figlio di un membro specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Member_Expression.Children  
```  
  
## <a name="arguments"></a>Argomenti  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Osservazioni  
 Il **figli** funzione restituisce un set ordinato che contiene gli elementi figlio di un membro specificato. Se non esistono membri figlio del membro specificato, la funzione restituisce un set vuoto.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente vengono restituiti i figli del membro United States della gerarchia Geography nella dimensione Geography.  
  
```  
SELECT [Geography].[Geography].[Country].&[United States].Children ON 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente restituisce tutti i membri il **misure** dimensione sull'asse delle colonne, inclusi tutti i membri calcolati e il set di tutti gli elementi figlio del `[Product].[Model Name]` gerarchia sull'asse delle righe dell'attributo di **Adventure Works** cubo.  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
  
```  
  
|Versione|Cronologia|  
|-------------|-------------|  
|[!INCLUDE[ssBOL2005_R03](../includes/ssbol2005-r03-md.md)]|**Contenuto modificato:**<br /> - E aggiornati, sintassi degli argomenti per maggiore chiarezza.<br /><br /> : Aggiunta di esempi aggiornati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
