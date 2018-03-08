---
title: "Monitorare le attività del processo | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, monitoring
- jobs [SQL Server Agent], monitoring
- monitoring [SQL Server], jobs
- activity monitoring [SQL Server Agent]
- monitoring [SQL Server], SQL Server Agent
- monitoring [SQL Server Agent]
- SQL Server Agent Job Activity Monitor
- SQL Server Agent jobs, monitoring
- performance [SQL Server], jobs
- current activity
ms.assetid: 71cb432b-631d-4b8b-9965-e731b3d8266d
caps.latest.revision: "6"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b25b8b95fa950f7764272d2e2a47ebea4e26a78f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="monitor-job-activity"></a>Monitoraggio delle attività del processo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Per eseguire il monitoraggio dell'attività corrente di tutti i processi definiti in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], è possibile usare Monitoraggio attività processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.  
  
## <a name="sql-server-agent-sessions"></a>Sessioni di SQL Server Agent  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent crea una nuova sessione ogni volta che viene avviato. Quando viene creata una nuova sessione, la tabella **sysjobactivity** del database **msdb** viene popolata con tutti i processi esistenti definiti. Al riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, nella tabella viene mantenuta l'ultima attività relativa ai processi. Ogni sessione registra l'attività dei processi normale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, dall'inizio al termine del processo. Le informazioni relative alle sessioni sono archiviate nella tabella **syssessions** del database **msdb** .  
  
## <a name="job-activity-monitor"></a>Monitoraggio attività processi  
Monitoraggio attività processi consente di visualizzare la tabella **sysjobactivity** tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]. È possibile visualizzare tutti i processi del server oppure definire filtri che consentono di limitare il numero dei processi visualizzati. È inoltre possibile ordinare le informazioni relative ai processi facendo clic su un'intestazione di colonna nella griglia di **Attività processi agente** . Ad esempio, se si seleziona l'intestazione di colonna **Ultima esecuzione** , i processi verranno visualizzati nell'ordine in cui sono stati eseguiti l'ultima volta. Se si fa di nuovo clic sull'intestazione di colonna, i processi verranno ordinati in ordine crescente o decrescente in base alla data dell'ultima esecuzione.  
  
Tramite Monitoraggio attività processi è possibile eseguire le attività seguenti:  
  
-   Avviare e arrestare i processi.  
  
-   Visualizzare le proprietà dei processi.  
  
-   Visualizzare la cronologia di un processo specifico.  
  
-   Aggiornare manualmente le informazioni contenute nella griglia di **Attività processi agente** oppure impostare un intervallo di aggiornamento automatico facendo clic su **Visualizza impostazioni di aggiornamento**.  
  
Monitoraggio attività processi consente di verificare quali processi sono stati pianificati per l'esecuzione, gli ultimi risultati dei processi eseguiti durante la sessione corrente e quali processi sono in esecuzione o sono inattivi. Se il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent viene interrotto in modo imprevisto, è possibile individuare i processi che erano in esecuzione controllando la sessione precedente di Monitoraggio attività processi.  
  
Per aprire Monitoraggio attività processi, espandere **SQL Server Agent** in Esplora oggetti di [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] , fare clic con il pulsante destro del mouse su **Monitoraggio attività processi**e scegliere **Visualizza attività processi**.  
  
Per visualizzare l'attività dei processi della sessione corrente è inoltre possibile usare la stored procedure **sp_help_jobactivity**.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Viene illustrato come visualizzare lo stato di runtime dei processi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Visualizza attività processi](../../ssms/agent/view-job-activity.md)|  
  
## <a name="see-also"></a>Vedere anche  
[Visualizza attività processi](../../ssms/agent/view-job-activity.md)  
[sysjobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/fd17cac9-5d1f-4b44-b2dc-ee9346d8bf1e)  
[syssessions (Transact-SQL)](http://msdn.microsoft.com/en-us/187819b6-c7f4-4a26-b74c-0a89e96695cf)  
[sp_help_jobactivity (Transact-SQL)](http://msdn.microsoft.com/en-us/d344864f-b4d3-46b1-8933-b81dec71f511)  
  
