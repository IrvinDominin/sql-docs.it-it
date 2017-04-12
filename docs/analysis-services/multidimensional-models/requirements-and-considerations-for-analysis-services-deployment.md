---
title: "Requisiti e considerazioni per la distribuzione di Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "memoria [Analysis Services]"
  - "scalabilità [Analysis Services]"
  - "spazio [Analysis Services]"
  - "distribuzioni di Analysis Services, requisiti"
  - "distribuzione [Analysis Services], requisiti"
  - "spazio su disco [Analysis Services]"
  - "requisiti [Analysis Services]"
  - "processori [Analysis Services]"
  - "requisiti di sistema [Analysis Services]"
  - "disponibilità [Analysis Services]"
ms.assetid: ef1387a5-5137-4ef4-b731-fec347e5f5ed
caps.latest.revision: 27
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 26
---
# Requisiti e considerazioni per la distribuzione di Analysis Services
  Le prestazioni e la disponibilità di una soluzione dipendono da molti fattori, tra cui le funzionalità dell'hardware sottostante, la topologia della distribuzione server, le caratteristiche della soluzione (ad esempio, con partizioni distribuite in più server o usando l'archiviazione ROLAP per la quale è richiesto l'accesso diretto al motore relazionale), i contratti di servizio e la complessità del modello di dati.  
  
## Requisiti relativi a memoria e processore  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è necessaria una quantità maggiore di risorse di memoria e processore nei casi seguenti:  
  
-   In caso di elaborazione di cubi di grandi dimensioni o complessi. Questi cubi richiedono maggiori risorse di memoria e processore rispetto ai cubi di piccole dimensioni o semplici.  
  
-   In caso di aumento del numero di cubi in un unico database.  
  
-   In caso di aumento del numero di database in un'unica istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
-   In caso di aumento del numero di istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un unico computer.  
  
