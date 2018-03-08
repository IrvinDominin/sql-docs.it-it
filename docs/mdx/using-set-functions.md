---
title: Utilizzo di Set di funzioni | Documenti Microsoft
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
dev_langs: kbMDX
helpviewer_keywords: set functions [MDX]
ms.assetid: b08ddc9d-38f8-41aa-b791-b5352f1a8783
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c0afa99103cbb10c29c66bc375dc10d206560fd8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-set-functions"></a>Utilizzo delle funzioni sui set
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Una funzione sui set recupera un set da una dimensione, da una gerarchia, da un livello o attraversando i percorsi assoluti e relativi dei membri di tali oggetti, costruendo i set in vari modi.  
  
 Le funzioni sui set, come le funzioni membro e le funzioni di tupla, sono essenziali per la negoziazione delle strutture multidimensionali utilizzate in Analysis Services. Le funzioni sui set sono essenziali anche per ottenere risultati dalle query MDX, perché le espressioni set definiscono gli assi di una query MDX.  
  
 Una delle funzioni set più comune è il [membri &#40; Set &#41; &#40; MDX &#41; ](../mdx/members-set-mdx.md) (funzione), che recupera un set contenente tutti i membri di una dimensione, gerarchia o livello. Nell'esempio seguente viene illustrato l'utilizzo di questa funzione all'interno di una query:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns all of the members on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Un'altra funzione di uso comune è il [Crossjoin &#40; MDX &#41; ](../mdx/crossjoin-mdx.md) (funzione). Questa funzione restituisce un set di tuple che rappresenta il prodotto cartesiano dei set passati come parametri. In termini pratici, consente di creare assi "nidificati" o "con campi incrociati" nelle query:  
  
 `SELECT`  
  
 `//Returns all of the members on the Measures dimension`  
  
 `[Measures].MEMBERS`  
  
 `ON Columns,`  
  
 `//Returns a set containing every combination of all of the members`  
  
 `//on the Calendar Year level of the Calendar Year Hierarchy`  
  
 `//on the Date dimension and all of the members on the Category level`  
  
 `//of the Category hierarchy on the Product dimension`  
  
 `Crossjoin(`  
  
 `[Date].[Calendar Year].[Calendar Year].MEMBERS,`  
  
 `[Product].[Category].[Category].MEMBERS)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Il [discendenti &#40; MDX &#41; ](../mdx/descendants-mdx.md) funzione è simile di **figli** funzionare, ma è più potente. Restituisce i discendenti di qualsiasi membro a uno o più livelli in una gerarchia:  
  
 SELECT  
  
 [Measures].[Internet Sales Amount]  
  
 ON Columns,  
  
 //Restituisce un set contenente tutte le date comprese nel calendario  
  
 //2004 nella gerarchia Calendar della dimensione Date  
  
 DESCENDANTS(  
  
 [Date].[Calendar].[Calendar Year].&[2004]  
  
 , [Date].[Calendar].[Date])  
  
 ON Rows  
  
 FROM [Adventure Works]  
  
 Il [ordine &#40; MDX &#41; ](../mdx/order-mdx.md) funzione consente di ordinare il contenuto di un set in ordine crescente o decrescente in base a una particolare espressione numerica. La query seguente restituisce gli stessi membri nelle righe della query precedente, ma in questo caso i membri vengono ordinati in base alla misura Internet Sales Amount:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//ordered by Internet Sales Amount`  
  
 `ORDER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount], BDESC)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Questa query illustra anche come passare come parametro il set restituito da una funzione sui set (Descendants) a un'altra funzione sui set (Order).  
  
 Filtraggio di un set in base a determinati criteri si rivela utile quando la scrittura di query e per questo scopo è possibile utilizzare il [filtro &#40; MDX &#41; ](../mdx/filter-mdx.md) funzione, come illustrato nell'esempio seguente:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//where Internet Sales Amount is greater than $70000`  
  
 `FILTER(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `, [Measures].[Internet Sales Amount]>70000)`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Esistono altre funzioni più sofisticate che consentono di applicare filtri a un set con modalità diverse. Ad esempio, la query seguente viene illustrato il [TopCount &#40; MDX &#41; ](../mdx/topcount-mdx.md) funzione restituisce i primi n elementi in un set:  
  
 `SELECT`  
  
 `[Measures].[Internet Sales Amount]`  
  
 `ON Columns,`  
  
 `//Returns a set containing the top 10 Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension by Internet Sales Amount`  
  
 `TOPCOUNT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,10, [Measures].[Internet Sales Amount])`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
 Infine è possibile eseguire una serie di operazioni logiche sui set utilizzando funzioni quali [Intersect &#40; MDX &#41; ](../mdx/intersect-mdx.md), [Unione &#40; MDX &#41; ](../mdx/union-mdx.md) e [tranne &#40; MDX &#41; ](../mdx/except-mdx-function.md) funzioni. La query seguente illustra l’utilizzo delle ultime due funzioni:  
  
 `SELECT`  
  
 `//Returns a set containing the Measures Internet Sales Amount, Internet Tax Amount and`  
  
 `//Internet Total Product Cost`  
  
 `UNION(`  
  
 `{[Measures].[Internet Sales Amount], [Measures].[Internet Tax Amount]}`  
  
 `, {[Measures].[Internet Total Product Cost]}`  
  
 `)`  
  
 `ON Columns,`  
  
 `//Returns a set containing all of the Dates beneath Calendar Year`  
  
 `//2004 in the Calendar hierarchy of the Date dimension`  
  
 `//except the January 1st 2004`  
  
 `EXCEPT(`  
  
 `DESCENDANTS(`  
  
 `[Date].[Calendar].[Calendar Year].&[2004]`  
  
 `, [Date].[Calendar].[Date])`  
  
 `,{[Date].[Calendar].[Date].&[915]})`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni &#40; La sintassi MDX &#41;](../mdx/functions-mdx-syntax.md)   
 [Utilizzo delle funzioni membro](../mdx/using-member-functions.md)   
 [Uso delle funzioni di tupla](../mdx/using-tuple-functions.md)  
  
  
