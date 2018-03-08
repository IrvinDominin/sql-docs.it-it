---
title: Impostare l'account di avvio del servizio SQL Server Agent | Microsoft Docs
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
- SQL Server Agent, service accounts
- startup accounts [SQL Server]
- service startup accounts [SQL Server Agent]
ms.assetid: 46ffe818-ebb5-43a0-840b-923f219a2472
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bcd26feceb6ecd2fc0b776a5ceec80756cd2e110
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="set-the-service-startup-account-for-sql-server-agent-sql-server-configuration-manager"></a>Impostazione dell'account di avvio del servizio SQL Server Agent (Gestione configurazione SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent definisce l'account di Windows con cui viene eseguito [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e le relative autorizzazioni di rete. In questo argomento viene descritto come impostare l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent con Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   [Per impostare l'account di avvio del servizio per SQL Server Agent tramite SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
  
-   A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)], non è più necessario che l'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent sia un membro del gruppo Administrators di [!INCLUDE[msCoName](../../includes/msconame_md.md)] . L'account di avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent deve tuttavia essere membro del ruolo predefinito del server [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]sysadmin. Per usare l'elaborazione dei processi multiserver, l'account deve essere un membro del ruolo TargetServersRole del database msdb nel server master.  
  
-   In Esplora oggetti viene visualizzato il nodo [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent solo se si dispone dell'autorizzazione per utilizzarlo.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
Per la corretta esecuzione delle funzioni, è necessario che [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent sia configurato per utilizzare le credenziali di un account membro del ruolo predefinito del server **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. L'account deve disporre delle autorizzazioni di Windows seguenti:  
  
-   Accesso come servizio (SeServiceLogonRight)  
  
-   Sostituzione di token a livello di processo (SeAssignPrimaryTokenPrivilege)  
  
-   Ignorare controllo incrociato (SeChangeNotifyPrivilege)  
  
-   Regolazione quote di memoria per un processo (SeIncreaseQuotaPrivilege)  
  
Per altre informazioni sulle autorizzazioni di Windows necessarie per l'account del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent, vedere [Selezionare un account per il servizio SQL Server Agent](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) e [Impostazione di account di servizio Windows](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014).  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-set-the-service-startup-account-for-sql-server-agent"></a>Per impostare l'account di avvio del servizio SQL Server Agent  
  
1.  In **Server registrati**, fare clic sul segno più per espandere **Motore di database**.  
  
2.  Fare clic sul segno più per espandere la cartella **Gruppi di server locali** .  
  
3.  Fare clic con il pulsante destro del mouse sull'istanza del server dove si intende impostare l'account di avvio del servizio e selezionare **Gestione configurazione SQL Server...**.  
  
4.  Nella finestra di dialogo **Controllo account utente** fare clic su **Sì**.  
  
5.  Nel riquadro della console di Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , selezionare **Servizi di SQL Server**.  
  
6.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse su **SQL Server Agent***(nome_server)*, dove *nome_server* è il nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent per cui si vuole modificare l'account di avvio del servizio e selezionare **Proprietà**.  
  
7.  Nella finestra di dialogo *Proprietà*di **Proprietà** , fare clic sulla scheda **Accesso** e selezionare una delle seguenti opzioni in **Accedi come**:  
  
    -   **Account predefinito**: selezionare questa opzione se i processi usano solo risorse del server locale. Per informazioni sulla selezione di un account predefinito di Windows, vedere [Selezionare un account per il servizio SQL Server Agent](http://msdn.microsoft.com/library/ms191543.aspx).  
  
        > [!IMPORTANT]  
        > Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent non supporta l'account **Servizio locale** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
    -   **Account seguente**: selezionare questa opzione se i processi richiedono risorse dalla rete, incluse le risorse dell'applicazione, per inoltrare eventi ad altri registri applicazioni di Windows oppure se per inviare una notifica agli operatori tramite messaggi di posta elettronica o cercapersone.  
  
        Se si seleziona questa opzione:  
  
        1.  Nella casella **Nome account** , immettere l'account che sarà utilizzato per eseguire SQL Server Agent. In alternativa, fare clic su **Sfoglia** per aprire la finestra di dialogo **Seleziona utente o gruppo** e selezionare l'account da utilizzare.  
  
        2.  Immettere nella casella **Password** la password per l'account. Immettere nuovamente la password nella casella **Conferma password** .  
  
8.  Fare clic su **OK**.  
  
9. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Fare clic sul pulsante **Chiudi** in Gestione configurazione.  
  
