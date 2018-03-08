---
title: Visualizzare informazioni sui passaggi di processo | Microsoft Docs
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
- displaying job step information
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- viewing job step information
ms.assetid: e3f06492-dc86-4e06-b186-ea58aff6d591
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 050180ff07ab89c24811d9adca754e67a6e2cf8e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="view-job-step-information"></a>Visualizzare informazioni sui passaggi di processo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come visualizzare informazioni dettagliate sui passaggi di processo nella finestra di dialogo Proprietà passaggio processo. Sono inoltre incluse informazioni sulla visualizzazione dell'output dei passaggi di processo.  
  
-   **Prima di iniziare:**  
  
    [Limitazioni e restrizioni](#Restrictions)  
  
    [Security](#Security)  
  
-   **Per visualizzare informazioni sui passaggi di processo mediante:**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Restrictions"></a>Limitazioni e restrizioni  
Se un passaggio di processo è stato configurato per la scrittura dell'output in una tabella o file e il processo è stato eseguito almeno una volta, è possibile esaminare l'output nella scheda **Avanzate** della finestra di dialogo **Proprietà passaggio processo** . Quando un processo o un passaggio di processo viene eliminato, viene eliminato automaticamente anche il log di output.  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
È possibile visualizzare solo i processi di cui si è proprietari, a meno che non si appartenga al ruolo predefinito del server **sysadmin** . I membri di questo ruolo infatti possono visualizzare tutti i processi e tutte le informazioni sui passaggi di processo.  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-view-job-step-information"></a>Per visualizzare informazioni sui passaggi di processo  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], quindi espanderla.  
  
2.  Espandere il nodo **SQL Server Agent**e il nodo **Processi**, fare clic con il pulsante destro del mouse sul processo che include il passaggio da visualizzare e scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà processo** fare clic sulla scheda **Passaggi** .  
  
4.  Fare clic sul passaggio di processo da visualizzare e quindi dare clic su **Modifica**.  
  
5.  Nella scheda **Generale** della finestra di dialogo **Proprietà passaggio processo** è indicato il tipo di passaggio e la funzione corrispondente.  
  
6.  Nella scheda **Avanzate** sono indicate le operazioni eseguite da [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se il passaggio di processo ha esito positivo o negativo, il numero di tentativi da eseguire, la posizione in cui viene scritto l'output del passaggio e l'utente in base al quale viene eseguito il passaggio.  
  
#### <a name="to-view-job-step-output"></a>Per visualizzare l'output dei passaggi di processo  
  
1.  Nella finestra di dialogo **Proprietà passaggio processo** fare clic sulla scheda **Avanzate** .  
  
2.  A seconda della versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] a cui si è connessi, è possibile visualizzare il file o la tabella di output dei passaggi di processo nel modo seguente:  
  
    -   Se si è connessi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] o versioni successive, è possibile fare clic su **Visualizza** solo quando è selezionata l'opzione **Registra nella tabella** . In questo caso l'output dei passaggi di processo viene scritto nella tabella **sysjobstepslogs** del database **msdb** .  
  
    -   Il pulsante **Visualizza** è disabilitato quando l'output dei passaggi di processo viene scritto in un file. Per visualizzare un file di output dei passaggi di processo, utilizzare il Blocco note.  
  
