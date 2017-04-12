---
title: "Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione snapshot) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1"
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Informazioni sulla pubblicazione, Tutte le sottoscrizioni (Pubblicazione snapshot)
  Il **tutte le sottoscrizioni** scheda vengono visualizzate informazioni su tutte le sottoscrizioni della pubblicazione snapshot selezionata.  
  
## Opzioni  
 Per ulteriori informazioni su una sottoscrizione e sulle attività correlate, fare clic con il pulsante destro del mouse sulla riga della sottoscrizione e quindi scegliere un'opzione dal menu di scelta rapida. Per modificare la modalità di visualizzazione dei dati nella griglia, fare clic con il pulsante destro del mouse sulla griglia, quindi scegliere una delle opzioni seguenti:  
  
-   **Ordinamento**: consente di ordinare una o più colonne nella finestra di dialogo **Ordina colonne** .  
  
-   **Seleziona colonne da visualizzare**: consente di selezionare le colonne da visualizzare e l'ordine di visualizzazione nella finestra di dialogo **Seleziona colonne** .  
  
-   **Filtro**: consente di filtrare le righe nella griglia in base a valori di colonna nella finestra di dialogo **Impostazioni filtro** .  
  
-   **Cancella filtro**: consente di cancellare qualsiasi impostazione di filtro per la griglia.  
  
 Le impostazioni di filtro sono specifiche di ogni griglia. La selezione e l'ordinamento delle colonne vengono applicati a tutte le griglie dello stesso tipo, ad esempio la griglia delle pubblicazioni per ogni server di pubblicazione.  
  
 **Mostra**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive. Consente di selezionare gli stati della sottoscrizione da visualizzare per il tipo di sottoscrizione selezionato. Ad esempio, è possibile scegliere di visualizzare solo le sottoscrizioni con errori.  
  
 **Stato**  
 Stato di ogni sottoscrizione determinato dallo stato dell'agente snapshot o dell'agente di distribuzione. Viene visualizzato lo stato con priorità più alta.  
  
 Per impostazione predefinita, la griglia contenente le informazioni di sottoscrizione verrà ordinata i **stato** colonna. Nell'elenco seguente vengono indicati i valori di stato possibili e l'ordinamento di tali valori, ad esempio gli errori vengono sempre visualizzati nella parte superiore della griglia.  
  
-   Errore  
  
-   Scadenza imminente/Scaduta (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Sottoscrizione non inizializzata (solo [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive)  
  
-   Ripetizione comando non riuscito  
  
-   Sincronizzazione in corso  
  
-   Non in sincronizzazione  
  
 L'ordinamento determina inoltre il valore da visualizzare quando per una particolare sottoscrizione sono disponibili più stati. Ad esempio, se per una sottoscrizione sono presenti errori e la scadenza della sottoscrizione è imminente, nella colonna **Stato** viene visualizzato il valore **Errore**.  
  
 I valori di stato **scadenza imminente/scaduta** e **sottoscrizione non inizializzata** sono avvisi. Quando viene visualizzato un avviso, nella colonna **Stato** viene inoltre visualizzato se è in esecuzione un agente. Ad esempio, lo stato potrebbe essere **in esecuzione, scadenza imminente/scaduta**.  
  
 Il valore di stato **scadenza imminente/scaduta** viene visualizzata solo se è impostata una soglia. Per informazioni sull'impostazione delle soglie, vedere [impostare soglie e avvisi in Monitoraggio replica](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Sottoscrizione**  
 Il nome di ogni sottoscrizione, nel formato: *SubscriberName: SubscriptionDatabaseName*.  
  
 **Ultima sincronizzazione**  
 Data e ora dell'ultima esecuzione dell'agente di distribuzione. Se il processo di sincronizzazione è in corso, viene visualizzato **In corso** .  
  
## Vedere anche  
 [Avvio di Monitoraggio replica](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Consente di visualizzare informazioni ed eseguire attività relative agli agenti associati a una sottoscrizione & #40; Monitoraggio replica & #41;](../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md)   
 [Monitoraggio della replica](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  