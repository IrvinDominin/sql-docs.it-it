---
title: Query di definizione dei dati (Data Mining) | Documenti Microsoft
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
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 286d7cbe5d6dbb2fb0b05b937fbd1a304f89aa1e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="data-definition-queries-data-mining"></a>Query di definizione dei dati (Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Per il data mining, la *query di definizione dei dati* della categoria indica le istruzioni DMX o i comandi XMLA usati per eseguire le operazioni seguenti:  
  
-   Creare o modificare oggetti di data mining, ad esempio un modello.  
  
-   Definire l'origine dei dati da utilizzare per il training o per la stima.  
  
-   Esportare o importare modelli e strutture di data mining  
  
 [Creazione di query di definizione dei dati](#bkmk_Create)  
  
-   [Creazione di query di definizione dei dati in SQL Server Data Tools](#bkmk_ssdt)  
  
-   [Query di definizione dei dati in SQL Server Management Studio](#bkmk_SSMS)  
  
 [Generazione dello script di istruzioni per la definizione dei dati](#bkmk_Scripts)  
  
 [Generazione dello script di istruzioni per la definizione dei dati](#bkmk_Export)  
  
##  <a name="bkmk_Create"></a> Creazione di query di definizione dei dati  
 È possibile creare query di definizione dei dati (istruzioni) usando il generatore delle query di stima in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]o tramite la finestra Query DMX in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Le istruzioni DMX per la definizione dei dati fanno parte del linguaggio DDL (Data Definition Language) di Analysis Services.  
  
 Per informazioni sulla sintassi di istruzioni per la definizione dei dati specifiche, vedere [Guida di riferimento a DMX &#40;Data Mining Extensions&#41;](../../dmx/data-mining-extensions-dmx-reference.md).  
  
###  <a name="bkmk_ssdt"></a> Creazione di query di definizione dei dati in SQL Server Data Tools  
 Creazione guidata modello di data mining è lo strumento preferito in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per la creazione e la modifica di modelli e strutture di data mining, nonché per la definizione delle origini dati utilizzate nelle query di stima e per il training.  
  
 Tuttavia, se si desidera conoscere quali istruzioni vengono inviate al server dalla procedura guidata per creare strutture di dati o modelli di data mining, è possibile utilizzare SQL Server Profiler per acquisire le istruzioni per la definizione dei dati. Per altre informazioni, vedere [Usare SQL Server Profiler per il monitoraggio di Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md).  
  
 Per visualizzare le istruzioni usate per la definizione delle origini dati per il training o la stima, è possibile usare la **Visualizzazione SQL** nel generatore delle query di stima. Talvolta, può essere utile per compilare query di base per il training e il testing di modelli utilizzando il generatore delle query di stima, per stabilire la sintassi corretta. È possibile passare quindi alla **Visualizzazione SQL** e modificare manualmente la query. Per altre informazioni, vedere [Modificare manualmente un query di stima](../../analysis-services/data-mining/manually-edit-a-prediction-query.md).  
  
###  <a name="bkmk_SSMS"></a> Query di definizione dei dati in SQL Server Management Studio  
 Per oggetti di data mining, è possibile utilizzare le query di definizione dei dati per effettuare le azioni seguenti:  
  
-   Creare tipi di modelli specifici, ad esempio un modello di clustering o di albero delle decisioni, tramite [CREATE MINING MODEL &#40;DMX&#41;](../../dmx/create-mining-model-dmx.md).  
  
-   Modificare una struttura di data mining esistente aggiungendo un modello o modificando le colonne tramite [ALTER MINING STRUCTURE &#40;DMX&#41;](../../dmx/alter-mining-structure-dmx.md). Si noti che non è possibile modificare un modello di data mining tramite DMX. Vengono aggiunti solo nuovi modelli a una struttura esistente.  
  
-   Effettuare una copia di un modello di data mining e quindi modificarla tramite [SELECT INTO &#40;DMX&#41;](../../dmx/select-into-dmx.md).  
  
-   Definire il set di dati usato per il training di un modello tramite [INSERT INTO &#40;DMX&#41;](../../dmx/insert-into-dmx.md), insieme a una query di origine dati quale OPENROWSET.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] offre modelli di query utili per la creazione di query di definizione dei dati. Per altre informazioni, vedere [Usare i modelli di Analysis Services in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md).  
  
 In generale, nei modelli forniti per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è contenuta solo la definizione della sintassi generale, che è necessario personalizzare digitando nella finestra **Query** o tramite la finestra di dialogo fornita per l'immissione di parametri.  
  
 Per un esempio di come immettere i parametri tramite l'interfaccia, vedere [Creare una query di stima singleton da un modello](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md).  
  
###  <a name="bkmk_Scripts"></a> Generazione dello script di istruzioni per la definizione dei dati  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fornisce più linguaggi di script e di programmazione che è possibile usare per creare o modificare oggetti di data mining o per definire le origini dati.  Anche se DMX è progettato per facilitare le attività di data mining, è possibile utilizzare inoltre sia XMLA sia AMO per modificare oggetti negli script o in codice personalizzato.  
  
 Nel componente aggiuntivo Data mining per Excel sono inclusi anche molti modelli di query, oltre all' **Editor avanzato query**che consente di comporre istruzioni DMX complesse. È possibile compilare una query in modo interattivo e passare a Visualizzazione SQL per acquisire l'istruzione DMX.  
  
##  <a name="bkmk_Export"></a> Esportazione e importazione di modelli  
 È possibile utilizzare le istruzioni per la definizione dei dati in DMX per esportare la definizione di un modello e le relative origini dati e struttura necessarie, e importare quindi tale definizione in un server diverso. L'utilizzo dell'esportazione e dell'importazione è il modo più veloce per spostare modelli e strutture di data mining tra istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Per altre informazioni, vedere [Gestione degli oggetti e delle soluzioni di data mining](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md).  
  
> [!WARNING]  
>  Se il modello è basato sui dati provenienti dall'origine dati di un cubo, non è possibile utilizzare DMX per esportare il modello, è necessario utilizzare invece la funzionalità di backup e ripristino.  
  
##  <a name="bkmk_Tasks"></a> Attività correlate  
 Nella tabella seguente vengono forniti i collegamenti alle attività correlate alle query di definizione dei dati.  
  
|||  
|-|-|  
|Utilizzo di modelli per query DMX.|[Utilizzare i modelli di Analysis Services in SQL Server Management Studio](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|Progettazione di query di tutti i tipi tramite il generatore delle query di stima.|[Creare una Query di stima utilizzando Generatore di Query di stima](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)|  
|Acquisizione delle definizioni di query tramite SQL Server Profiler e utilizzo delle tracce per monitorare [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[Utilizzare SQL Server Profiler per monitorare Analysis Services](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|Informazioni sui linguaggi di scripting e di programmazione forniti per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|[XML for Analysis &#40; XMLA &#41; Riferimento](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)<br /><br /> [Lo sviluppo con Analysis Management Objects &#40; AMO &#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)|  
|Informazioni sulla gestione di modelli in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].|[Esportare e importare oggetti di Data Mining](../../analysis-services/data-mining/export-and-import-data-mining-objects.md)<br /><br /> [ESPORTAZIONE &#40; DMX &#41;](../../dmx/export-dmx.md)<br /><br /> [DMX IMPORTAZIONE &#40; &#41;](../../dmx/import-dmx.md)|  
|Informazioni su OPENROWSET e su altre modalità per eseguire una query sui dati esterni.|[&#60;query origine dati&#62;](../../dmx/source-data-query.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione guidata di Data Mining &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/data-mining-wizard-analysis-services-data-mining.md)  
  
  
