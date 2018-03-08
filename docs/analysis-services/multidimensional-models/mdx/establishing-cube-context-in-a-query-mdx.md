---
title: Definizione del contesto di cubo in una Query (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 570d327b099508fc98f0e247b919fb222db54509
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>Definizione del contesto di cubo in una query (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Ogni query MDX viene eseguita nel contesto di cubo specificato. Tale contesto definisce i membri che vengono valutati dalle espressioni incluse nella query.  
  
 Il contesto di cubo è determinato dalla clausola FROM dell'istruzione SELECT. Può corrispondere all'intero cubo o a una sezione del cubo, o sottocubo. Dopo aver specificato il contesto di cubo tramite la clausola FROM, è possibile utilizzare funzioni aggiuntive per espandere o limitare tale contesto.  
  
> [!NOTE]  
>  Per la gestione del contesto di cubo è inoltre possibile utilizzare le istruzioni SCOPE e CALCULATE che consentono di gestire il contesto in uno script MDX. Per altre informazioni, vedere [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
## <a name="from-clause-syntax"></a>Sintassi della clausola FROM  
 La sintassi della clausola FROM è la seguente:  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 Si noti che il cubo o sottocubo in cui viene eseguita l'istruzione SELECT è descritta nella clausola `<SELECT subcube clause>` .  
  
 Una clausola FROM semplice viene eseguita nell'intero cubo di esempio Adventure Works. Il formato di tale clausola è il seguente:  
  
```  
FROM [Adventure Works]  
```  
  
 Per altre informazioni sulla clausola FROM nell'istruzione MDX SELECT, vedere [Istruzione SELECT &#40;MDX&#41;](../../../mdx/mdx-data-manipulation-select.md).  
  
## <a name="refining-the-context"></a>Ridefinizione del contesto  
 Sebbene la clausola FROM specifichi il contesto di cubo come singolo cubo, ciò non impedisce di utilizzare i dati di più cubi contemporaneamente.  
  
 Tramite la funzione MDX [LookupCube](../../../mdx/lookupcube-mdx.md) è possibile recuperare dati di cubi all'esterno del contesto di cubo. Sono inoltre disponibili funzioni che consentono una limitazione temporale del contesto durante la valutazione della query, ad esempio la funzione [Filter](../../../mdx/filter-mdx.md) .  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali sulle Query MDX &#40; Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
