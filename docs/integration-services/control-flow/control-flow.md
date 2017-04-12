---
title: "Flusso di controllo | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "flusso di controllo [Integration Services], elementi"
  - "elementi del flusso di controllo SSIS"
  - "elementi del flusso di controllo di SQL Server Integration Services"
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
caps.latest.revision: 46
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 46
---
# Flusso di controllo
  Un pacchetto è costituito da un flusso di controllo e, facoltativamente, da uno o più flussi di dati. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] offre tre diversi tipi di elementi del flusso di controllo: contenitori, che definiscono le strutture nei pacchetti, attività, che forniscono le funzionalità, e vincoli di precedenza, che connettono eseguibili, contenitori e attività in un flusso di controllo ordinato.  
  
 Per altre informazioni, vedere [Vincoli di precedenza](../../integration-services/control-flow/precedence-constraints.md), [Contenitori in Integration Services](../../integration-services/control-flow/integration-services-containers.md) e [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md).  
  
 Nella figura seguente viene illustrato un flusso di controllo con un contenitore e sei attività, di cui cinque definite a livello di pacchetto e una a livello di contenitore. Tale attività è all'interno di un contenitore.  
  
 ![Flusso di controllo con sei attività e un contenitore](../../integration-services/control-flow/media/ssis-controlflowelmt.gif "Flusso di controllo con sei attività e un contenitore")  
  
 L'architettura di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] supporta la nidificazione dei contenitori e un flusso di controllo può includere più livelli di contenitori nidificati. Un pacchetto può ad esempio includere un contenitore quale Ciclo Foreach, che a sua volta può includere un altro contenitore Ciclo Foreach e così via.  
  
 Anche i gestori di eventi includono flussi di controllo, che vengono compilati utilizzando gli stessi tipi di elementi del flusso di controllo.  
  
## Implementazione del flusso di controllo  
 Il flusso di controllo in un pacchetto viene creato tramite la scheda **Flusso di controllo** di Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Quando la scheda **Flusso di controllo** è attiva, nella Casella degli strumenti sono elencati i contenitori e le attività che è possibile aggiungere al flusso di controllo.  
  
 Nella figura seguente viene illustrato il flusso di controllo di un semplice pacchetto nella finestra di progettazione del flusso di controllo. Il flusso di controllo illustrato nella figura è composto da tre attività a livello di pacchetto e da un contenitore a livello di pacchetto contenente tre attività. Le attività e il contenitore sono connessi tramite vincoli di precedenza.  
  
 ![Schermata della finestra di progettazione del flusso di controllo con pacchetto](../../integration-services/control-flow/media/samplecontrolflow.gif "Schermata della finestra di progettazione del flusso di controllo con pacchetto")  
  
 Per creare un flusso di controllo è necessario eseguire i passaggi seguenti:  
  
-   Aggiungere contenitori che implementano flussi di lavoro ripetuti in un pacchetto o suddividono il flusso di controllo in subset.  
  
-   Aggiungere attività che supportano il flusso di dati, preparano i dati, implementano script ed eseguono funzioni di flusso di lavoro e Business Intelligence.  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include un'ampia gamma di attività che è possibile usare per creare un flusso di controllo in grado di soddisfare i requisiti aziendali del pacchetto. Se il pacchetto deve gestire dati, il flusso di controllo dovrà includere almeno un'attività Flusso di dati. Un pacchetto può ad esempio estrarre dati, aggregarne i valori e quindi scrivere i risultati in un'origine dei dati.  Per altre informazioni, vedere [Attività di Integration Services](../../integration-services/control-flow/integration-services-tasks.md) e [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md).  
  
-   Connettere contenitori e attività tramite vincoli di precedenza, in modo da formare un flusso di controllo ordinato.  
  
     Dopo l'aggiunta di un'attività o un contenitore all'area di progettazione della scheda **Flusso di controllo**, Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] aggiunge automaticamente un connettore a tale elemento. Se in un pacchetto sono inclusi due o più elementi, attività o contenitori, sarà possibile crearne un join in modo da formare un flusso di controllo trascinandone i connettori da un elemento all'altro.  
  
     Il connettore tra due elementi rappresenta un vincolo di precedenza, che definisce la relazione tra i due elementi connessi. Specifica infatti l'ordine in cui attività e contenitori devono essere eseguiti in fase di esecuzione, nonché le condizioni in cui tali attività e contenitori devono essere eseguiti. Un vincolo di precedenza può ad esempio specificare che una determinata attività deve essere completata, affinché sia possibile eseguire l'attività successiva nel flusso di controllo. Per altre informazioni, vedere [Vincoli di precedenza](../../integration-services/control-flow/precedence-constraints.md).  
  
-   Aggiunta di gestioni connessioni.  
  
     Molte attività richiedono una connessione a un'origine dei dati ed è pertanto necessario aggiungere al pacchetto le gestioni connessioni richieste dalle attività. A seconda del tipo di enumeratore utilizzato, anche il contenitore Ciclo Foreach può richiedere una gestione connessione. È possibile aggiungere le gestioni connessioni durante la costruzione del flusso di controllo elemento per elemento oppure prima di iniziare la costruzione del flusso di controllo. Per altre informazioni, vedere [Connessioni in Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md) e [Creazione di gestioni connessioni](../Topic/Create%20Connection%20Managers.md).  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] Progettazione SSIS include inoltre molte funzionalità della modalità progettazione che è possibile usare per gestire l'area di progettazione e creare un flusso di controllo autodocumentato.  
  
## Attività correlate  
  
-   [Aggiunta o eliminazione di un'attività o un contenitore in un flusso di controllo](../../integration-services/control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
  
-   [Impostazione delle proprietà di un'attività o di un contenitore](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
-   [Raggruppare o separare componenti](../../integration-services/group-or-ungroup-components.md)  
  
  