-   In caso di aumento del numero di utenti che accedono contemporaneamente alle risorse di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Il numero di risorse in termini di memoria e processore disponibili per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] varia a seconda dell'edizione di SQL Server, del sistema operativo, della capacità hardware e se si usano processori virtuali o fisici. Per altre informazioni, vedere i collegamenti seguenti:  
  
 [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)  
  
 [Limiti della capacità di calcolo per edizione di SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)  
  
 [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
  
 [Specifiche di capacità massima &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/olap-physical/maximum-capacity-specifications-analysis-services.md)  
  
## Requisiti relativi allo spazio su disco  
 Per i diversi aspetti dell'installazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e le diverse attività correlate all'elaborazione degli oggetti sono necessarie quantità di spazio su disco differenti. Nell'elenco seguente vengono descritti questi requisiti.  
  
 Cubi  
 I cubi che includono tabelle dei fatti di grandi dimensioni richiedono una quantità maggiore di spazio su disco rispetto a quelli contenenti tabelle dei fatti di piccole dimensioni. Analogamente, sebbene in proporzioni minori, i cubi che includono un numero elevato di dimensioni grandi richiedono una maggiore quantità di spazio su disco rispetto ai cubi che contengono un numero minore di membri della dimensione. In genere, un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] richiede approssimativamente il 20% dello spazio su disco necessario per gli stessi dati archiviati nel database relazionale sottostante.  
  
 Aggregations  
 Le aggregazioni richiedono spazio su disco aggiuntivo in modo proporzionale al numero di aggregazioni aggiunte: maggiore è il numero di aggregazioni, maggiore sarà lo spazio necessario. Se si evita la creazione di aggregazioni non necessarie, lo spazio su disco aggiuntivo necessario per le aggregazioni non supera in genere il 10% circa della dimensione dei dati archiviati nel database relazionale sottostante.  
  
 Data Mining  
 Per impostazione predefinita, le strutture di data mining memorizzano nella cache il set di dati in cui viene eseguito il training. Per rimuovere dal disco i dati presenti nella cache, è possibile usare l'opzione di elaborazione **Elaborazione struttura pulita** nell'oggetto struttura di data mining. Per altre informazioni, vedere [Requisiti e considerazioni sull'elaborazione &#40;data mining&#41;](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).  
  
 Elaborazione di oggetti  
 Durante l'elaborazione, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] archivia le copie degli oggetti in fase di elaborazione nella transazione di elaborazione sul disco fino al termine del processo. Al termine dell'elaborazione, le copie elaborate degli oggetti sostituiscono gli oggetti originali. È pertanto necessario verificare che vi sia spazio su disco aggiuntivo sufficiente per una seconda copia di ogni oggetto da elaborare. Se, ad esempio, si desidera elaborare un intero cubo in un'unica transazione, è necessario disporre di spazio su disco sufficiente per l'archiviazione di una seconda copia dell'intero cubo.  
  
##  <a name="BKMK_Availability"></a> Considerazioni sulla disponibilità  
 In un ambiente [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] un cubo o un modello di data mining potrebbe non essere disponibile per l'esecuzione di query a causa di un problema hardware o software. Un cubo potrebbe inoltre non essere disponibile in quanto necessita di essere elaborato.  
  
### Metodi per garantire la disponibilità in caso di problemi hardware o software  
 I componenti hardware o software possono presentare problemi per vari motivi. Per garantire la disponibilità dell'installazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non è tuttavia sufficiente risolvere questi problemi, ma è anche necessario offrire risorse alternative che consentano all'utente di continuare a usare un sistema in caso di errore. Spesso per offrire le risorse alternative necessarie a mantenere la disponibilità in caso di problema hardware o software vengono usati server di clustering o di bilanciamento del carico.  
  
 Per offrire un'alternativa in caso di problema hardware o software, valutare l'opportunità di distribuire [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un cluster di failover. In un cluster di failover se nel nodo primario si verifica un errore per qualsiasi motivo oppure se è necessario riavviare tale nodo, le funzionalità di clustering di failover di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows consentono di eseguire il failover a un nodo secondario. Dopo il failover, che avviene in modo molto rapido, quando gli utenti eseguono query accedono all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in esecuzione nel nodo secondario. Per ulteriori informazioni sui cluster di failover, vedere la pagina relativa ai [cluster di failover (tecnologie di Windows Server)](http://technet.microsoft.com/library/cc732488\(v=WS.10\).aspx).  
  
 Un'altra soluzione utile per risolvere i problemi di disponibilità consiste nel distribuire il progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in due o più server di produzione. Sarà quindi possibile usare la funzionalità di bilanciamento del carico di rete dei server Windows per combinare i server di produzione in un unico cluster. In un cluster con bilanciamento carico di rete, se un server non è disponibile a causa di problemi hardware o software, tramite il servizio di bilanciamento carico di rete le query degli utenti vengono indirizzate ai server ancora disponibili.  
  
### Metodi per garantire la disponibilità durante l'elaborazione di modifiche strutturali  
 Determinate modifiche apportate a un cubo possono rendere i l cubo non disponibile fino al termine dell'elaborazione. Se, ad esempio, si apportano modifiche strutturali a una dimensione in un cubo, non è sufficiente rielaborare la dimensione, ma è necessario elaborare anche ogni cubo che usano la dimensione modificata. Durante l'elaborazione di tali cubi, gli utenti non possono eseguire query su di essi né sui modelli di data mining basati su un cubo contenente una dimensione modificata.  
  
 Per offrire la disponibilità durante l'elaborazione di modifiche strutturali che potrebbero riguardare uno o più cubi in un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , valutare l'opportunità di usare un server dell'area di gestione temporanea e la Sincronizzazione guidata database. Questa funzionalità consente di aggiornare i dati e i metadati in un server dell'area di gestione temporanea e quindi di eseguire una sincronizzazione online del server di produzione e del server dell'area di gestione temporanea. Per altre informazioni, vedere [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md).  
  
 Per elaborare in modo trasparente gli aggiornamenti incrementali ai dati di origine, abilitare il caching attivo. Tramite il caching attivo i cubi vengono aggiornati con i nuovi dati di origine senza che sia necessaria l'elaborazione manuale e senza influire sulla disponibilità dei cubi. Per altre informazioni, vedere [Memorizzazione nella cache attiva &#40;partizioni&#41;](../Topic/Proactive%20Caching%20\(Partitions\).md).  
  
##  <a name="BKMK_Scalability"></a> Considerazioni sulla scalabilità  
 La presenza di più istanze di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nello stesso computer può causare problemi di prestazioni. Per risolvere questi problemi, un'opzione consiste nell'aumentare le risorse di memoria, processore e disco nel server. Potrebbe inoltre essere necessario distribuire le istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in più computer.  
  
### Distribuzione di Analysis Services in più computer  
 È possibile distribuire un'installazione di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in più computer in diversi modi. Le opzioni disponibili sono descritte nell'elenco seguente.  
  
-   Se vi sono più istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un unico computer, è possibile spostare una o più istanze in un altro computer.  
  
-   Se vi sono più database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un unico computer, è possibile spostare uno o più database nella relativa istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un computer diverso.  
  
-   Se uno o più database relazionali forniscono dati a un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , è possibile spostare questi database in un computer diverso. Prima di spostare i database, valutare la velocità di rete e la larghezza di banda tra il database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e i database sottostanti. Se la rete è lenta o sovraccarica, lo spostamento dei database sottostanti in un computer diverso influirà negativamente sulle prestazioni di elaborazione.  
  
-   Se le operazioni di elaborazione influiscono sulle prestazioni di esecuzione delle query, ma non è possibile eseguire tali operazioni durante i periodi in cui il carico di query è ridotto, valutare l'opportunità di spostare le attività di elaborazione in un server dell'area di gestione temporanea e quindi di eseguire una sincronizzazione online del server di produzione e del server dell'area di gestione temporanea. Per altre informazioni, vedere [Sincronizzare database di Analysis Services](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md). È inoltre possibile distribuire le attività di elaborazione tra più istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tramite partizioni remote. Per l'elaborazione delle partizioni remote vengono usate risorse di memoria e processore nel server remoto anziché nel computer locale. Per altre informazioni sulla gestione delle partizioni remote, vedere [Creare e gestire una partizione remota &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md).  
  
-   Se le prestazioni di esecuzione delle query non sono soddisfacenti, ma non è possibile aumentare le risorse di memoria e processore nel server locale, valutare l'opportunità di distribuire un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in due o più server di produzione. Sarà quindi possibile usare la funzionalità di bilanciamento del carico di rete per combinare i server in un unico cluster. In un cluster con bilanciamento carico di rete, le query vengono automaticamente distribuite tra tutti i server del cluster.  
  
  