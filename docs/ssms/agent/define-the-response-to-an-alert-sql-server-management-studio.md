---
title: Definire la risposta a un avviso (SQL Server Management Studio) | Microsoft Docs
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
- SQL Server Agent, alerts
- alerts [SQL Server], responding to
- responding to alerts
ms.assetid: c86ca6eb-c59f-46e9-bc32-d474e7c3b170
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7188c78647298e2eb382fded68e9c5bfd1a44bc6
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="define-the-response-to-an-alert-sql-server-management-studio"></a>Definizione della risposta a un avviso (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento viene descritta la procedura per la definizione delle modalità di risposta di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] agli avvisi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] o [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per definire la risposta a un avviso tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   Le opzioni Cercapersone e **net send** verranno rimosse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent in una versione futura di [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Evitare pertanto di utilizzarle in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui sono state implementate.  
  
-   Si noti che per inviare notifiche tramite posta elettronica e cercapersone agli operatori, è necessario configurare SQL Server Agent per l'utilizzo di Posta elettronica database. Per ulteriori informazioni, vedere [Procedura: Assegnazione di avvisi a un operatore (SQL Server Management Studio)](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] è incluso un semplice strumento grafico per la gestione dei processi, che è lo strumento consigliato per la creazione e la gestione dell'infrastruttura dei processi.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Solo i membri del ruolo predefinito del server **sysadmin** possono definire la risposta a un avviso.  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-define-the-response-to-an-alert"></a>Per definire la risposta a un avviso  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server contenente l'avviso per cui si desidera definire una risposta.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Avvisi** .  
  
4.  Fare clic con il pulsante destro del mouse sull'avviso per cui si desidera definire una risposta e selezionare **Proprietà**.  
  
5.  Nella finestra di dialogo *Proprietà dell'avviso***nome_avviso** selezionare **Risposta** in **Seleziona una pagina**.  
  
6.  Selezionare la casella di controllo **Esegui processo** e, dall'elenco sottostante la casella di controllo **Esegui processo**, selezionare il processo da eseguire quando viene generato l'avviso. È possibile creare un nuovo processo facendo clic su **Nuovo processo**. Per visualizzare ulteriori informazioni sul processo, fare clic su **Visualizza processo**. Per altre informazioni sulle opzioni disponibili nelle finestre di dialogo **Nuovo processo** e **Proprietà processo***nome_processo*, vedere [Creare un processo](../../ssms/agent/create-a-job.md) e [Visualizzare un processo](../../ssms/agent/view-a-job.md).  
  
7.  Selezionare la casella di controllo **Invia notifica a operatori** se si desidera notificare agli operatori quando viene attivato l'avviso. In **Elenco operatori**selezionare uno o più dei metodi seguenti per inviare la notifica all'operatore o agli operatori: **Posta elettronica**, **Cercapersone**o **Net Send**. È possibile creare un nuovo operatore facendo clic su **Nuovo operatore**. Per visualizzare ulteriori informazioni su un operatore, fare clic su **Visualizza operatore**. Per ulteriori informazioni sulle opzioni disponibili nelle finestre di dialogo delle proprietà **Nuovo operatore** e **Visualizza operatore** , vedere [Create an Operator](../../ssms/agent/create-an-operator.md) e [View Information About an Operator](../../ssms/agent/view-information-about-an-operator.md).  
  
8.  Al termine, fare clic su **OK**.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-define-the-response-to-an-alert"></a>Per definire la risposta a un avviso  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- adds an e-mail notification for Test Alert.  
    -- assumes that Test Alert already exists and that
    -- François Ajenstat is a valid operator name   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_notification  
     @alert_name = N'Test Alert',  
     @operator_name = N'François Ajenstat',  
     @notification_method = 1 ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_notification (Transact-SQL)](http://msdn.microsoft.com/en-us/0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd).  
  
