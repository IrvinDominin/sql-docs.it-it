---
title: Oggetto Processi di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ccbf65c2b1d297b8fd36ef75f84a6a8c09b21175
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32950496"
---
# <a name="sql-server-agent-jobs-object"></a>Oggetto Processi di SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazioni **Processi** di SQL Server Agent include contatori delle prestazioni che forniscono informazioni relative ai processi di SQL Server Agent. Nella tabella seguente sono elencati i contatori inclusi nell'oggetto.  
  
 Nella tabella seguente sono illustrati i contatori di **SQLAgent:Processi** .  
  
|nome|Description|  
|----------|-----------------|  
|**Processi attivi**|Questo contatore indica il numero di processi attualmente in esecuzione.|  
|**Processi non riusciti**|Questo contatore indica il numero di processi chiusi con un errore.|  
|**Percentuale processi completati**|Questo contatore indica la percentuale di processi eseguiti completati correttamente.|  
|**Processi attivati/minuto**|Questo contatore indica il numero di processi avviati nell'ultimo minuto.|  
|**Processi in coda**|Questo contatore indica il numero di processi pronti per l'esecuzione in SQL Server Agent, ma la cui esecuzione non è ancora stata avviata.|  
|**Processi completati**|Questo contatore indica il numero di processi chiusi correttamente.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Istanza|Description|  
|--------------|-----------------|  
|**_Total**|Informazioni relative a tutti i processi.|  
|**Avvisi**|Informazioni relative ai processi avviati da avvisi.|  
|**Altri**|Informazioni relative a processi non avviati da avvisi o pianificazioni. In genere, si tratta di processi avviati manualmente tramite **sp_start_job**.|  
|**Pianificazioni**|Informazioni relative ai processi avviati da pianificazioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di processi](http://msdn.microsoft.com/library/69e06724-25c7-4fb3-8a5b-3d4596f21756)   
 [Utilizzo degli oggetti prestazioni](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
