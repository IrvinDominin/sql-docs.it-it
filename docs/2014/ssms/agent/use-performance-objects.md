---
title: Usare gli oggetti prestazioni | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, monitoring
- SQL Server Agent service, monitoring
- SQL Server Agent service, performance objects
- SQL Server Agent, performance objects
- performance objects [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- performance counters [SQL Server], SQL Server Agent
- counters [SQL Server], SQL Server Agent
ms.assetid: 830b843a-6b2a-4620-a51b-98358e9fc54b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e934557924dba81604d064d95804b8fd5fb5986d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128461"
---
# <a name="use-performance-objects"></a>Utilizzo degli oggetti prestazioni
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent include oggetti e contatori delle prestazioni che consentono di monitorare lo stato del servizio. Tramite gli oggetti prestazione è possibile utilizzare Performance Monitor, uno strumento Windows che consente di identificare le attività eseguite in background dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. È possibile ad esempio identificare il numero dei processi attivi attualmente in esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e individuare quelli bloccati.  
  
 Per ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installata in un computer sono presenti oggetti prestazione e contatori delle prestazioni del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Agli oggetti prestazione viene assegnato un nome in base all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rappresentata da ciascun oggetto.  
  
 Nella tabella seguente viene illustrata la modalità di assegnazione dei nomi per gli oggetti prestazione del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent:  
  
|Tipo di istanza|Nome oggetto|  
|-------------------|-----------------|  
|Default|**SQLAgent:** *oggetto*:*contatore*|  
|Denominato|**SQLAgent$**<br /> ***instance_name* :** *oggetto*:*contatore*|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include gli oggetti prestazione seguenti per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
|Nome oggetto|Description|  
|-----------------|-----------------|  
|[SQLAgent:Processi](../../relational-databases/performance-monitor/sql-server-agent-jobs-object.md)|Informazioni sulle prestazioni relative a processi avviati, alle percentuali di processi completati e allo stato corrente|  
|[SQLAgent:JobSteps](../../relational-databases/performance-monitor/sql-server-agent-jobsteps-object.md)|Informazioni sullo stato relative ai passaggi di processo|  
|[SQLAgent:Avvisi](../../relational-databases/performance-monitor/sql-server-agent-alerts-object.md)|Informazioni sul numero di avvisi e notifiche|  
|[SQLAgent:Statistiche](../../relational-databases/performance-monitor/sql-server-agent-statistics-object.md)|Informazioni generali sulle prestazioni|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [Avviare il Monitoraggio di sistema &#40;Windows&#41;](../../relational-databases/performance/start-system-monitor-windows.md)  
  
  
