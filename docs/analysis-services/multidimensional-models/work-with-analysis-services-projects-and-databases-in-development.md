---
title: Lavorare con progetti e database in fase di sviluppo di Analysis Services | Documenti Microsoft
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
ms.assetid: 39cf9166-fa92-40fe-9962-210a52461257
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2315a46f017758da30f2973154bcd2fe451e1748
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="work-with-analysis-services-projects-and-databases-in-development"></a>Lavorare con progetti e database in fase di sviluppo di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]È possibile sviluppare un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database utilizzando [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità progetto o in modalità online.  
  
## <a name="single-developer"></a>Sviluppatore singolo  
 Quando l'intero database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e tutti gli oggetti da cui è costituito vengono sviluppati esclusivamente da un singolo sviluppatore, lo sviluppatore può utilizzare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità progetto o in modalità online in qualsiasi momento durante il ciclo di vita della soluzione di Business Intelligence. In caso di sviluppatore singolo, la scelta delle modalità non riveste importanza critica. Il mantenimento di un file di progetto offline integrato con un sistema di controllo del codice sorgente offre numerosi vantaggi, ad esempio in termini di archiviazione e rollback. Con un singolo sviluppatore, tuttavia, non si presenta il problema della comunicazione delle modifiche con un altro sviluppatore.  
  
## <a name="multiple-developers"></a>Più sviluppatori  
 Quando più sviluppatori lavorano su una soluzione di Business Intelligence, se gli sviluppatori non operano in modalità progetto con controllo del codice sorgente in tutte le circostanze o nella maggior parte di esse si verificheranno problemi. Il controllo del codice sorgente garantisce che due sviluppatori non apportino modifiche allo stesso oggetto contemporaneamente.  
  
 Si supponga ad esempio che uno sviluppatore apporti modifiche ad alcuni oggetti selezionati in modalità progetto e che al tempo stesso un altro sviluppatore apporti una modifica al database distribuito in modalità online. Quando il primo sviluppatore tenta di distribuire il proprio progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , si verificherà un problema. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] rileverà infatti che gli oggetti sono stati modificati nel database distribuito e richiederà allo sviluppatore di sovrascrivere l'intero database, sovrascrivendo le modifiche del secondo sviluppatore. Poiché [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] non è in grado di risolvere il conflitto tra le modifiche all'istanza del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e agli oggetti del progetto da sovrascrivere, l'unica concreta possibilità per lo sviluppatore è eliminare tutte le proprie modifiche e partire da un nuovo progetto basato sulla versione corrente del database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
  
