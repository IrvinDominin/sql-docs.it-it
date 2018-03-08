---
title: Definire formule personalizzate membro | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
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
- members [Analysis Services], custom
- custom rollup formulas [Analysis Services]
- MDX [Analysis Services], custom rollup formulas
- custom member formulas [Analysis Services]
ms.assetid: 258304e2-d900-4013-97e3-871f51dfdce2
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: a81bd6be288a17ca22d82a63f8a7e8952b506772
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="attribute-properties---define-custom-member-formulas"></a>Attributo di proprietà: definire formule personalizzate membro
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
È possibile definire un'espressione MDX (MultiDimensional Expression), denominata formula personalizzata membro, per indicare i valori dei membri di un attributo specificato. L'espressione utilizzata per specificare il valore di ogni membro di un attributo è indicata in una colonna di una tabella di una vista origine dati.  
  
 Le formule personalizzate membro determinano i valori delle celle associati ai membri e hanno priorità rispetto alle funzioni di aggregazione delle misure. Le formule personalizzate membro sono scritte in MDX. Ogni formula personalizzata membro viene applicata a un singolo membro. Le formule personalizzate membro vengono archiviate nella tabella della dimensione o in un'altra tabella collegata tramite una relazione di chiave esterna alla tabella della dimensione.  
  
 La proprietà **CustomRollupColumn** di un attributo specifica la colonna che include le formule personalizzate membro per i membri dell'attributo. Se una riga della colonna è vuota, il valore della cella per il membro viene restituito normalmente. Se la formula nella colonna non è valida, si verifica un errore di run-time ogni volta che viene recuperato il valore di una cella che utilizza il membro.  
  
 Prima di poter specificare formule personalizzate membro per un attributo, verificare che nella tabella della dimensione contenente l'attributo o in una tabella direttamente correlata sia disponibile una colonna stringa per l'archiviazione delle formule personalizzate membro. In caso affermativo, è possibile impostare la proprietà **CustomRollupColumn** per un attributo manualmente oppure usare la funzionalità avanzata per l'impostazione di una formula personalizzata membro della Configurazione guidata funzionalità di Business Intelligence per abilitare una formula personalizzata membro per un attributo. Per altre informazioni su come usare questa funzionalità avanzata, vedere [Impostare formule personalizzate membro per gli attributi in una dimensione](../../analysis-services/multidimensional-models/bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md).  
  
## <a name="evaluating-custom-member-formulas"></a>Valutazione delle formule personalizzate membro  
 Le formule personalizzate membro si differenziano dai membri calcolati per vari aspetti. Vengono applicate ai membri esistenti nelle tabelle delle dimensioni e determinano solo il valore del membro. I membri calcolati, viceversa, non vengono archiviati nelle tabelle delle dimensioni e le relative espressioni definiscono sia i dati che i metadati dei membri aggiuntivi inclusi in una dimensione o una gerarchia.  
  
 Le formule personalizzate membro hanno priorità rispetto alle funzioni di aggregazione associate alle misure. Ad esempio, si supponga che, prima dell'impostazione di una formula personalizzata membro, una misura usi la funzione di aggregazione **Sum** che presenta per i membri della dimensione Time i valori riportati di seguito:  
  
-   2003: 2100  
  
    -   Quarter 1: 700  
  
    -   Quarter 2: 500  
  
    -   Quarter 3: 100  
  
    -   Quarter 4: 800  
  
-   2004: 1500  
  
    -   Quarter 1: 600  
  
    -   Quarter 2: 200  
  
    -   Quarter 3: 300  
  
    -   Quarter 4: 400  
  
 Se si utilizza una formula personalizzata membro, il valore del membro è invece specificato dalla formula personalizzata di rollup. Ad esempio, la formula personalizzata membro seguente può essere utilizzata per determinare il valore 450 per il membro figlio Quarter 4 del membro 2004 nella dimensione Time.  
  
```  
Time.[Quarter 3] * 1.5  
```  
  
 Le formule personalizzate membro vengono archiviate in una colonna della tabella della dimensione. Per abilitare le formule personalizzate di rollup, impostare la proprietà **CustomRollupColumn** di un attributo.  
  
 Per applicare una singola espressione MDX a tutti i membri di un attributo, creare un calcolo denominato nella tabella della dimensione che restituisce un'espressione sotto forma di una stringa letterale. Specificare quindi il calcolo denominato nella proprietà **CustomRollupColumn** dell'attributo che si vuole configurare. Un calcolo denominato è una colonna di una tabella di una vista origine dati che restituisce valori di riga definiti da un'espressione SQL. Per altre informazioni sulla creazione di calcoli denominati, vedere [Definire calcoli denominati in una vista origine dati &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
> [!NOTE]  
>  Per applicare un'espressione MDX ai membri di un livello particolare invece che ai membri di tutti i livelli in base a un particolare attributo, è possibile definire l'espressione come script MDX nel livello. Per altre informazioni, vedere [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md).  
  
 Se si utilizzano sia membri calcolati che formule personalizzate di rollup per i membri di un attributo, è importante tenere presente l'ordine di valutazione. I membri calcolati vengono risolti prima delle formule personalizzate di rollup.  
  
## <a name="see-also"></a>Vedere anche  
 [Gli attributi e gerarchie di attributi](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [Impostare formule personalizzate membro per gli attributi in una dimensione](../../analysis-services/multidimensional-models/bi-wizard-custom-member-formulas-for-attributes-in-a-dimension.md)  
  
  
