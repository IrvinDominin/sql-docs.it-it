---
title: Account dei servizi Client e modificare il Controller | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a73ddb-18ad-415c-bfbe-126ab2e3290b
caps.latest.revision: "29"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b43b611e45de9da98954417d5e7a1bfad009eac
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="modify-the-controller-and-client-services-accounts"></a>Modificare gli account dei servizi controller e client
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In questo argomento, si imparerà a modificare gli account del servizio client e il controller di riesecuzione distribuita e quindi riapplicare gli elenchi di controllo di accesso (ACL).  
  
### <a name="to-start-or-stop-the-distributed-replay-services-using-computer-management"></a>Per avviare o arrestare i servizi client Riesecuzione distribuita tramite Gestione computer  
  
1.  Nel computer in cui sono installati i servizi di ridistribuzione distribuita digitare **dcomcnfg**al prompt dei comandi.  
  
2.  Fare doppio clic su **servizi**, scorrere verso il basso e fare doppio clic su  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] riesecuzione distribuita \<nome servizio >**, quindi fare clic su **avviare** o **arrestare**.  
  
### <a name="to-modify-the-distributed-replay-controller-service"></a>Per modificare il servizio controller di Riesecuzione distribuita  
  
1.  Nel computer controller arrestare il servizio controller di Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  In **Servizi** fare clic con il pulsante destro del mouse su **Controller di Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**, quindi scegliere **Proprietà**.  
  
3.  Nella scheda **Accesso** della finestra **Proprietà di Controller di Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** selezionare **Account seguente**, digitare il nuovo account di accesso o fare clic su **Sfoglia** per selezionarlo, quindi fare clic su **OK**.  
  
     **Importante**: quando si configura il Controller di Riesecuzione distribuita, è possibile specificare uno o più account utente da usare per eseguire i servizi client Riesecuzione distribuita. Di seguito viene fornito l'elenco degli account supportati:  
  
    -   Account utente di dominio  
  
    -   Account utente locale creato dall'utente  
  
    -   Amministratore  
  
    -   Account virtuale e account del servizio gestito  
  
    -   Servizi di rete, Servizi locali e Sistema  
  
     Gli account di gruppo (locale o dominio) e gli altri account predefiniti (come Everyone) non sono accettati.  
  
4.  Avviare il servizio controller di Riesecuzione distribuita.  
  
### <a name="to-modify-the-distributed-replay-client-service"></a>Per modificare il servizio client Riesecuzione distribuita  
  
1.  Prima di modificare il servizio client Riesecuzione distribuita, verificare che l'account del servizio client da modificare sia stato specificato durante l'installazione, nel parametro CTLRUSERS del computer controller. Se l'account del servizio client da modificare non è stato specificato durante l'installazione, è necessario effettuare innanzitutto i passaggi seguenti:  
  
    1.  Arrestare il servizio controller di Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    2.  Nel computer controller in cui è installato il servizio controller, digitare **dcomcnfg** al prompt dei comandi.  
  
    3.  Nella finestra **Servizi componenti** passare a **Radice console -> Servizi componenti -> Computer -> Risorse del computer -> Config DCOM ->DReplayController**.  
  
    4.  Fare clic con il pulsante destro del mouse su **DReplayController**, quindi scegliere **Proprietà**.  
  
    5.  Nella scheda **Sicurezza** nella finestra **Proprietà di DReplayController** fare clic su **Modifica** nella sezione **Autorizzazioni di esecuzione e attivazione** .  
  
    6.  Concedere al nuovo account di accesso del servizio client le autorizzazioni **Attivazione locale e Attivazione remota** , quindi fare clic su **OK**.  
  
    7.  Fare clic su **Modifica** nella sezione **Autorizzazioni di accesso** e concedere al nuovo account di accesso del servizio client le autorizzazioni **Accesso locale e Accesso remoto** , quindi fare clic su **OK**.  
  
    8.  Fare clic su **OK** per chiudere la finestra **Proprietà di DReplayController** .  
  
    9. Nel computer controller aggiungere l'account di accesso del servizio client modificato al gruppo **Distributed COM Users** .  
  
    10. Avviare il servizio SQL Server Distributed Replay Controller.  
  
2.  Arrestare il servizio client Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3.  Nella scheda **Accesso** della finestra **Proprietà di Client Riesecuzione distribuita di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** scegliere **Account seguente**, digitare il nuovo account di accesso o fare clic su **Sfoglia** per selezionarlo e quindi fare clic su **OK**.  
  
4.  Avviare il servizio client Riesecuzione distribuita.  
  
  
