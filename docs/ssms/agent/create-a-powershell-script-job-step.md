---
title: Creare un passaggio di processo di uno script di PowerShell | Microsoft Docs
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
- PowerShell [SQL Server], job steps
- jobs [SQL Server Agent], PowerShell
- job steps [PowerShell]
- SQL Server Agent jobs, PowerShell steps
ms.assetid: 50afcf84-fae0-4eb5-9b0f-f2cf144c1433
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a5c667437e2c5df4ff276f8fbdebb81dab79474f
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="create-a-powershell-script-job-step"></a>Create a PowerShell Script Job Step
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive le procedure per la creazione e la definizione di un passaggio di processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent che esegue uno script di PowerShell in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per creare un passaggio di processo di uno script di PowerShell utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Per creare un passaggio di processo di uno script di PowerShell  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**, creare un nuovo processo oppure fare clic con il pulsante destro del mouse su un processo esistente e quindi scegliere **Proprietà**. Per ulteriori informazioni sulla creazione di un processo, vedere [Creazione di processi](../../ssms/agent/create-jobs.md).  
  
3.  Nella finestra di dialogo **Proprietà processo** fare clic sulla pagina **Passaggi** e quindi su **Nuovo**.  
  
4.  Nella finestra di dialogo **Nuovo passaggio di processo** digitare il nome del passaggio del processo nella casella **Nome passaggio**.  
  
5.  Scegliere **PowerShell** dall'elenco **Tipo**.  
  
6.  Nell'elenco **Esegui come** selezionare l'account proxy con le credenziali che verranno utilizzate dal processo.  
  
7.  Nella casella **Comando** immettere la sintassi dello script di PowerShell che verrà eseguito per il passaggio di processo. In alternativa, è possibile fare clic su **Apri** e selezionare un file contenente la sintassi dello script. Per un esempio di script di PowerShell, vedere di seguito **Utilizzo di Transact-SQL** .  
  
8.  Fare clic sulla pagina **Avanzate** per impostare le opzioni seguenti relative al passaggio di processo: l'azione da eseguire in caso di esito positivo o negativo del passaggio, il numero di tentativi di esecuzione del passaggio che devono essere effettuati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e gli intervalli tra tentativi successivi.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-create-a-powershell-script-job-step"></a>Per creare un passaggio di processo di uno script di PowerShell  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- creates a PowerShell job step that finds the processes
    -- that use more than 1000 MB of memory and kills them  
    USE msdb;  
    GO  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Kills all processes that use more than 1000 MB of memory',  
        @subsystem = N'PowerShell',  
        @command = N'Get-Process | Where-Object { $_.WS -gt 1000MB } | Stop-Process',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per creare un passaggio di processo di uno script di PowerShell**  
  
Usare la classe **JobStep** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell.  
  
