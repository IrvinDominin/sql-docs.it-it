---
title: Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools [SQL Server], monitoring performance
- monitoring server performance [SQL Server], tools
- monitoring performance [SQL Server], tools
- database performance [SQL Server], tools
- tuning databases [SQL Server], tools
- database monitoring [SQL Server], tools
- performance [SQL Server], monitoring tools
- server performance [SQL Server], tools
ms.assetid: 31529dfe-68e7-49f7-b3c2-39fcecf33a95
caps.latest.revision: "37"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5121d6d12b0c009a6463f461204da027f67f16ef
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="performance-monitoring-and-tuning-tools"></a>Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] include un set completo di strumenti per il monitoraggio di eventi in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e per l'ottimizzazione della progettazione fisica del database. La scelta dello strumento dipende dal tipo di monitoraggio o di ottimizzazione da eseguire e dagli eventi specifici da monitorare.  
  
 Di seguito sono elencati gli strumenti di monitoraggio e ottimizzazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
|Strumento|Description|  
|----------|-----------------|  
|[sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] tiene traccia degli eventi di elaborazione del motore, ad esempio l'avvio di un batch o di una transazione, consentendo di monitorare l'attività del server e del database, ad esempio deadlock, errori irreversibili o attività di accesso. È possibile acquisire dati di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] in un file o una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per poterli analizzare in seguito, nonché riprodurre gli eventi acquisiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passaggio per passaggio e determinare con esattezza quali eventi hanno avuto luogo.|  
|[SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] In Distributed Replay è possibile usare più computer per riprodurre dati di traccia e simulare un carico di lavoro di importanza critica.|  
|[Monitoraggio dell'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)|Monitor di sistema tiene traccia principalmente dell'utilizzo delle risorse, ad esempio il numero corrente di richieste di pagine a Gestione buffer, consentendo di monitorare le prestazioni e l'attività del server tramite oggetti e contatori predefiniti o contatori definiti dall'utente per il monitoraggio degli eventi. Monitoraggio di sistema, Performance Monitor in Microsoft Windows NT 4.0, raccoglie misurazioni e valori piuttosto che dati sugli eventi, ad esempio l'utilizzo della memoria, il numero di transazioni attive, il numero di blocchi bloccati o l'attività della CPU. È possibile impostare le soglie per contatori specifici allo scopo di generare avvisi per la notifica agli operatori.<br /><br /> Monitoraggio di sistema funziona con Microsoft Windows Server e i sistemi operativi Windows. Questo strumento consente di monitorare, in remoto o in locale, un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Windows NT 4.0 o versioni successive.<br /><br /> La principale differenza tra [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] e Monitoraggio di sistema consiste nel fatto che [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] esegue il monitoraggio degli eventi del Motore di database, mentre Monitoraggio di sistema esegue il monitoraggio dell'utilizzo delle risorse associate ai processi del server.|  
|[Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)|Monitoraggio attività di [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è utile per le viste ad hoc dell'attività corrente e consente di visualizzare in formato grafico informazioni relative a:<br /><br /> Processi in esecuzione in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Processi bloccati.<br /><br /> Blocchi.<br /><br /> Attività degli utenti.|  
|[Statistiche sulle query dinamiche](../../relational-databases/performance/live-query-statistics.md)|Visualizza statistiche in tempo reale relative ai passaggi per l'esecuzione di query. Dal momento che i dati sono disponibili durante l'esecuzione della query, queste statistiche di esecuzione sono estremamente utili per il debug di problemi relativi alle prestazioni delle query.|  
|[Traccia SQL](../../relational-databases/sql-trace/sql-trace.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] Stored procedure che consentono di creare, filtrare e definire la creazione della traccia:<br /><br /> [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)<br /><br /> [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)<br /><br /> [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)<br /><br /> [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)<br /><br /> [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)|  
|Log degli errori|Il registro eventi applicazioni di Windows offre una panoramica complessiva degli eventi generati in Windows Server e nei sistemi operativi Windows, nonché degli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e di ricerca full-text. Questo registro contiene informazioni sugli eventi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non disponibili in altro modo. Tali informazioni possono essere utilizzate per risolvere i problemi relativi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)|Le stored procedure di sistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seguenti offrono una potente alternativa per molte attività di monitoraggio:<br /><br /> [sp_who &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md):<br />                    Visualizza informazioni snapshot sugli utenti e i processi correnti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], incluse indicazioni sull'istruzione in esecuzione e sull'eventuale blocco dell'istruzione.<br /><br /> [sp_lock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-lock-transact-sql.md):<br />                    Restituisce informazioni snapshot sui blocchi, inclusi ID oggetto, ID indice, tipo di blocco e tipo di risorsa a cui è applicato il blocco.<br /><br /> [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md): <br />                    Visualizza una stima della quantità corrente di spazio su disco utilizzato da una tabella o da un intero database.<br /><br /> [sp_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md):<br />                    Visualizza statistiche, tra cui utilizzo della CPU, utilizzo delle risorse di I/O e quantità di tempo inattivo dopo l'ultima esecuzione di **sp_monitor** .|  
|[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)|Le istruzioni DBCC (Database Console Command) consentono di controllare le statistiche relative alle prestazioni e la consistenza logica e fisica di un database.|  
|[Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)|Le funzioni predefinite consentono di visualizzare informazioni statistiche snapshot sull'attività di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dall'avvio del server. Questi dati statistici vengono archiviati in contatori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] predefiniti. Ad esempio, **@@CPU_BUSY** indica la quantità di tempo dedicata dalla CPU all'esecuzione di codice [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **@@CONNECTIONS** indica il numero di connessioni o tentativi di connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e **@@PACKET_ERRORS** indica il numero di pacchetti di rete trasferiti nelle connessioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Flag di traccia &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)|I flag di traccia consentono di visualizzare informazioni su un'attività specifica del server e vengono utilizzati per la diagnostica di problemi o inconvenienti relativi alle prestazioni, ad esempio catene di deadlock.|  
|[Ottimizzazione guidata motore di database](../../relational-databases/performance/database-engine-tuning-advisor.md)|Ottimizzazione guidata motore di database analizza gli effetti delle prestazioni delle istruzioni di [!INCLUDE[tsql](../../includes/tsql-md.md)] eseguite sui database che si desidera ottimizzare. Ottimizzazione guidata motore di database offre consigli relativi ad aggiunta, rimozione o modifica di indici, viste indicizzate e partizionamento.|  
  
