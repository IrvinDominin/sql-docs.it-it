---
title: "Monitoraggio delle prestazioni con Monitoraggio replica | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "monitoraggio delle prestazioni [replica di SQL Server], Monitoraggio replica"
  - "agente di lettura log, monitoraggio"
  - "Monitoraggio replica, prestazioni"
  - "agente di merge, monitoraggio"
  - "agente di lettura coda, monitoraggio"
  - "agente snapshot, monitoraggio"
  - "agente di distribuzione, monitoraggio"
  - "monitoraggio delle prestazioni [replica di SQL Server]"
ms.assetid: f212397d-1bfd-496b-a246-668952891d09
caps.latest.revision: 36
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 36
---
# Monitoraggio delle prestazioni con Monitoraggio replica
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Monitoraggio replica consente di monitorare le prestazioni della replica transazionale e della replica di tipo merge come indicato di seguito:  
  
-   Impostazione di avvisi e soglie  
  
-   Visualizzazione delle misurazioni delle prestazioni  
  
-   Determinazione della latenza con token di traccia (replica transazionale)  
  
-   Visualizzazione di statistiche dettagliate sulla sincronizzazione (replica di tipo merge)  
  
-   Visualizzazione di transazioni e tempi di recapito (replica transazionale)  
  
## Impostazione di avvisi e soglie  
 Monitoraggio replica consente di abilitare avvisi in relazione a varie condizioni delle prestazioni. Quando si attiva un avviso, si specifica una soglia. Quando tale soglia viene raggiunta o superata, viene visualizzato un avviso nel **stato** colonna per la sottoscrizione e la pubblicazione con cui Sincronizza (a meno che non debba essere visualizzato un problema con una priorità più alta). Oltre a visualizzare un avviso in Monitoraggio replica, il raggiungimento di un valore soglia può inoltre attivare un messaggio di avviso. È possibile attivare avvisi per le condizioni delle prestazioni seguenti:  
  
-   Superamento della latenza specificata (quantità di tempo trascorso tra l'esecuzione del commit di una transazione nel server di pubblicazione e l'esecuzione del commit della transazione corrispondente nel Sottoscrittore).  
  
     Si applica alla replica transazionale. Se la soglia specificata viene raggiunta o superata, viene visualizzato lo stato **Prestazioni critiche**.  
  
-   Superamento del tempo di sincronizzazione specificato.  
  
     Si applica alla replica di tipo merge. Se la soglia specificata viene raggiunta o superata, lo stato viene visualizzato come **merge con esecuzione prolungata**. È possibile specificare soglie diverse per connessioni remote e LAN.  
  
