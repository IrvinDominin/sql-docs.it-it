---
title: Lavorare con progetti e database nell'ambiente di produzione di Analysis Services | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: af715c072f35ebee79a126eed58308d1b1f27629
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-production"></a>Lavorare con progetti e database nell'ambiente di produzione di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dopo aver sviluppato e distribuito il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del database del [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] del progetto a un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] istanza, è necessario decidere come si desidera apportare modifiche agli oggetti nel database distribuito. Alcune modifiche, ad esempio quelle relative ai ruoli di sicurezza, al partizionamento e alle impostazioni di archiviazione, possono essere apportate mediante [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Altre modifiche, ad esempio l'aggiunta di attributi o gerarchie definite dall'utente, possono essere apportate soltanto usando [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]in modalità progetto o in modalità online.  
  
 Non appena si apporta una modifica a un database distribuito di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online, il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usato per la distribuzione risulta obsoleto. Se uno sviluppatore apporta qualsiasi modifica all'interno del progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e tenta di distribuire il progetto modificato, verrà richiesto di sovrascrivere l'intero database. In caso di sovrascrittura dell'intero database, è inoltre necessario eseguirne l'elaborazione. Il problema risulta ancora più complesso se le modifiche apportate direttamente al database distribuito dal personale di produzione non sono state comunicate al team di sviluppo, poiché non sarà in grado di comprendere il motivo per cui le relative modifiche non vengono più riportate nel database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Per evitare i problemi intrinseci di questa situazione, è possibile utilizzare gli strumenti di SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in diversi modi.  
  
-   Metodo 1: ogni volta che si apporta una modifica a una versione di produzione di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , usare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per creare un nuovo progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] basato sulla versione modificata del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Questo nuovo progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] può essere archiviato nel sistema di controllo del codice sorgente come copia master del progetto. Questo metodo è applicabile indipendentemente dal fatto che la modifica venga apportata al database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online.  
  
-   Metodo 2: apportare modifiche alla versione di produzione di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] soltanto usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità progetto. Questo metodo consente di utilizzare le opzioni disponibili nella Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per mantenere le modifiche apportate da [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ad esempio per i ruoli di sicurezza e le impostazioni di archiviazione. È così possibile garantire che vengano mantenute le impostazioni relative alla progettazione nel file di progetto (ignorando impostazioni di archiviazione e ruoli di sicurezza) e che per le impostazioni di archiviazione e i ruoli di sicurezza venga utilizzato il server online.  
  
-   Metodo 3: apportare modifiche alla versione di produzione di un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] soltanto usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online. Poiché entrambi gli strumenti utilizzano solo lo stesso server online, non è possibile ottenere una diversa versione non sincronizzata.  
  
  
