---
title: Categoria di eventi report di stato | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- progress events [Analysis Services]
- Progress Reports event category
- event classes [Analysis Services], progress reports
ms.assetid: c130f160-28ef-49bc-9ee6-da47dc9aab2a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c90cfbe7e30d0678d13a329737c21f7d45575e22
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="progress-reports-event-category"></a>categoria di eventi di report di stato
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
La categoria di eventi di report di stato include le classi di eventi descritte nella tabella seguente.  
  
|Event Class|ID evento|Description|  
|-----------------|--------------|-----------------|  
|Progress Report Begin|5|Raccoglie tutti gli eventi di inizio dei report di stato dall'avvio della traccia.|  
|Progress Report End|6|Raccoglie tutti gli eventi di fine dei report di stato dall'avvio della traccia.|  
|Progress Report Current|7|Raccoglie tutti gli eventi di report dello stato corrente dall'avvio della traccia. Durante l'elaborazione, ad esempio, i report dello stato corrente includono le informazioni di elaborazione sugli oggetti da elaborare, ad esempio dimensioni, partizioni, cubo e così via.|  
|Progress Report Error|8|Raccoglie tutti gli eventi di errore nei report di stato dall'avvio della traccia.|  
  
 Ogni evento Inizio dei report di stato inizia con un flusso di eventi di stato e viene terminato con un evento Fine dei report di stato. Il flusso può includere un numero qualsiasi di eventi Report dello stato corrente ed Errore nel report di stato.  
  
 Per informazioni sulle colonne associate a ogni classe di evento inclusa nella categoria Report di stato, vedere [Colonne di dati degli eventi di report di stato](../../analysis-services/trace-events/progress-reports-data-columns.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi di traccia di Analysis Services](../../analysis-services/trace-events/analysis-services-trace-events.md)  
  
  