-   Impossibilità di elaborare il numero di righe specificato in un determinato intervallo di tempo.  
  
     Si applica alla replica di tipo merge. Se la soglia specificata viene raggiunta o superata, viene visualizzato lo stato **Prestazioni critiche**. È possibile specificare soglie diverse per connessioni remote e LAN.  
  
 Per ulteriori informazioni, vedere [impostare soglie e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
## Visualizzazione delle misurazioni delle prestazioni  
 Monitoraggio replica consente di visualizzare i valori di qualità delle prestazioni per la replica transazionale di replica e di tipo merge nel **prestazioni medie correnti** e **prestazioni peggiori correnti** colonne per le pubblicazioni e **prestazioni** colonna per le sottoscrizioni. Le prestazioni possono risultare:  
  
-   Eccellenti  
  
-   Buone  
  
-   Discrete  
  
-   Scarse  
  
-   Critiche (solo per la replica transazionale)  
  
 I valori vengono determinati nei modo seguenti:  
  
-   Per la replica transazionale la qualità delle prestazioni viene determinata dalla soglia di latenza. Se la soglia non viene impostata, non verrà visualizzato alcun valore. Nella tabella seguente viene illustrata la correlazione tra la soglia e il valore della qualità delle prestazioni. Ad esempio, se la soglia è impostata su 60 secondi e la latenza attuale è di 30 secondi, la latenza rappresenta il 50% della soglia, producendo quindi il valore Buone.  
  
    |Eccellenti|Buone|Discrete|Scarse|Critico|  
    |---------------|----------|----------|----------|--------------|  
    |0 – 34%|35 – 59%|60 – 84%|85 – 99%|100% +|  
  
-   Replica di tipo merge è indipendente dalla soglia qualità delle prestazioni (la soglia di elaborazione delle righe è determinare se un valore di **prestazioni critiche** viene visualizzato nel **stato** colonna). La qualità delle prestazioni è determinata dal confronto tra le prestazioni delle singole sottoscrizioni e le prestazioni medie cronologiche delle sottoscrizioni, che utilizzano lo stesso tipo di connessione (remota o LAN), rispetto alla pubblicazione. In Monitoraggio replica viene visualizzato un valore dopo cinque sincronizzazioni con 50 o più modifiche eseguite con lo stesso tipo di connessione. Se sono state eseguite meno di cinque sincronizzazioni con 50 o più modifiche oppure la sincronizzazione più recente include meno di 50 modifiche, in Monitoraggio replica non viene visualizzato alcun valore.  
  
     Nella tabella seguente viene illustrata la correlazione tra le prestazioni medie e il valore della qualità delle prestazioni. Ad esempio, se dieci Sottoscrittori hanno eseguito la sincronizzazione tramite una connessione LAN con una velocità media di elaborazione di 100 righe al secondo e successivamente una delle sottoscrizioni esegue la sincronizzazione con una velocità di 125 righe al secondo, le prestazioni di sincronizzazione di quel Sottoscrittore saranno del 125% rispetto alla media, producendo quindi il valore Buone.  
  
    |Eccellenti|Buone|Discrete|Scarse|  
    |---------------|----------|----------|----------|  
    |151+%|76 – 150%|26 – 75%|0 – 25%|  
  
 Per ulteriori informazioni sulla visualizzazione delle informazioni di sottoscrizione, vedere [visualizzare le informazioni ed esecuzione delle attività per una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
## Determinazione della latenza con token di traccia  
 La replica transazionale consente di misurare la latenza di un sistema inserendo un token (una piccola quantità di dati) nel log delle transazioni del database di pubblicazione e misurando il tempo impiegato dal token per arrivare al database di distribuzione e ai Sottoscrittori. Il token consente inoltre di rilevare se i dati non raggiungono il database di distribuzione o il Sottoscrittore. Per ulteriori informazioni, vedere [misurazione latenza e convalidare le connessioni per la replica transazionale](../../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
## Visualizzazione di statistiche dettagliate sulle prestazioni di sincronizzazione per la replica di tipo merge  
 Per la replica di tipo merge in Monitoraggio replica vengono visualizzate statistiche dettagliate di ogni articolo elaborato durante la sincronizzazione, inclusa la quantità di tempo impiegato in ogni fase di elaborazione (caricamento delle modifiche, download delle modifiche e così via). Ciò può essere utile per individuare tabelle specifiche che determinano rallentamenti ed è l'opzione migliore per risolvere problemi relativi alle prestazioni delle sottoscrizioni di tipo merge. Per ulteriori informazioni sulla visualizzazione di statistiche dettagliate, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Visualizzazione delle transazioni e dei tempi di recapito della replica transazionale  
 Per la replica transazionale in Monitoraggio replica vengono visualizzate informazioni sul numero di transazioni nel database di distribuzione non ancora distribuite a un Sottoscrittore e il tempo stimato per la relativa distribuzione. Per ulteriori informazioni, vedere [visualizzare le informazioni ed esecuzione delle attività degli agenti associati con una sottoscrizione & #40; Monitoraggio replica & #41;](../../../relational-databases/replication/monitor/view information and perform tasks for subscription agents.md).  
  
## Vedere anche  
 [Monitoraggio della replica](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)   
 [Impostazione di valore soglia e avvisi in Monitoraggio replica](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md)  
  
  