---
title: Avviare un processo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d255a32058588d943ea88d596a4c0bfdb1badfed
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325491"
---
# <a name="start-a-job"></a>Start a Job
  In questo argomento viene descritto come avviare l'esecuzione di un processo di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] o SQL Server Management Objects.  
  
 Un processo è una serie specificata di azioni eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent possono essere eseguiti in un server locale o in più server remoti.  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Per avviare un processo utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-start-a-job"></a>Per avviare un processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]ed espandere tale istanza.  
  
2.  Espandere **SQL Server Agent** e quindi **Processi**. In base alla modalità di avvio del processo desiderata, eseguire una delle seguenti operazioni:  
  
    -   Se si usa un unico server oppure un server di destinazione, oppure se si esegue un processo del server locale in un server master, fare clic con il pulsante destro del mouse sul processo da avviare e scegliere **Avvia processo**.  
  
    -   Se si vuole avviare più processi, fare clic con il pulsante destro del mouse su **Monitoraggio attività processi**e scegliere **Visualizza attività processi**. In Monitoraggio attività processi è possibile selezionare più processi; fare clic con il pulsante destro del mouse sui processi selezionati e scegliere **Avvia processi**.  
  
    -   Se si usa un server master e si vuole eseguire il processo contemporaneamente in tutti i server di destinazione, fare clic con il pulsante destro del mouse sul processo da avviare, scegliere **Avvia processo**e fare clic su **Avvia su tutti i server di destinazione**.  
  
    -   Se si usa un server master e si vogliono specificare i server di destinazione in cui eseguire il processo, fare clic con il pulsante destro del mouse sul processo da avviare, scegliere **Avvia processo**e fare clic su **Avvia sui server di destinazione specificati**. Nella finestra di dialogo **Invia istruzioni di download** selezionare la casella di controllo **Solo i server di destinazione seguenti** e quindi selezionare i server di destinazione in cui si desidera eseguire il processo.  
  
##  <a name="TSQL"></a> Uso di Transact-SQL  
  
#### <a name="to-start-a-job"></a>Per avviare un processo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
 Per altre informazioni, vedere [sp_start_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-start-job-transact-sql).  
  
##  <a name="SMO"></a> Utilizzo di SQL Server Management Objects  
 **Per avviare un processo**  
  
 Chiamare il metodo `Start` della classe `Job` usando un linguaggio di programmazione come Visual Basic, Visual C# o PowerShell. Per altre informazioni, vedere [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  
  
