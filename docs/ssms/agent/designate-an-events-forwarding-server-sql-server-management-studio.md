---
title: Impostare un server di inoltro eventi | Microsoft Docs
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
- event forwarding servers [SQL Server]
- events [SQL Server], forwarding
- alerts [SQL Server], forwarded events
ms.assetid: 81dfcbe4-3000-4e77-99de-bf85fef63a12
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bde51d61bbe715dd476fe9869471dfa97dc195d
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="designate-an-events-forwarding-server-sql-server-management-studio"></a>Designate an Events Forwarding Server (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questo argomento viene descritto come designare un server al quale verranno inoltrati eventi da [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] eventi in [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] . Si noti che l'inoltro di eventi si applica agli eventi inoltrati tra server, non agli eventi inoltrati tra istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ospitate in un singolo computer. Notare inoltre che per ricevere eventi inoltrati, il server di gestione degli avvisi deve essere un'istanza predefinita di SQL Server.  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per impostare un server di inoltro eventi utilizzando:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-designate-an-events-forwarding-server"></a>Per impostare un server di inoltro eventi  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server da cui si desidera inoltrare gli eventi a un altro server.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent** e scegliere **Proprietà**.  
  
3.  Nella finestra di dialogo **Proprietà SQL Server Agent –***nome_server* fare clic su **Avanzate** in **Selezione pagina**.  
  
4.  In **Inoltro eventi SQL Server**selezionare la casella di controllo **Inoltra eventi a un altro server** .  
  
5.  Nell'elenco **Server** fare clic su un server e quindi in **Eventi**selezionare una delle opzioni seguenti:  
  
    -   Selezionare **Eventi non gestiti** per inoltrare solo gli eventi che non sono stati gestiti da avvisi locali.  
  
    -   Selezionare **Tutti gli eventi** per inoltrare tutti gli eventi, indipendentemente dal fatto che siano stati gestiti o meno da avvisi locali.  
  
6.  Nell'elenco **Eventi con gravità maggiore o uguale a** selezionare il livello di gravità che contraddistingue gli eventi da inoltrare al server selezionato.  
  
7.  Al termine, fare clic su **OK**.  
  
