---
title: Eliminare una categoria di processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- deleting job category
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- removing job category
ms.assetid: 47a7640b-20b3-4639-ab37-b6fc73575e6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1e98d9f168e0256b96fefdd1d1c1bf65b5b54155
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078391"
---
# <a name="delete-a-job-category"></a>Eliminare una categoria di processi
  In questo argomento viene descritto come eliminare una categoria di processi di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o SQL Server Management Objects.  
  
 Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È ad esempio possibile organizzare tutti i processi di backup dei database raggruppandoli nella categoria Manutenzione database.  
  

  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Quando si elimina una categoria di processi definita dall'utente, tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent viene richiesto di riassegnare i processi appartenenti alla categoria a un'altra categoria. È possibile eliminare solo categorie di processi definite dall'utente.  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  

  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-delete-a-job-category"></a>Per eliminare una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera eliminare una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Processi** e selezionare **Gestione categorie processi**.  
  
4.  Nella finestra di dialogo **Gestione categorie di processi***nome_server* selezionare la categoria di processi da eliminare.  
  
5.  Fare clic su **Elimina**.  
  
6.  Nella finestra di dialogo **Categorie di processi** fare clic su **Sì**.  
  
7.  Chiudere la finestra di dialogo **Gestione categorie di processi***nome_server*.  
  

  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-delete-a-job-category"></a>Per eliminare una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- deletes the job category named AdminJobs.  
    USE msdb ;  
    GO   
    EXEC dbo.sp_delete_category  
        @name = N'AdminJobs',  
        @class = N'JOB' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_delete_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-category-transact-sql).  
  

  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per eliminare una categoria di processi**  
  
 Chiamare il `JobCategory` classe utilizzando un linguaggio di programmazione desiderato, ad esempio Visual Basic, Visual c# o PowerShell.  
  

  
  
