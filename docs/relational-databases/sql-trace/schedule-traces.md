---
title: Pianificare tracce | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-trace
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filters [SQL Server], events
- traces [SQL Server]
- traces [SQL Server], stopping
- events [SQL Server], filters
- scheduling traces [SQL Server]
- traces [SQL Server], scheduling
- stopping traces
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: "24"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6693df4ddf0afbca69ad46f50bbaa49877be4450
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="schedule-traces"></a>Pianificare tracce
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Esistono due modi per pianificare le tracce in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile effettuare le operazioni seguenti:  
  
-   Abilitare una data e un'ora di arresto della traccia  
  
-   Utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per pianificare una traccia.  
  
## <a name="specifying-a-stop-time"></a>Specifica di una data e un'ora di arresto  
 È possibile specificare una data e un'ora di arresto della traccia se si utilizzano le stored procedure di [!INCLUDE[tsql](../../includes/tsql-md.md)] o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. L'impostazione della data e dell'ora di arresto deve essere eseguita durante la configurazione originale della traccia.  
  
## <a name="scheduling-traces-by-using-sql-server-agent"></a>Pianificazione di tracce tramite SQL Server Agent  
 Il metodo migliore per pianificare le tracce consiste nell'avviare la traccia tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e quindi specificare una data e un'ora di arresto per la traccia tramite la stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)]**sp_trace_setstatus** o [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 **Per impostare un filtro basato sulla data e sull'ora di fine per una traccia**  
  
 [Filtrare gli eventi in base all'ora di fine &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Automatizzazione delle attività amministrative &#40;SQL Server Agent&#41;](http://msdn.microsoft.com/library/541ee5ac-2c9f-4b74-b4f0-13b7bd5920b0)  
  
  
