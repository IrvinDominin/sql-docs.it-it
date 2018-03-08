---
title: Visualizzare o modificare processi | Microsoft Docs
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
- jobs [SQL Server Agent], modifying
- jobs [SQL Server Agent], viewing
- modifying jobs
- viewing jobs
- SQL Server Agent jobs, viewing
- SQL Server Agent jobs, modifying
- displaying jobs
ms.assetid: 57f649b8-190c-4304-abd7-7ca5297deab7
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0a18aeb0dd55575c1c287608af634ce5502004c9
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="view-or-modify-jobs"></a>Visualizzare o modificare processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] È possibile visualizzare tutti i processi creati. Dopo l'esecuzione di un processo, è inoltre possibile visualizzarne la cronologia. Ciò consente di verificare quando un processo è stato eseguito, lo stato dell'intero processo e lo stato di ogni relativo passaggio. È inoltre possibile verificare se in precedenza si sono verificati errori nel processo, l'ultima volta che il processo è stato completato e l'output creato a ogni esecuzione del processo. I membri del ruolo predefinito del server **sysadmin** possono visualizzare o modificare qualsiasi processo, indipendentemente dal proprietario.  
  
> [!NOTE]  
> Affinché sia disponibile una cronologia processo, è necessario che il processo sia stato eseguito almeno una volta. È possibile limitare le dimensioni totali del log di cronologia processo e le dimensioni di ogni processo.  
  
È infine possibile modificare un processo in modo da soddisfare nuovi requisiti. È possibile ad esempio modificare:  
  
-   Opzioni di risposta  
  
-   Pianificazioni  
  
-   Passaggi  
  
-   Proprietario  
  
-   Categoria di processo  
  
-   Server di destinazione (solo processi multiserver)  
  
Per verificare che le modifiche ai processi multiserver siano operative, è necessario inviare le modifiche all'elenco di download, in modo da consentire ai server di destinazione di scaricare nuovamente il processo aggiornato. Per garantire che i server di destinazione dispongano delle definizioni di processo più aggiornate, inviare un'istruzione INSERT dopo l'aggiornamento del processo multiserver, come illustrato di seguito:  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
Per altre informazioni, vedere [sp_purge_jobhistory (Transact-SQL)](http://msdn.microsoft.com/en-us/237f9bad-636d-4262-9bfb-66c034a43e88).  
  
I membri del ruolo predefinito del server **sysadmin** possono visualizzare la definizione o la cronologia nonché modificare qualsiasi processo.  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Descrive la procedura per la visualizzazione dei processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[View a Job](../../ssms/agent/view-a-job.md)|  
|Illustra come visualizzare il log cronologia processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[View the Job History](../../ssms/agent/view-the-job-history.md)|  
|Descrive come eliminare i contenuti del log cronologia processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Clear the Job History Log](../../ssms/agent/clear-the-job-history-log.md)|  
|Descrive come impostare le dimensioni massime per i log cronologia processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Resize the Job History Log](../../ssms/agent/resize-the-job-history-log.md)|  
|Illustra la procedura per la modifica delle proprietà dei processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent.|[Modify a Job](../../ssms/agent/modify-a-job.md)|  
  
## <a name="see-also"></a>Vedere anche  
[sysjobhistory](http://msdn.microsoft.com/en-us/1b1fcdbb-2af2-45e6-bf3f-e8279432ce13)  
  
