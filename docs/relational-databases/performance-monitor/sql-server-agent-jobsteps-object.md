---
title: "Oggetto JobSteps di SQL Server Agent | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JobSteps - oggetto"
  - "SQLAgent:JobSteps"
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# Oggetto JobSteps di SQL Server Agent
  L'oggetto prestazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JobSteps **di** Agent contiene contatori delle prestazioni che forniscono informazioni relative ai passaggi di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Nella tabella seguente sono elencati i contatori inclusi nell'oggetto.  
  
 Nella tabella seguente sono inclusi i contatori **SQLAgent:Passaggi processi** .  
  
|Nome|Descrizione|  
|----------|-----------------|  
|**Passaggi attivi**|In questo contatore viene visualizzato il numero di passaggi del processo attualmente in esecuzione.|  
|**Passaggi in coda**|In questo contatore viene visualizzato il numero di passaggi del processo pronti per l'esecuzione in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, ma la cui esecuzione non è ancora stata avviata.|  
|**Totale tentativi passaggio**|In questo contatore viene visualizzato il numero totale di tentativi di esecuzione di un passaggio del processo in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal momento dell'ultimo riavvio del server.|  
  
 Per ogni contatore nell'oggetto sono disponibili le istanze seguenti:  
  
|Istanza|Descrizione|  
|--------------|-----------------|  
|**_Total**|Informazioni su tutti i passaggi del processo.|  
|**ActiveScripting**|Informazioni per i passaggi del processo che utilizzano il sottosistema **ActiveScripting** .|  
|**ANALYSISCOMMAND**|Informazioni per i passaggi del processo che utilizzano il sottosistema ANALYSISCOMMAND.|  
|**ANALYSISQUERY**|Informazioni per i passaggi del processo che utilizzano il sottosistema ANALYSISQUERY.|  
|**CmdExec**|Informazioni per i passaggi del processo che utilizzano il sottosistema **CmdExec** .|  
|**Distribuzione**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Distribution** .|  
|**Dts**|Informazioni per i passaggi del processo che utilizzano il sottosistema [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|**LogReader**|Informazioni per i passaggi del processo che utilizzano il sottosistema **LogReader** .|  
|**Merge**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Merge** .|  
|**PowerShell**|Informazioni per i passaggi del processo che utilizzano il sottosistema **PowerShell** .|  
|**QueueReader**|Informazioni per i passaggi del processo che utilizzano il sottosistema **QueueReader** .|  
|**Snapshot**|Informazioni per i passaggi del processo che utilizzano il sottosistema **Snapshot** .|  
|**TSQL**|Informazioni per i passaggi del processo che comportano l'esecuzione di [!INCLUDE[tsql](../../includes/tsql-md.md)].|  
  
## Vedere anche  
 [Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)   
 [Utilizzo degli oggetti prestazioni](../../ssms/agent/use-performance-objects.md)   
 [Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  