---
title: DrillupMember (MDX) | Documenti Microsoft
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
f1_keywords: DRILLUPMEMBER
dev_langs: kbMDX
helpviewer_keywords: DrillupMember function
ms.assetid: debcd966-ea4e-4ecf-8600-0a4d346d03f8
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7062d26fa444eefcdcf77519be5e6d28e42ce9cf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="drillupmember-mdx"></a>DrillupMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Restituisce i membri di un set specificato che non sono discendenti dei membri di un secondo set specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillupMember(Set_Expression1, Set_Expression2)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
## <a name="remarks"></a>Remarks  
 Il **DrillupMember** funzione restituisce un set di membri in base ai membri specificati nel primo set che sono discendenti dei membri del secondo set. Il primo set può avere qualsiasi dimensionalità, mentre il secondo deve contenere un set unidimensionale. L'ordine tra i membri originali del primo set viene mantenuto. La funzione costruisce il set includendo solo i membri del primo set che sono discendenti immediati dei membri del secondo set. Se il predecessore immediato di un membro del primo set non è presente nel secondo set, il set restituito dalla funzione include il membro del primo set. Vengono inoltre inclusi i discendenti presenti nel primo set che precedono un membro predecessore del secondo set.  
  
 Il primo set può contenere tuple anziché membri. La funzione per il drill-down di tuple è un'estensione di OLE DB e restituisce un set di tuple anziché di membri.  
  
> [!IMPORTANT]  
>  Il drill-up di un membro verrà eseguito solo se il membro è seguito immediatamente da un elemento figlio o un discendente. L'ordine dei membri nel set è rilevante per il drill-down\* e drill-up\* famiglie di funzioni. È consigliabile utilizzare il **Hierarchize** funzione per ordinare in modo appropriato i membri del primo set.  
  
## <a name="example"></a>Esempio  
 I tre esempi seguenti sono identici a eccezione del secondo set. Nel primo esempio, il secondo set è United States. Di conseguenza, Colorado viene escluso dal set di risultati. È un discendente di United States.  
  
```  
SELECT DrillUpMember (   
  { [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[United States]}   
 ) ON 0   
FROM [Adventure Works]  
```  
  
 Il secondo esempio mostra l'importanza dell'ordine dei membri. Poiché **DrillupMember** solo drill backup dei membri seguiti immediatamente dai discendenti nel primo set, non drill-up del membro Canada. Canada è separato dal relativi discendenti da United States e Colorado. Se si riordinano i membri in modo che Canada sia direttamente sopra Alberta, Alberta e Brunswick verranno esclusi dal set di righe.  
  
```  
SELECT DrillUpMember (   
 {  [Geography].[Geography].[Country].[Canada]   
   ,[Geography].[Geography].[Country].[United States]   
   ,[Geography].[Geography].[State-Province].[Colorado]   
   ,[Geography].[Geography].[State-Province].[Alberta]   
   ,[Geography].[Geography].[State-Province].[Brunswick]    
 }   
 , {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
```  
  
 Terzo esempio mostra come l'uso di **Hierarchize** può ridurre gli effetti dell'ordine dei membri e le esercitazioni del membro Canada.  
  
```  
SELECT DrillUpMember (   
 Hierarchize   
  (   
   { [Geography].[Geography].[Country].[Canada]   
    ,[Geography].[Geography].[Country].[United States]   
    ,[Geography].[Geography].[State-Province].[Colorado]   
    ,[Geography].[Geography].[State-Province].[Alberta]   
    ,[Geography].[Geography].[State-Province].[Brunswick]    
   }   
  ), {[Geography].[Geography].[Country].[Canada]}   
 )   
ON 0   
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
