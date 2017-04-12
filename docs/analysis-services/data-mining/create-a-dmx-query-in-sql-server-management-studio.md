---
title: "Creare una query DMX in SQL Server Management Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli [Analysis Services], query"
  - "SQL Server Management Studio [Analysis Services], query DMX"
  - "stime [Analysis Services], query di stima DMX"
  - "stime (DMX)"
  - "query di stima [DMX]"
  - "query [DMX], query di stima"
  - "modelli di data mining [Analysis Services], DMX"
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
caps.latest.revision: 43
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 43
---
# Creare una query DMX in SQL Server Management Studio
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre un set di funzionalità che consentono di creare query di stima, query sul contenuto e query di definizione dei dati su modelli e strutture di data mining.  
  
-   Un generatore di query di stima grafico è disponibile sia in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] che in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per semplificare il processo di scrittura delle query di stima e il mapping dei set di dati a un modello.  
  
-   I modelli di query forniti in Esplora modelli avviano rapidamente la creazione di molti tipi di query DMX, tra cui molti tipi di query di stima. Vengono forniti modelli per query contenuto, query che utilizzano set di dati nidificati, query che restituiscono case dalla struttura di data mining e anche query di definizione dei dati.  
  
-   In Visualizzatore metadati nei riquadri delle query MDX e DMX è presente un elenco di modelli e strutture disponibili che è possibile trascinare nel generatore di query, nonché un elenco di funzioni DMX. Questa funzionalità consente di ottenere con facilità i nomi degli oggetti corretti, senza doverli digitare.  
  
 In questo argomento viene illustrato come compilare una query DMX tramite Visualizzatore metadati e l'editor di query DMX.  
  
##  <a name="BKMK_Templates"></a> Modelli di query DMX  
 I modelli per la creazione delle query DMX di base sono disponibili in Esplora modelli. La cartella **DMX** contiene modelli di data mining, divisi nelle categorie seguenti:  
  
-   **Contenuto del modello**  
  
-   **Gestione del modello**  
  
-   **Query di stima**  
  
-   **Contenuto della struttura**  
  
 È inoltre possibile creare modelli personalizzati, per query o comandi eseguiti frequentemente.  
  
## Modelli di query XMLA  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include anche modelli per le query XMLA.  
  
 I tipi di query che è possibile eseguire tramite XMLA e DMX sono parzialmente sovrapposti. Ad esempio, è possibile creare alcune query contenuto del modello tramite DMX o i set di righe dello schema di data mining, ma i set di righe dello schema talvolta contengono informazioni non esposte nelle query contenuto DMX.  
  
 Sono inoltre presenti alcune differenze fondamentali nella modalità di gestione delle operazioni in DMX e in XMLA. Ad esempio, è possibile usare XMLA per eseguire operazioni amministrative, come il backup di un intero database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ma per eseguire il backup di un solo modello di data mining in DMX è disponibile un comando semplice, [EXPORT &#40;DMX&#41;](../../dmx/export-dmx.md), più indicato allo scopo.  
  
##  <a name="BKMK_Building_Queries"></a> Compilare ed eseguire una query DMX  
  
#### Aprire una nuova finestra Query DMX  
  
1.  Fare clic su **Nuova query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi selezionare **Nuova query DMX di Analysis Server**.  
  
2.  Quando viene visualizzata la finestra di dialogo **Connetti al server**, selezionare l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente i modelli di data mining da usare.  
  
#### Aprire Esplora modelli  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] scegliere **Esplora modelli** dal menu **Visualizza**.  
  
2.  Fare clic su **Analysis Server** per ottenere una visualizzazione albero dei modelli applicabili a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
#### Applicare un modello per compilare una query  
  
-   Fare clic con il pulsante destro del mouse sul tipo di query adatto e scegliere **Apri**.  
  
-   In alternativa, trascinare il modello nell'editor di query.  
  
-   È anche possibile compilare i parametri per la query scegliendo l'opzione **Specifica valori per parametri** dal menu **Query**.  
  
 Per esempi relativi alla creazione di tipi specifici di query dai modelli, vedere gli argomenti seguenti:  
  
 [Creare una query di stima singleton da un modello](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
  
 [Creare una query sul contenuto di un modello di data mining](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
  
## Vedere anche  
 [Strumenti query di data mining](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [Guida di riferimento a DMX &#40;Data Mining Extensions&#41;](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  