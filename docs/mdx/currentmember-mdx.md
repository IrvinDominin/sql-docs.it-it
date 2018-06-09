---
title: CurrentMember (MDX) | Documenti Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7d47e12b95a92930bbdfceaba5cc8997c286eec
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739950"
---
# <a name="currentmember-mdx"></a>CurrentMember (MDX)


  Restituisce il membro corrente in una gerarchia specificata durante l'iterazione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Hierarchy_Expression.CurrentMember  
```  
  
## <a name="arguments"></a>Argomenti  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
## <a name="remarks"></a>Remarks  
 Il membro su cui si opera a ogni passaggio di un'iterazione in un set di membri della gerarchia corrisponde al membro corrente. Il **CurrentMember** funzione restituisce tale membro.  
  
> [!IMPORTANT]  
>  Quando una dimensione contiene una sola gerarchia visibile, è possibile fare riferimento alla gerarchia con il nome della dimensione o della gerarchia poiché il nome della dimensione viene risolto in base all'unica gerarchia visibile che contiene. `Measures.CurrentMember` è ad esempio un'espressione MDX valida perché esegue la risoluzione nell'unica gerarchia nella dimensione Measures.  
  
## <a name="examples"></a>Esempi  
 La query seguente viene illustrato come **Currentmember** consente di trovare il membro corrente da gerarchie sulle colonne, righe e sezione asse:  
  
 `WITH MEMBER MEASURES.CURRENTDATE AS`  
  
 `[Date].[Calendar].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTPRODUCT AS`  
  
 `[Product].[Product Categories].CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTMEASURE AS`  
  
 `MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.CURRENTCUSTOMER AS`  
  
 `[Customer].[Customer Geography].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `[Product].[Product Categories].[Category].MEMBERS`  
  
 `*`  
  
 `{MEASURES.CURRENTDATE, MEASURES.CURRENTPRODUCT,MEASURES.CURRENTMEASURE, MEASURES.CURRENTCUSTOMER}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 `WHERE([Customer].[Customer Geography].[Country].&[Australia])`  
  
 Il membro corrente cambia su una gerarchia utilizzata su un asse in una query. Può pertanto cambiare anche il membro corrente sulle altre gerarchie sulla stessa dimensione che non vengono utilizzati su un asse; Questo comportamento viene chiamato 'auto EXIST' e altri dettagli sono disponibili [concetti chiave di MDX &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md). Ad esempio, nella query seguente viene illustrato come il membro corrente sulla gerarchia di Calendar Year della dimensione Date cambia con il membro corrente sulla gerarchia Calendar, quando quest'ultimo viene visualizzato sull'asse delle righe:  
  
 `WITH MEMBER MEASURES.CURRENTYEAR AS`  
  
 `[Date].[Calendar Year].CURRENTMEMBER.NAME`  
  
 `SELECT`  
  
 `{MEASURES.CURRENTYEAR}`  
  
 `ON 0,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
 **CurrentMember** è molto importante per rendere i calcoli specifici del contesto della query vengono utilizzati in. L'esempio seguente restituisce la quantità dell'ordine di ogni prodotto e la percentuale di quantità dell'ordine per categoria e modello, dal **Adventure Works** cubo. Il **CurrentMember** funzione identifica il prodotto la cui quantità dell'ordine viene utilizzato durante il calcolo.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty  
(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
