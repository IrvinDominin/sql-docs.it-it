---
title: Utilizzo di espressioni di tupla | Documenti Microsoft
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
helpviewer_keywords:
- single-member tuples [MDX]
- expressions [MDX], tuples
- one-member tuples
- tuples
- implicit tuples
ms.assetid: 0b802b76-9123-405e-ae43-d438754724ba
caps.latest.revision: "27"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 659b1047984e58395097a15446b2860ed37a7371
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="using-tuple-expressions"></a>Utilizzo delle espressioni di tupla
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Una tupla è costituita da un membro proveniente da ogni dimensione contenuta in un cubo. Una tupla identifica pertanto in modo univoco una singola cella del cubo.  
  
> [!NOTE]  
>  Una tupla che fa riferimento a uno o più membri non validi è detta tupla vuota.  
  
 L'espressione completa di un identificatore di tupla è costituita da uno o più membri specificati in modo esplicito e racchiusi tra parentesi:  
  
 (*Member_expression* [,*Member_expression* ...])  
  
 Una tupla può essere completa, può contenere membri impliciti oppure un solo membro.  
  
## <a name="tuples-and-implicit-members"></a>Tuple e membri impliciti  
 Una tupla che specifica in modo esplicito un singolo membro da ogni dimensione contenuta in un cubo è detta tupla completa. Non è tuttavia indispensabile utilizzare tuple complete.  
  
 A ogni dimensione a cui la tupla non fa riferimento in modo esplicito viene fatto riferimento in modo implicito. Il membro per la dimensione alla quale viene fatto riferimento in modo implicito dipende dalla struttura delle relazioni della dimensione e degli attributi in essa definiti. Se esiste un riferimento esplicito a una gerarchia nella stessa dimensione della gerarchia con riferimento implicito e se esiste una relazione diretta o indiretta tra le due gerarchie, la tupla si comporta come se contenesse il membro sulla gerarchia con riferimento implicito che esiste con il membro nella gerarchia con riferimento esplicito. Ad esempio, se un cubo contiene una dimensione Cliente con gli attributi Città e Paese ed esiste una relazione definita tra questi due attributi per cui una Città ha un Paese e un Paese può contenere più Città, l'inserimento esplicito della Città "Londra" nella tupla farà riferimento implicito al Paese "Regno Unito". Se invece non è definita alcuna relazione tra gli attributi, la relazione è posta in senso inverso (ad esempio, sebbene Città possa avere una relazione con Paese, non sarà possibile determinare la Città in cui una persona vive semplicemente conoscendone il Paese). Se non vi sono relazioni dirette tra i due attributi definiti (potrebbe esistere una relazione definita tra Cliente e Città e tra Cliente e Paese, ma non tra Città e Paese), vengono applicate le regole seguenti:  
  
-   Se la gerarchia con riferimento implicito dispone di un membro predefinito, tale membro sarà aggiunto alla tupla.  
  
-   Se la gerarchia con riferimento implicito non dispone di alcun membro predefinito, il **(tutti)** membro della gerarchia predefinita viene utilizzato.  
  
-   Se la gerarchia con riferimento implicito non dispone di un membro predefinito, verrà utilizzato il primo membro del livello più alto della gerarchia.  
  
## <a name="one-member-tuples"></a>Tuple con un solo membro  
 Se l'espressione di tupla ha un solo membro, per valutare l'espressione MDX convertirà il membro in una tupla con un solo membro. In altre parole, l'utilizzo dell'espressione di membro `[Measures].[TestMeasure]` al posto di un'espressione di tupla è equivalente, dal punto di vista funzionale, a utilizzare l'espressione di tupla `( [Measures].[TestMeasure] ).`  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40; MDX &#41;](../mdx/expressions-mdx.md)   
 [Riferimento alla funzione MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
