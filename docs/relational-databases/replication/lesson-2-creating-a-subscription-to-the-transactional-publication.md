---
title: 'Lezione 2: Creazione di una sottoscrizione per una pubblicazione transazionale | Microsoft Docs'
ms.custom: 
ms.date: 03/01/2017
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
ms.assetid: 5995b7d2-7c06-46f5-b96c-2bee879bcda2
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bc5e6abed8f9d92532e186377b85396b711f290d
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-2-creating-a-subscription-to-the-transactional-publication"></a>Lezione 2: Creazione di una sottoscrizione per una pubblicazione transazionale
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In questa lezione verranno descritte le procedure per creare una sottoscrizione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Per eseguire questa lezione è necessario aver completato la lezione precedente, [Lezione 1: Pubblicazione dei dati tramite la replica transazionale](../../relational-databases/replication/lesson-1-publishing-data-using-transactional-replication.md).  
  
### <a name="to-create-the-subscription"></a>Per creare la sottoscrizione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** fare clic con il pulsante destro del mouse sulla pubblicazione **AdvWorksProductTrans** e quindi scegliere **Nuove sottoscrizioni**.  
  
    Verrà avviata la Creazione guidata nuova sottoscrizione.  
  
3.  Nella pagina Pubblicazione selezionare **AdvWorksProductTrans**e quindi fare clic su **Avanti**.  
  
4.  Nella pagina Posizione in cui eseguire l'agente di distribuzione selezionare **Esegui tutti gli agenti nel database di distribuzione**e quindi fare clic su **Avanti**.  
  
5.  Nella pagina Sottoscrittori, se il nome dell'istanza del Sottoscrittore non è visualizzato, fare clic su **Aggiungi Sottoscrittore**, quindi su **Aggiungi Sottoscrittore SQL Server**, immettere il nome dell'istanza del Sottoscrittore nella finestra di dialogo **Connetti al server** e quindi fare clic su **Connetti**.  
  
6.  Nella pagina Sottoscrittori selezionare il nome dell'istanza del server Sottoscrittore, quindi scegliere **<New Database>** in **Database di sottoscrizione**.  
  
7.  Nella finestra di dialogo **Nuovo database** digitare **ProductReplica** nella casella **Nome database** , fare clic su **OK**e scegliere **Avanti**.  
  
8.  Nella finestra di dialogo **Sicurezza agente di distribuzione** fare clic sul pulsante con i puntini di sospensione (**…**), immettere \<*Nome_computer>***\repl_distribution** nella casella **Account processo**, specificare la password per l'account, fare clic su **OK** e quindi su **Avanti**.  
  
9. Fare clic su **Fine** per accettare i valori predefiniti nelle pagine seguenti e completare la procedura guidata.  
  
### <a name="setting-database-permissions-at-the-subscriber"></a>Impostazione delle autorizzazioni per il database nel Sottoscrittore  
  
1.  Connettersi al Sottoscrittore in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere **Database**, **ProductReplica**e **Sicurezza**, fare clic con il pulsante destro del mouse su **Utenti**e quindi scegliere **Nuovo utente**.  
  
2.  Nella pagina **Generale**, nell'elenco della pagina **Tipo utente** selezionare **Utente di Windows**.  
  
3.  Selezionare la casella **Nome utente** e fare clic sul pulsante con i puntini di sospensione (…), quindi nella casella **Inserire il nome oggetto da selezionare** digitare <Nome_computer>**\repl_distribution**, fare clic su **Controlla nomi** e fare clic su **OK**.  
  
4.  Nella pagina **Appartenenze**, in **Appartenenza a ruoli del database** selezionare **db_owner**, quindi scegliere **OK** per creare l'utente.  
  
### <a name="to-view-the-synchronization-status-of-the-subscription"></a>Per visualizzare lo stato di sincronizzazione della sottoscrizione  
  
1.  Connettersi al server di pubblicazione in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], espandere il nodo del server e quindi la cartella **Replica** .  
  
2.  Nella cartella **Pubblicazioni locali** espandere la pubblicazione **AdvWorksProductTrans** , fare clic con il pulsante destro del mouse sulla sottoscrizione nel database **ProductReplica** e quindi scegliere **Visualizza stato sincronizzazione**.  
  
    Verrà visualizzato lo stato corrente della sincronizzazione della sottoscrizione.  
  
3.  Se la sottoscrizione non è visualizzata in **AdvWorksProductTrans**, premere F5 per aggiornare l'elenco.  
  
## <a name="next-steps"></a>Next Steps  
In questo modo è stata creata una sottoscrizione per la pubblicazione transazionale. Poiché l'agente di distribuzione per questa sottoscrizione è in esecuzione continua, la sottoscrizione viene inizializzata al momento della creazione. Il passaggio successivo consiste nell'utilizzo di token di traccia per verificare che le modifiche sono state replicate nel Sottoscrittore e per determinare la latenza. Vedere [Lezione 3: Convalida della sottoscrizione e misurazione della latenza](../../relational-databases/replication/lesson-3-validating-the-subscription-and-measuring-latency.md).  
  
## <a name="see-also"></a>Vedere anche  
[Inizializzazione di una sottoscrizione con uno snapshot](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
[Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)  
[Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
