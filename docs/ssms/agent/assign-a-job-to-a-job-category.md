---
title: Assegnare un processo a una categoria di processi | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 39a00b53ae37f52c0ade4c123f52fb7b72aa4a5b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "42775492"
---
# <a name="assign-a-job-to-a-job-category"></a>Assegnare un processo a una categoria di processi
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene descritto come assegnare i processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent a categorie di processi in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o SQL Server Management Objects.  
  
Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È ad esempio possibile organizzare tutti i processi di backup dei database raggruppandoli nella categoria Manutenzione database. È possibile assegnare processi a categorie predefinite, oppure creare una categoria definita dall'utente e usarla per l'assegnazione dei processi.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per assegnare un processo a una categoria di processi usando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Per assegnare un processo a una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera assegnare un processo a una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic sul segno più per espandere la cartella **Processi** .  
  
4.  Fare clic con il pulsante destro del mouse sul processo da modificare e selezionare **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà processo -***nome_processo* selezionare nell'elenco **Categoria** la categoria di processi alla quale assegnare il processo.  
  
6.  Fare clic su **OK**.  
  
## <a name="TSQL"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Per assegnare un processo a una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Per altre informazioni, vedere [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
**Per assegnare un processo a una categoria di processi**  
  
Usare la classe **JobCategory** con un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell.  
  
