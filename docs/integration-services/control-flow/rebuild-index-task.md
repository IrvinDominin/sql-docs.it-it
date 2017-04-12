---
title: "Attivit&#224; Ricompila indice | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.rebuildindextask.f1"
helpviewer_keywords: 
  - "ricompilazione di indici"
  - "indici [Integration Services]"
  - "Ricompila indice - attività"
ms.assetid: 021884dd-e72d-47b2-99e8-b741410509c3
caps.latest.revision: 50
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 50
---
# Attivit&#224; Ricompila indice
  L'attività Ricompila indice consente di ricompilare indici nelle tabelle e nelle viste dei database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per altre informazioni sulla frammentazione degli indici, vedere [Riorganizzare e ricompilare gli indici](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md).  
  
 Tramite l'attività Ricompila indice un pacchetto può ricompilare gli indici in uno o più database. Se si utilizza l'attività per ricompilare gli indici di un singolo database, sarà possibile scegliere le viste e le tabelle di cui ricompilare gli indici.  
  
 L'attività incapsula un'istruzione ALTER INDEX REBUILD con le opzioni di ricompilazione degli indici seguenti:  
  
-   Per l'opzione FILLFACTOR è possibile specificare un valore percentuale o utilizzare il valore originale.  
  
-   Impostare SORT_IN_TEMPDB = ON per archiviare in tempdb i risultati intermedi dell'ordinamento utilizzati per la ricompilazione dell'indice. Quando l'opzione relativa al risultato intermedio dell'ordinamento è impostata su OFF, il risultato viene archiviato nello stesso database dell'indice.  
  
-   Impostare PAD_INDEX = ON per allocare alle pagine di livello intermedio dell'indice lo spazio disponibile specificato dall'opzione FILLFACTOR.  
  
-   Impostare IGNORE_DUP_KEY = ON per consentire alle operazioni di inserimento di più righe che includono record che violano i vincoli UNIQUE di inserire i record che non violano tali vincoli.  
  
-   Impostare ONLINE = ON per non mantenere i blocchi di tabella in modo da consentire l'esecuzione di aggiornamenti o query sulla tabella sottostante durante la ricostruzione dell'indice.  
  
    > [!NOTE]  
    >  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
-   Specificare un valore per MAXDOP per limitare il numero di processori usati durante l'esecuzione di piani paralleli.  
  
-   Specificare WAIT_AT_LOW_PRIORITY, MAX_DURATION e ABORT_AFTER_WAIT per controllare il tempo di attesa dell'operazione sull'indice per i blocchi a bassa priorità.  
  
 Per altre informazioni sull'istruzione ALTER INDEX e sulle opzioni di ricompilazione dell'indice, vedere [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
> [!IMPORTANT]  
>  Il tempo richiesto dall'attività per creare l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] da eseguire è proporzionale al numero degli indici da ricompilare. Se l'attività è configurata per la ricompilazione degli indici in tutte le tabelle e le viste di un database con un numero elevato di indici oppure per la ricompilazione degli indici in più database, la generazione dell'istruzione Transact-SQL potrebbe richiedere una quantità di tempo considerevole.  
  
## Configurazione dell'attività Ricompila indice  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Questa attività è disponibile nella sezione **Attività di manutenzione** della casella degli strumenti **** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Per ulteriori informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , fare clic sull'argomento seguente:  
  
 [Attività Ricompila indice &#40;Piano di manutenzione&#41;](../../relational-databases/maintenance-plans/rebuild-index-task-maintenance-plan.md)  
  
## Attività correlate  
 Per altre informazioni su come impostare queste proprietà nella finestra di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md).  
  
## Vedere anche  
 [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md)   
 [Flusso di controllo](../../integration-services/control-flow/control-flow.md)  
  
  