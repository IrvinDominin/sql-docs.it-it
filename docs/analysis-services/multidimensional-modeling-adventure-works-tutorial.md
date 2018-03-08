---
title: Modellazione multidimensionale (esercitazione di Adventure Works) | Documenti Microsoft
ms.custom: 
ms.date: 02/13/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Active
ms.openlocfilehash: af9371e71223eedc44b7b7ec8cbeb3ab20423da8
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a>Modellazione multidimensionale (esercitazione di AdventureWorks)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Introduzione all'esercitazione [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial. In questa esercitazione viene descritto come utilizzare [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] per sviluppare e distribuire un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] utilizzando la società fittizia [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] per tutti gli esempi.  
  
## <a name="what-you-learn"></a>Informazioni  
In questa esercitazione verranno illustrate le operazioni seguenti:  
  
-   Come definire origini dati, viste origine dati, dimensioni, attributi, relazioni tra attributi, gerarchie e cubi in un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] all'interno di [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].  
  
-   Come visualizzare dati di dimensioni e cubi distribuendo il progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]e come elaborare gli oggetti distribuiti per popolarli con i dati dell'origine dati sottostante.  
  
-   Come modificare le misure, le dimensioni, le gerarchie, gli attributi e i gruppi di misure nel progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e come distribuire le modifiche incrementali al cubo distribuito nel server di sviluppo.  
  
-   Come definire calcoli, indicatori di prestazioni chiave (KPI), azioni, prospettive, traduzioni e ruoli di sicurezza in un cubo.  
  
Con questa esercitazione viene fornita una descrizione dello scenario in modo da comprendere meglio il contesto di queste lezioni. Per ulteriori informazioni, vedere [Analysis Services Tutorial Scenario](../analysis-services/analysis-services-tutorial-scenario.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
Per completare tutte le lezioni di questa esercitazione sono necessari dati di esempio, file di progetto di esempio e software specifici. Per istruzioni su come trovare e installare i prerequisiti per questa esercitazione, vedere [Installare dati di esempio e progetti per l'esercitazione di modellazione multidimensionale di Analysis Services](../analysis-services/install-sample-data-and-projects.md).  
  
Per completare questa esercitazione sono inoltre necessarie le autorizzazioni seguenti:  
  
-   È necessario essere membro del gruppo Administrators nel computer locale di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] o membro del ruolo di amministrazione del server nell'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
-   È necessario avere autorizzazioni di lettura di **AdventureWorksDW** database di esempio. Questo database di esempio è valido per la versione [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] .  
  
## <a name="lessons"></a>Lezioni  
L'esercitazione include le lezioni seguenti.  
  
|Lezione|Tempo stimato per il completamento|  
|----------|------------------------------|  
|[Lezione 1: Definizione di una vista origine dati all'interno di un'analisi di progetto di servizi](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|15 minuti|  
|[Lezione 2: Definizione e distribuzione di un cubo](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)|30 minuti|  
|[Lezione 3: Modifica di misure, attributi e gerarchie](../analysis-services/lesson-3-modifying-measures-attributes-and-hierarchies.md)|45 minuti|  
|[Lezione 4: Definizione di attributo avanzato e proprietà dimensione](../analysis-services/lesson-4-defining-advanced-attribute-and-dimension-properties.md)|120 minuti|  
|[Lezione 5: Definizione delle relazioni tra dimensioni e gruppi di misure](../analysis-services/lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|45 minuti|  
|[Lezione 6: Definizione di calcoli](../analysis-services/lesson-6-defining-calculations.md)|45 minuti|  
|[Lezione 7: Definizione di indicatori di prestazioni chiave &#40; Gli indicatori KPI &#41;](../analysis-services/lesson-7-defining-key-performance-indicators-kpis.md)|30 minuti|  
|[Lezione 8: Definizione di azioni](../analysis-services/lesson-8-defining-actions.md)|30 minuti|  
|[Lezione 9: Definizione di prospettive e traduzioni](../analysis-services/lesson-9-defining-perspectives-and-translations.md)|30 minuti|  
|[Lezione 10: Definizione dei ruoli amministrativi](../analysis-services/lesson-10-defining-administrative-roles.md)|15 minuti|  
  
> [!NOTE]  
> Il database del cubo che verrà creato in questa esercitazione è una versione semplificata di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] progetto di modello multidimensionale che fa parte dei database di esempio Adventure Works disponibili per il download su GitHub. La versione per l'esercitazione del database multidimensionale Adventure Works è semplificata per focalizzare maggiormente l'attenzione sulle specifiche competenze con cui si desidera subito familiarizzare. Dopo avere completato l'esercitazione, esplorare il progetto di modello multidimensionale per proprio conto per accrescere la comprensione della modellazione multidimensionale in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
## <a name="next-step"></a>Passaggio successivo  
Per iniziare questa esercitazione, passare alla prima lezione: [Lezione 1: Definizione di una vista origine dati in un progetto di Analysis Services](../analysis-services/lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).  
  
  
  
