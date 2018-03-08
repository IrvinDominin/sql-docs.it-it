---
title: 'Panoramica: Esportazione di dati (Master Data Services) | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting data [Master Data Services]
- subscription views [Master Data Services]
- subscription views [Master Data Services], about subscription views
ms.assetid: 8b74409a-ea70-45f8-84c7-da6905e4901a
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1d2a7c7eccfffebd6e3d4000b302c1f9241ddc9d
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="overview-exporting-data-master-data-services"></a>Panoramica: Esportazione di dati (Master Data Services)
  Quest'articolo illustra i tipi di formati delle viste sottoscrizioni e descrive come determinare se è necessario modificare le viste a causa di modifiche agli oggetti modello.  
  
 Viene creata una vista sottoscrizioni per esportare i dati di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] in un sistema di sottoscrizione, ad esempio [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il sistema di sottoscrizione viene usato per visualizzare i dati nel database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Per informazioni su come creare la vista sottoscrizioni, vedere [Creare una vista sottoscrizioni per esportare i dati &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)  
  
 Per altre informazioni sulle viste, vedere [Viste](../relational-databases/views/views.md).  
  
## <a name="subscription-view-formats"></a>Formati di vista sottoscrizioni  
 Quando si crea una vista in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], è possibile effettuare una scelta da un set di formati di viste standard disponibili in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Questi formati possono essere utilizzati per creare viste in cui sono visualizzati:  
  
-   Tutti i membri foglia e i relativi attributi.  
  
-   Tutti i membri consolidati e i relativi attributi.  
  
-   Tutte le raccolte e i relativi attributi.  
  
-   I membri aggiunti in modo esplicito a una raccolta.  
  
-   I membri in una gerarchia derivata, in formato padre-figlio o a livelli.  
  
-   I membri in tutte le gerarchie esplicite per un'entità, in formato padre-figlio o a livelli.  
  
## <a name="subscription-views-can-become-out-of-date"></a>Le viste delle sottoscrizioni possono diventare non aggiornate  
 Dopo avere creato una vista sottoscrizioni per un'entità o una gerarchia, le modifiche apportate agli oggetti modello associati non vengono applicate automaticamente nella vista. Può essere inoltre necessario rigenerare una vista sottoscrizioni in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] per applicare le modifiche apportate a oggetti modello. La colonna **Modificato** nella pagina **Esporta** viene aggiornata a **Vero** quando gli oggetti modello cambiano. **Vero** indica che è necessario modificare la vista sottoscrizioni e salvarla, in modo da rigenerarla.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Creare una vista sottoscrizioni dei dati master.|[Creare una vista sottoscrizioni per esportare i dati &#40;Master Data Services&#41;](../master-data-services/create-a-subscription-view-to-export-data-master-data-services.md)|  
|Eliminare una vista sottoscrizioni esistente.|[Eliminare una vista sottoscrizioni &#40;Master Data Services&#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)|  
  
## <a name="related-content"></a>Contenuto correlato  
  
-   [Formati di vista sottoscrizioni &#40;Master Data Services&#41;](../master-data-services/subscription-view-formats-master-data-services.md)  
  
-   [Viste](../relational-databases/views/views.md)  
  
  
