---
title: 'Lezione 3: Configurazione della distribuzione | Microsoft Docs'
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f248984a-0b59-4c2f-a56d-31f8dafe72b5
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 2888c3f576159def2fb141802aafc1853ce9b50f
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-3-configuring-distribution"></a>Lezione 3: Configurazione della distribuzione
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa lezione verrà configurata la distribuzione nel server di pubblicazione e verranno impostate le autorizzazioni necessarie per i database di pubblicazione e di distribuzione. Se il server di distribuzione è già stato configurato, è necessario disabilitare la pubblicazione e la distribuzione prima di iniziare questa lezione. Non eseguire questa operazione se è necessario mantenere la topologia di replica esistente.  
  
In questa esercitazione non è prevista la configurazione del server di pubblicazione con un server di distribuzione remoto.  
  
### <a name="configuring-distribution-at-the-publisher"></a>Configurazione della distribuzione nel server di pubblicazione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi espandere il nodo del server.  
  
2.  Fare clic con il pulsante destro del mouse sulla cartella **Replica** e scegliere **Configura distribuzione**.  
  
    > [!NOTE]  
    > Se è stata effettuata la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando **localhost** anziché il nome effettivo del server, verrà visualizzato un avviso in cui viene indicata l'impossibilità di stabilire una connessione tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il server **'localhost'**. Fare clic su **OK** nella finestra di dialogo di avviso. Nella finestra di dialogo **Connetti al server** modificare **Nome server** sostituendo **localhost** con il nome del server. Fare clic su **Connetti**.  
  
    Verrà avviata la Configurazione guidata distribuzione.  
  
3.  Nella pagina **Server di distribuzione** selezionare 'NomeServer>' fungerà da database distribuzione per se stesso. Verranno creati un database di distribuzione e un log** e quindi fare clic su **Avanti**.  
  
4.  Se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in esecuzione, nella pagina [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**Agent** selezionare **Sì**e configurare l'avvio automatico del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Scegliere **Avanti**.  
  
5.  Nella casella di testo **Cartella snapshot** immettere **\\\\**\<*Nome_computer>***\repldata**, dove \<*Nome_computer>* è il nome del server di pubblicazione e quindi fare clic su **Avanti**.  
  
6.  Accettare i valori predefiniti nella pagine seguenti della procedura guidata.  
  
7.  Fare clic su **Fine** per abilitare la distribuzione.  
  
### <a name="setting-database-permissions-at-the-publisher"></a>Impostazione delle autorizzazioni per il database nel server di pubblicazione  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]espandere la cartella **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso**e quindi scegliere **Nuovo account di accesso**.  
  
2.  Nella pagina **Generale** fare clic su **Cerca**, immettere \<*Nome_computer>***\repl_snapshot** nella casella **Immettere il nome dell'oggetto da selezionare**, dove \<*Nome_computer>* è il nome del server di pubblicazione locale, fare clic su **Controlla nomi** e quindi su **OK**.  
  
3.  Nell'elenco **Utenti con mapping all'account di accesso seguente** nella pagina **Mapping utenti** selezionare il database **e il database di** distribuzione [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
    Nell'elenco **Appartenenza a ruoli del database** selezionare il ruolo **db_owner** per l'account di accesso per entrambi i database.  
  
4.  Fare clic su **OK** per creare l'account di accesso.  
  
5.  Ripetere i passaggi da 1 a 4 per creare un account di accesso per l'account locale repl_logreader. È necessario eseguire il mapping di questo account anche agli utenti membri del ruolo predefinito del database **db_owner** nel database di **distribuzione** e nel database **AdventureWorks** .  
  
6.  Ripetere i passaggi da 1 a 4 per creare un account di accesso per l'account locale repl_distribution. È necessario eseguire il mapping di questo account a un utente membro del ruolo predefinito del database **db_owner** nel database di **distribuzione** .  
  
7.  Ripetere i passaggi da 1 a 4 per creare un account di accesso per l'account locale repl_merge. Questo account deve avere mapping di utenti nel database di **distribuzione** e nel database **AdventureWorks** .  
  
## <a name="see-also"></a>Vedere anche  
[Configura distribuzione](../../relational-databases/replication/configure-distribution.md)  
[Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)  
  
  
  
