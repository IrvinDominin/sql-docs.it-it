---
title: "Editor origine CDC (pagina Colonne) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.designer.cdcsource.columns.f1"
ms.assetid: bcf3030e-98d8-4445-967c-33c3f8ecb4fc
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# Editor origine CDC (pagina Colonne)
  Usare la pagina **Colonne** della finestra di dialogo **CDC Source Editor (Editor origine CDC)** per eseguire il mapping tra una colonna di output e ogni colonna esterna (di origine).  
  
 Per ulteriori informazioni sull'origine CDC, vedere [CDC Source](../../integration-services/data-flow/cdc-source.md).  
  
## Elenco attività  
 **Per aprire CDC Source Editor (pagina Colonne)**  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], aprire il pacchetto [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene l'origine CDC.  
  
2.  Nella scheda **Flusso di dati** fare doppio clic sull'origine CDC.  
  
3.  In **CDC Source Editor**, fare clic su **Colonne**.  
  
## Opzioni  
 **Colonne esterne disponibili**  
 Elenco delle colonne esterne disponibili nell'origine dei dati. Non è possibile utilizzare questa tabella per l'aggiunta o l'eliminazione di colonne. Selezionare le colonne da utilizzare nell'origine. Le colonne scelte vengono aggiunte all'elenco **Colonna esterna** nell'ordine in cui vengono selezionate.  
  
 **Colonna esterna**  
 Una vista delle colonne esterne (di origine) nell'ordine in cui vengono presentate durante la configurazione di componenti che utilizzano i dati dell'origine CDC. Per modificare questo ordine, deselezionare innanzitutto le colonne selezionate nell'elenco **Colonne esterne disponibili** , quindi selezionare le colonne esterne nell'elenco secondo un ordine diverso. Le colonne scelte vengono aggiunte all'elenco **Colonna esterna** nell'ordine in cui vengono selezionate.  
  
 **Colonna di output**  
 Consente di immettere un nome univoco per ogni colonna di output. Per impostazione predefinita viene suggerito il nome della colonna esterna (di origine) selezionata. È comunque possibile scegliere qualsiasi nome descrittivo univoco. Il nome immesso viene visualizzato in Progettazione SSIS.  
  
## Vedere anche  
 [Editor origine CDC &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md)   
 [Editor origine CDC &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/cdc-source-editor-error-output-page.md)  
  
  