## <a name="choosing-a-monitoring-tool"></a>Scelta di uno strumento di monitoraggio  
 La scelta dello strumento di monitoraggio dipende dall'evento o dall'attività che si desidera monitorare.  
  
|Evento o attività|SQL Server Profiler|Distributed Replay|Monitor di sistema|Monitoraggio attività|Transact-SQL|Log degli errori|  
|-----------------------|-------------------------|------------------------|--------------------|----------------------|-------------------|----------------|  
|Analisi delle tendenze|Sì||Sì||||  
|Riproduzione di eventi acquisiti|Sì (da un singolo computer)|Sì (da più computer)|||||  
|Monitoraggio ad hoc|Sì|||Sì|Sì|Sì|  
|Generazione di avvisi|||Sì||||  
|Interfaccia grafica|Sì||Sì|Sì||Sì|  
|Utilizzo con applicazioni personalizzate|Sì*||||Sì||  
  
 *Utilizzo di stored procedure di sistema di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] .  
  
## <a name="windows-monitoring-tools"></a>Strumenti di monitoraggio di Windows  
 Nei sistemi operativi Windows e in Windows Server 2003 sono inoltre disponibili gli strumenti di monitoraggio indicati di seguito.  
  
|Strumento|Description|  
|----------|-----------------|  
|Gestione attività|Consente di visualizzare un riepilogo dei processi e delle applicazioni eseguite nel sistema.|  
|Agente Network Monitor|Esegue il monitoraggio del traffico di rete.|  
  
 Per ulteriori informazioni sugli strumenti di Windows Server o dei sistemi operativi Windows, consultare la documentazione di Windows.  
  
  
