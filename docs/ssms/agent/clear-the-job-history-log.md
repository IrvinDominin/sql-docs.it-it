---
title: Cancellare il contenuto del log di cronologia processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- clearing job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 34b9398a-c409-4040-8ea1-0deceb18f961
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba8542dbff7d4dedfac9ac3e43af6ac077dc3e35
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="clear-the-job-history-log"></a>Cancellare il contenuto del log di cronologia processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come eliminare il contenuto del log della cronologia processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] o SQL Server Management Objects.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per cancellare il contenuto del log di cronologia processo utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-clear-the-job-history-log"></a>Per cancellare il contenuto del log di cronologia processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent**e quindi espandere **Processi**.  
  
3.  Fare clic con il pulsante destro del mouse su un processo e scegliere **Visualizza cronologia**.  
  
4.  Nel **Visualizzatore file di log**selezionare il processo di cui si desidera cancellare la cronologia e quindi eseguire una delle operazioni seguenti:  
  
    -   Fare clic su **Elimina**e quindi su **Elimina tutta la cronologia** nella finestra di dialogo **Elimina cronologia** . È possibile eliminare tutta la cronologia processo oppure solo quella precedente a una data specificata. Per rimuovere tutta la cronologia processo, fare clic su **Elimina tutta la cronologia**. Per rimuovere solo i log cronologia processo più vecchi, fare clic su **Elimina la cronologia precedente a**e quindi specificare una data.  
  
    -   Fare clic su **Stato processo** se si desidera cancellare il contenuto del log della cronologia di un processo multiserver. Fare clic su **Processo**, selezionare il nome di un processo e quindi fare clic su **Visualizza cronologia processi remoti**.  
  
5.  Fare clic su **Elimina**.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-clear-the-job-history-log"></a>Per cancellare il contenuto del log di cronologia processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- example removes the history for a job named NightlyBackups.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_purge_jobhistory  
        @job_name = N'NightlyBackups' ;  
    GO  
    ```  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per cancellare il contenuto del log di cronologia processo**  
  
Usare il metodo **PurgeJobHistory** della classe **JobServer** tramite un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
