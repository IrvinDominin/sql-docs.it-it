---
title: Creare una categoria di processi | Microsoft Docs
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
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0d1809cc9170cc0213d52dc4b96b75e44e9e05af
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="create-a-job-category"></a>Creare una categoria di processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento si descrive come creare una categoria di processi in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)] o [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Management Objects.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent offre categorie di processi predefinite a cui possono essere assegnati processi. In alternativa, è possibile creare una nuova categoria e assegnarvi i processi. Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È ad esempio possibile organizzare tutti i processi di backup dei database raggruppandoli nella categoria Manutenzione database. È inoltre possibile creare categorie di processi personalizzate.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per creare una categoria di processi mediante:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
Le categorie multiserver sono disponibili solo in un server master. In un server master è disponibile una sola categoria di processi predefinita: [**Senza categoria (multiserver)**]. Quando viene scaricato un processo multiserver, la categoria viene modificata in **Processi dal server MSX** nel server di destinazione.  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Per creare una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera creare una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Processi** e selezionare **Gestione categorie processi**.  
  
4.  Nella finestra di dialogo **Gestione categorie di processi***nome_server* fare clic su **Aggiungi**.  
  
5.  Nella casella **Nome** della nuova finestra di dialogo immettere un nome per la nuova categoria di processi.  
  
6.  Selezionare la casella di controllo **Mostra tutti i processi** . Selezionare uno o più processi per la nuova categoria selezionando le caselle corrispondenti ai processi.  
  
7.  Fare clic su **OK**.  
  
8.  Nella finestra di dialogo **Gestione categorie di processi***nome_server* fare clic su **Aggiorna** per assicurarsi che la nuova categoria di processi sia attiva. Se l'aspetto è quello previsto, chiudere questa finestra di dialogo.  
  
Per altre informazioni su queste finestre di dialogo, vedere [Categorie processi - Gestione categorie processi](../../ssms/agent/job-categories-manage-job-categories.md) e [Proprietà categorie processi - Nuova categoria di processi](../../ssms/agent/job-categories-properties-new-job-category.md).  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Per creare una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_add_category (Transact-SQL)](http://msdn.microsoft.com/en-us/6cca32cd-d941-4378-aed6-a7c90cb7520a).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per creare una categoria di processi**  
  
Chiamare la classe **JobCategory** con un linguaggio di programmazione a scelta, ad esempio Visual Basic, Visual C# o PowerShell. Per un codice di esempio, vedere [Pianificazione delle attività amministrative automatiche in SQL Server Agent](http://msdn.microsoft.com/en-us/900242ad-d6a2-48e9-8a1b-f0eea4413c16).  
  
