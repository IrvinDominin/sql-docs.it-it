---
title: "Replica di tabelle e indici partizionati | Microsoft Docs"
ms.custom: ""
ms.date: "09/10/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "indici partizionati [SQL Server], replica"
  - "tabelle partizionate [SQL Server], replica"
  - "replica [SQL Server], tabelle partizionate"
  - "pubblicazione [replica di SQL Server], tabelle partizionate"
  - "replica transazionale, tabelle partizionate"
ms.assetid: c9fa81b1-6c81-4c11-927b-fab16301a8f5
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Replica di tabelle e indici partizionati
  Il partizionamento semplifica la gestione di indici e tabelle di grandi dimensioni, in quanto consente di gestire e accedere in modo rapido ed efficace a subset di dati, preservando al contempo l'integrità di una raccolta dati. Per ulteriori informazioni, vedere [Partitioned Tables and Indexes](../../../relational-databases/partitions/partitioned-tables-and-indexes.md). La replica supporta il partizionamento fornendo un set di proprietà che specificano la modalità di gestione di tabelle e indici partizionati.  
  
## Proprietà degli articoli per la replica transazionale e di tipo merge  
 Nella tabella seguente sono inclusi gli oggetti utilizzati per partizionare i dati.  
  
|Oggetto|Creato tramite|  
|------------|----------------------|  
|Tabella o indice partizionato|CREATE TABLE o CREATE INDEX|  
|Funzione di partizione|CREATE PARTITION FUNCTION|  
|Schema di partizione|CREATE PARTITION SCHEME|  
  
 Il primo set di proprietà correlato al partizionamento è costituito dalle opzioni dello schema dell'articolo che determinano se gli oggetti di partizionamento devono essere copiati nel Sottoscrittore. È possibile impostare tali opzioni nei modi seguenti:  
  
-   Nella pagina **Proprietà articolo** della Creazione guidata nuova pubblicazione o nella finestra di dialogo Proprietà pubblicazione. Per copiare gli oggetti elencati nella tabella precedente, specificare un valore **true** per le proprietà **Copia schemi di partizione delle tabelle** e **Copia schemi di partizione dell'indice**. Per informazioni sulle modalità di accesso di **Proprietà articolo** pagina, vedere [visualizzare e modificare le proprietà di pubblicazione](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
-   Tramite il *schema_option* parametro di una delle stored procedure seguenti:  
  
    -   [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) o [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) per la replica transazionale  
  
    -   [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) o [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) per la replica di tipo merge  
  
     Per copiare gli oggetti elencati nella tabella precedente, specificare i valori dell'opzione dello schema appropriati. Per informazioni su come specificare le opzioni dello schema, vedere [Specify Schema Options](../../../relational-databases/replication/publish/specify-schema-options.md).  
  
 Tramite la replica vengono copiati gli oggetti nel Sottoscrittore durante la sincronizzazione iniziale. Se lo schema di partizione utilizza filegroup diversi dal filegroup PRIMARY, tali filegroup devono essere presenti nel Sottoscrittore prima della sincronizzazione iniziale.  
  
 Al termine dell'inizializzazione del Sottoscrittore, le modifiche dei dati vengono propagate al Sottoscrittore e applicate alle partizioni appropriate. Non sono tuttavia supportate le modifiche allo schema di partizione. Le repliche transazionale e di tipo merge non supportano la replica dei comandi seguenti: ALTER PARTITION FUNCTION, ALTER PARTITION SCHEME e l'istruzione REBUILD WITH PARTITION di ALTER INDEX. Le modifiche associate non verranno replicate automaticamente nel sottoscrittore. È responsabilità dell'utente apportare manualmente modifiche simili nel Sottoscrittore.  
  
## Supporto della replica per il cambio della partizione  
 Uno dei vantaggi principali del partizionamento di tabelle consiste nella possibilità di spostare in modo rapido ed efficiente subset di dati tra partizioni. I dati vengono spostati utilizzando il comando SWITCH PARTITION. Per impostazione predefinita, quando una tabella è abilitata per la replica, le operazioni SWITCH PARTITION sono bloccate per i motivi seguenti:  
  
-   Se i dati vengono spostati all'interno o all'esterno di una tabella presente nel server di pubblicazione ma non nel Sottoscrittore, il server di pubblicazione e il Sottoscrittore potrebbero risultare incoerenti uno rispetto all'altro. Questo problema si verifica in genere quando i dati vengono spostati all'interno o all'esterno di una tabella di gestione temporanea.  
  
-   Se il Sottoscrittore ha una definizione diversa per la tabella partizionata rispetto al server di pubblicazione, l'esecuzione dell'agente di distribuzione verrà interrotta quando questo tenta di applicare le modifiche nel Sottoscrittore.  
  
 Nonostante questi possibili problemi, il cambio della partizione può essere abilitato per la replica transazionale. Prima di abilitare il cambio della partizione, assicurarsi che tutte le tabelle interessate siano presenti nel server di pubblicazione e nel Sottoscrittore e verificare che le definizioni di tabella e di partizione siano identiche.  
  
 Quando delle partizioni è esatto stesso schema di partizione al server di pubblicazione e nei Sottoscrittori, è possibile abilitare *allow_partition_switch* insieme a *replication_partition_switch* che verranno replicate solo l'istruzione switch della partizione al sottoscrittore. È inoltre possibile attivare *allow_partition_switch* senza la replica della DDL. Questa operazione risulta utile nel caso in cui si desideri eseguire il roll out dei mesi precedenti della partizione ma mantenendo la partizione replicata per un altro anno per scopi di backup nel Sottoscrittore.  
  
 Se si abilita il cambio della partizione usando la versione corrente in SQL Server 2008 R2, successivamente potrebbero essere necessarie anche operazioni di divisione e merge. Prima di eseguire un'operazione di divisione o di unione su una tabella replicata assicurarsi che la partizione in questione non abbia comandi replicati in sospeso. È anche necessario assicurarsi che nessuna operazione DML venga eseguita sulla partizione durante le operazioni di divisione e unione. Se sono presenti transazioni non elaborate dalla lettura log o se le operazioni DML vengono eseguite in una partizione di una tabella replicata durante l'esecuzione di un'operazione di divisione o di merge che coinvolge tale partizione, si potrebbe verificare un errore di elaborazione nell'agente di lettura log. Per correggere l'errore è necessaria una reinizializzazione della sottoscrizione.  
  
> [!WARNING]  
>  Non è necessario abilitare il cambio della partizione per pubblicazioni peer-to-peer, a causa della colonna nascosta utilizzata per rilevare e risolvere conflitti.  
  
### Abilitazione del cambio della partizione  
 Le proprietà seguenti per le pubblicazioni transazionali consentono agli utenti di controllare il comportamento del cambio della partizione in un ambiente replicato:  
  
-   **@allow_partition_switch**, se impostato su **true**, è possibile eseguire SWITCH PARTITION sul database di pubblicazione.  
  
-   **@replicate_partition_switch** determina se l'istruzione SWITCH PARTITION DDL deve essere replicata ai sottoscrittori. Questa opzione è valida solo quando **@allow_partition_switch** è impostato su **true**.  
  
 È possibile impostare queste proprietà utilizzando [sp_addpublication](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) quando viene creata la pubblicazione oppure utilizzando [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) dopo la creazione della pubblicazione. Come notato in precedenza, la replica di tipo merge non supporta il cambio della partizione. Per eseguire SWITCH PARTITION in una tabella abilitata per la replica di tipo merge, rimuovere la tabella dalla pubblicazione.  
  
## Vedere anche  
 [Pubblicazione di dati e oggetti di database](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  