---
title: Creare una Query DMX in SQL Server Management Studio | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: edb3f0ab17369a4a1df4a69d80e07bfa1ff84012
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a>Creare una query DMX in SQL Server Management Studio
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre un set di funzionalità che consentono di creare query di stima, query sul contenuto e query di definizione dei dati su modelli e strutture di data mining.  
  
-   Un generatore di query di stima grafico è disponibile sia in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] che in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]per semplificare il processo di scrittura delle query di stima e il mapping dei set di dati a un modello.  
  
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
  
## <a name="xmla-query-templates"></a>Modelli di query XMLA  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include anche modelli per le query XMLA.  
  
 I tipi di query che è possibile eseguire tramite XMLA e DMX sono parzialmente sovrapposti. Ad esempio, è possibile creare alcune query contenuto del modello tramite DMX o i set di righe dello schema di data mining, ma i set di righe dello schema talvolta contengono informazioni non esposte nelle query contenuto DMX.  
  
 Sono inoltre presenti alcune differenze fondamentali nella modalità di gestione delle operazioni in DMX e in XMLA. Ad esempio, è possibile usare XMLA per eseguire operazioni amministrative, come il backup di un intero database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], ma per eseguire il backup di un solo modello di data mining in DMX è disponibile un comando semplice, [EXPORT &#40;DMX&#41;](../../dmx/export-dmx.md), più indicato allo scopo.  
  
##  <a name="BKMK_Building_Queries"></a> Compilare ed eseguire una query DMX  
  
#### <a name="open-a-new-dmx-query-window"></a>Aprire una nuova finestra Query DMX  
  
1.  Fare clic su **Nuova query** in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]e quindi selezionare **Nuova query DMX di Analysis Server**.  
  
2.  Quando viene visualizzata la finestra di dialogo **Connetti al server** , selezionare l'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] contenente i modelli di data mining da usare.  
  
#### <a name="open-template-explorer"></a>Aprire Esplora modelli  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]scegliere **Esplora modelli** dal menu **Visualizza**.  
  
2.  Fare clic su **Analysis Server** per ottenere una visualizzazione albero dei modelli applicabili a [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
#### <a name="apply-a-template-to-build-a-query"></a>Applicare un modello per compilare una query  
  
-   Fare clic con il pulsante destro del mouse sul tipo di query adatto e scegliere **Apri**.  
  
-   In alternativa, trascinare il modello nell'editor di query.  
  
-   È anche possibile compilare i parametri per la query scegliendo l'opzione **Specifica valori per parametri**dal menu **Query** .  
  
 Per esempi relativi alla creazione di tipi specifici di query dai modelli, vedere gli argomenti seguenti:  
  
 [Creare una Query di stima Singleton da un modello](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
  
 [Creare una Query sul contenuto su un modello di Data Mining](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti query di data mining](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  
