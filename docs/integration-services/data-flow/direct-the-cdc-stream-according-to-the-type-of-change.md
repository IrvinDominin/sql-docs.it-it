---
title: Indirizzare il flusso CDC in base al tipo di modifica | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 37a861b25d578d6c7d7b94b3a2072b7242a5bb51
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>Indirizzare il flusso CDC in base al tipo di modifica
  Per aggiungere e configurare una trasformazione CDC Splitter, il pacchetto deve contenere almeno un'attività Flusso di dati e un'origine CDC.  
  
 Per l'origine CDC aggiunta al pacchetto deve essere selezionata una modalità di elaborazione CDC Net. Per altre informazioni sulla selezione delle modalità di elaborazione, vedere [Editor origine CDC &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/cdc-source-editor-connection-manager-page.md).  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>Per indirizzare il flusso CDC in base al tipo di modifica  
  
1.  In [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]aprire il progetto di [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] che contiene il pacchetto desiderato.  
  
2.  In Esplora soluzioni fare doppio clic sul pacchetto per aprirlo.  
  
3.  Fare clic sulla scheda **Flusso di dati** , quindi trascinare la barra di divisione CDC dalla **Casella degli strumenti**all'area di progettazione.  
  
4.  Connettere l'origine CDC inclusa nel pacchetto alla barra di divisione CDC.  
  
5.  Connettere la barra di divisione CDC a una o più destinazioni. È possibile eseguire la connessione a un massimo di tre output diversi.  
  
6.  Selezionare uno degli output seguenti:  
  
    -   Output di eliminazione: output in cui vengono indirizzate le righe delle modifiche DELETE.  
  
    -   Output di inserimento: output in cui vengono indirizzate le righe delle modifiche INSERT.  
  
    -   Output di aggiornamento: output in cui vengono indirizzate le righe delle modifiche before/after UPDATE e le righe delle modifiche MERGE.  
  
7.  È eventualmente possibile configurare le proprietà avanzate utilizzando la finestra di dialogo **Editor avanzato** .  
  
     La finestra di dialogo **Editor avanzato** contiene le proprietà che è possibile impostare a livello di codice.  
  
     Per aprire la finestra di dialogo **Editor avanzato** :  
  
    -   Nella schermata **Flusso di dati** del progetto di [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] fare clic con il pulsante destro del mouse sulla barra di divisione CDC e scegliere **Visualizza editor avanzato**.  
  
     Per ulteriori informazioni sull'utilizzo della barra di divisione CDC, vedere Componenti CDC per Microsoft SQL Server Integration Services.  
  
## <a name="see-also"></a>Vedere anche  
 [CDC Splitter](../../integration-services/data-flow/cdc-splitter.md)  
  
  
