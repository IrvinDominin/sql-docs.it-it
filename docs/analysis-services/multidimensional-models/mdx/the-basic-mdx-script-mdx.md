---
title: "Script MDX di base (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "script MDX predefiniti"
  - "istruzioni [MDX]"
  - "espressioni [MDX], script"
  - "script [MDX], informazioni"
ms.assetid: 83d9afda-7d34-42b5-8f28-20172a905f23
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 27
---
# Script MDX di base (MDX)
  In [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] il processo di calcolo per un cubo è definito da uno script MDX (Multidimensional Expressions). Esistono due tipi di script MDX:  
  
 **Script MDX predefinito**  
 Quando si crea un cubo, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea uno script MDX predefinito per tale cubo. Lo script definisce una sessione di calcolo per l'intero cubo.  
  
 **Script MDX definito dall'utente**  
 Dopo la creazione di un cubo è possibile aggiungervi script MDX definiti dall'utente che estendono le capacità di calcolo del cubo.  
  
## Script MDX predefinito  
 Lo script MDX predefinito creato da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] quando si definisce un cubo contiene una sola istruzione CALCULATE, che si trova all'inizio dello script e indica che l'intero cubo dovrà essere calcolato durante la prima sessione di calcolo.  
  
 Lo script MDX predefinito contiene anche i comandi script che creano i set denominati, le assegnazioni e i membri calcolati creati in Progettazione cubi:  
  
-   [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] aggiunge direttamente i comandi script allo script MDX predefinito.  
  
-   Per ogni set denominato presente nel cubo, esiste un'istruzione CREATE SET corrispondente nello script MDX predefinito.  
  
-   Per ogni membro calcolato definito nel cubo, esiste un'istruzione CREATE MEMBER corrispondente nello script MDX predefinito.  
  
 È possibile controllare l'ordine dei comandi script, dei set denominati e dei membri calcolati nello script MDX predefinito usando la scheda **Calcoli** di Progettazione cubi. Per altre informazioni sulla definizione dei calcoli archiviati nello script MDX predefinito, vedere [Calcoli nei modelli multidimensionali](../../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md).  
  
 Se a un cubo non è associato alcuno script MDX, il cubo utilizzerà lo script MDX predefinito. Un cubo deve essere associato ad almeno uno script MDX, perché si basa sullo script MDX per determinare il comportamento di calcolo. In altre parole, un cubo non associato a uno script MDX o associato a uno script MDX vuoto non è in grado di calcolare alcuna cella. Se si creano cubi a livello di programmazione, utilizzando comandi ASSL (Analysis Services Scripting Language) o tramite AMO (Analysis Management Objects), è consigliabile creare anche uno script MDX predefinito contenente una singola istruzione CALCULATE per il cubo.  
  
## Contenuto degli script MDX  
 Uno script MDX può contenere le istruzioni e le espressioni seguenti:  
  
 Tutte le istruzioni di scripting MDX  
 Negli script MDX le istruzioni di scripting MDX controllano il contesto e l'ambito dei calcoli e gestiscono il comportamento delle altre istruzioni contenute nello script MDX. Questa categoria include le istruzioni seguenti:  
  
-   [CALCULATE](../Topic/CALCULATE%20Statement%20\(MDX\).md)  
  
-   [FREEZE](../Topic/FREEZE%20Statement%20\(MDX\).md)  
  
-   [SCOPE](../Topic/SCOPE%20Statement%20\(MDX\).md)  
  
 Per altre informazioni sulle istruzioni di scripting MDX, vedere [Istruzioni di scripting MDX &#40;MDX&#41;](../../../mdx/mdx-scripting-statements-mdx.md).  
  
 [CREATE MEMBER](../Topic/CREATE%20MEMBER%20Statement%20\(MDX\).md)  
 L'istruzione CREATE MEMBER crea membri calcolati. Per altre informazioni sulla creazione di membri calcolati, vedere [Compilazione di membri calcolati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-calculated-members-in-mdx-mdx.md).  
  
 [CREATE SET](../Topic/CREATE%20SET%20Statement%20\(MDX\).md)  
 L'istruzione CREATE SET crea set denominati. Per altre informazioni sulla procedura per creare set denominati, vedere [Compilazione di set denominati in MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/building-named-sets-in-mdx-mdx.md).  
  
 Istruzioni condizionali  
 Le istruzioni condizionali aggiungono logica condizionale agli script MDX. Questa categoria include le istruzioni [CASE](../../../mdx/case-statement-mdx.md) e [IF](../Topic/IF%20Statement%20%20\(MDX\).md).  
  
 Espressioni di assegnazione  
 Un'espressione di assegnazione assegna un'espressione, ad esempio un valore, a un sottocubo soggetto a vincoli. Un'espressione di sottocubo soggetta a vincoli è una raccolta di espressioni set soggette a vincoli che definisce i limiti di un sottocubo in uno script MDX. Nei frammenti di codice seguenti viene illustrata la sintassi di un'espressione di sottocubo soggetta a vincoli:  
  
```  
<Constrained subcube> ::= (   
    ( <Constrained set> [<Crossjoin operator> <Constrained set>...] |  
    <ROOT function> |  
    <TREE function> |  
    LEAVES() |  
    * ) [, <Constrained subcube>...]  
<Constrained set> ::=   
    <Natural hierarchy>.MEMBERS |   
    <Natural hierarchy>.LEVEL(<numeric expression>).MEMBERS |   
    { <Natural hierarchy member> } |   
    DESCENDANTS( <Natural hierarchy member>, <Level expression>, ( SELF | AFTER | SELF_AND_AFTER ) ) |   
    DESCENDANTS( <Natural hierarchy member>, , LEAVES )  
<Natural hierarchy> ::= <Hierarchy identifier>  
<Natural hierarchy member> ::= <Natural hierarchy>.<identifier>[.<identifier>...]  
```  
  
## Vedere anche  
 [Guida di riferimento al linguaggio MDX &#40;MDX&#41;](../../../mdx/mdx-language-reference-mdx.md)   
 [Nozioni fondamentali sullo scripting MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)  
  
  