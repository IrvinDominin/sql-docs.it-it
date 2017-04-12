---
title: "Destinazione OLE DB | Microsoft Docs"
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
  - "sql13.dts.designer.oledbdest.f1"
helpviewer_keywords: 
  - "modalità di accesso ai dati con caricamento rapido [Integration Services]"
  - "destinazione OLE DB [Integration Services]"
  - "opzioni di caricamento rapido [Integration Services]"
  - "opzioni di caricamento rapido [Integration Services]"
  - "destinazioni [Integration Services], OLE DB"
  - "modalità di accesso ai dati con caricamento rapido [Integration Services]"
  - "inserimento di dati"
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
caps.latest.revision: 79
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 79
---
# Destinazione OLE DB
  La destinazione OLE DB consente di caricare dati in un'ampia gamma di database conformi con OLE DB, tramite una tabella o vista di database oppure un comando SQL. L'origine OLE DB, ad esempio, può caricare dati nelle tabelle dei database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Se l'origine dati è [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, è richiesta una gestione connessione diversa rispetto alle versioni precedenti di Excel. Per altre informazioni, vedere [Connessione a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md).  
  
 Sono disponibili cinque diverse modalità di accesso ai dati per il caricamento dei dati:  
  
-   Vista o tabella. È possibile specificare una vista o tabella esistente o creare una nuova tabella.  
  
-   Vista o tabella che utilizza opzioni per il caricamento rapido. È possibile specificare una tabella esistente o creare una nuova tabella.  
  
-   Vista o tabella specificata in una variabile.  
  
-   Vista o tabella specificata in una variabile che utilizza opzioni per il caricamento rapido.  
  
-   Risultato di un'istruzione SQL.  
  
> [!NOTE]  
>  La destinazione OLE DB non supporta parametri. Per eseguire un'istruzione INSERT con parametri, è possibile utilizzare la trasformazione Comando OLE DB. Per altre informazioni, vedere [Trasformazione Comando OLE DB](../../integration-services/data-flow/transformations/ole-db-command-transformation.md).  
  
 Quando nella destinazione OLE DB vengono caricati dati che utilizzano un Double-Byte Character Set (DBCS), è possibile che tali dati vengano danneggiati se nella modalità di accesso non viene utilizzata l'opzione di caricamento rapido e la gestione connessione OLE DB utilizza il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB). Per assicurare l'integrità dei dati DBCS è necessario configurare Gestione connessione OLE DB in modo da usare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client o una delle modalità di accesso con caricamento rapido: **Tabella o vista - Caricamento rapido** o **Variabile nome vista o nome tabella - Caricamento rapido**. Entrambe le opzioni sono disponibili nella finestra di dialogo **Editor destinazione OLE DB**. Durante la programmazione modello a oggetti di [!INCLUDE[ssIS](../../includes/ssis-md.md)], è necessario impostare la proprietà AccessMode su **OpenRowset con FastLoad** o **OpenRowset con FastLoad da variabile**.  
  
> [!NOTE]  
>  Se si usa la finestra di dialogo **Editor destinazione OLE DB[!INCLUDE[ssIS](../../includes/ssis-md.md)] in Progettazione ** per creare la tabella di destinazione in cui la destinazione OLE DB inserisce i dati, sarà necessario selezionare la nuova tabella manualmente. È necessario eseguire la selezione manuale quando un provider OLE DB, ad esempio il provider Microsoft OLE DB per DB2, aggiunge automaticamente gli identificatori di schema al nome della tabella.  
  
> [!NOTE]  
>  In base al tipo di destinazione può essere necessario modificare l'istruzione CREATE TABLE generata dalla finestra di dialogo **Editor destinazione OLE DB**. Alcune destinazioni non supportano ad esempio i tipi di dati utilizzati dall'istruzione CREATE TABLE.  
  
 Per connettersi a un'origine dei dati questa destinazione utilizza una gestione connessione OLE DB, che specifica il provider OLE DB da utilizzare. Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
 Con un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] viene inoltre fornito l'oggetto di origine dati da cui è possibile creare una gestione connessione OLE DB, rendendo disponibili origini dati e viste origine dati alla destinazione OLE DB.  
  
 Una destinazione OLE DB include i mapping tra le colonne di input e quelle nell'origine dei dati della destinazione. Non è necessario eseguire il mapping delle colonne di input a tutte le colonne di destinazione ma, a seconda delle proprietà delle colonne di destinazione, se alle colonne di destinazione non corrispondono colonne di input è possibile che vengano generati errori. Se, ad esempio, una colonna di destinazione non ammette valori Null, sarà necessario eseguire il mapping di una colonna di input a tale colonna. È inoltre necessario che i tipi di dati delle colonne di cui è stato eseguito il mapping siano compatibili. Non è ad esempio possibile eseguire il mapping di una colonna di input con un tipo di dati string a una colonna di destinazione con un tipo di dati numeric.  
  
 La destinazione OLE DB include un input regolare e un output degli errori.  
  
 Per altre informazioni sui tipi di dati, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
## Opzioni per il caricamento rapido  
 Se la destinazione OLE DB usa una modalità di accesso ai dati con caricamento rapido, nell'interfaccia utente della destinazione, ovvero in **Editor destinazione OLE DB**, sarà possibile specificare le opzioni di caricamento rapido seguenti:  
  
-   È possibile mantenere i valori Identity del file di dati importato o utilizzare valori univoci assegnati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   È possibile mantenere i valori Null durante le operazioni di caricamento bulk.  
  
-   È possibile controllare i vincoli sulla tabella o vista di destinazione durante le operazioni di importazione bulk.  
  
-   È possibile acquisire un blocco a livello di tabella per la durata dell'operazione di caricamento bulk.  
  
-   È possibile specificare il numero di righe nel batch e le dimensioni del commit.  
  
 Alcune opzioni di caricamento rapido sono archiviate in proprietà specifiche della destinazione OLE DB. Ad esempio, FastLoadKeepIdentity specifica se mantenere i valori Identity, FastLoadKeepNulls specifica se mantenere i valori Null e FastLoadMaxInsertCommitSize specifica il numero di righe di cui eseguire il commit come batch. Altre opzioni di caricamento rapido sono archiviate in un elenco con valori delimitati da virgole nella proprietà FastLoadOptions. Se la destinazione OLE DB usa tutte le opzioni di caricamento rapido archiviate in FastLoadOptions ed elencate nella finestra di dialogo **Editor destinazione OLE DB**, il valore della proprietà verrà impostato su **TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000**. Il valore 1000 indica che la destinazione è configurata per l'utilizzo di batch di 1000 righe.  
  
> [!NOTE]  
>  Un eventuale esito negativo della verifica dei vincoli nella destinazione causa l'interruzione dell'intero batch di righe definito da FastLoadMaxInsertCommitSize.  
  
 Oltre alle opzioni di caricamento rapido elencate nella finestra di dialogo **Editor destinazione OLE DB**, è possibile configurare la destinazione OLE DB in modo da usare le opzioni per il caricamento bulk seguenti digitandole nella proprietà FastLoadOptions della finestra di dialogo **Editor avanzato**.  
  
|Opzione per il caricamento rapido|Description|  
|----------------------|-----------------|  
|KILOBYTES_PER_BATCH|Specifica le dimensioni in kilobyte del batch da inserire. L'opzione ha il formato **KILOBYTES_PER_BATCH** = \< valore intero positivo**>**.|  
|FIRE_TRIGGERS|Specifica se attivare o meno i trigger sulla tabella inserita. La sintassi dell'opzione è **FIRE_TRIGGERS**. La presenza dell'opzione indica che i trigger vengono attivati.|  
|ORDER|Specifica la modalità con ordinare i dati in input. La sintassi dell'opzione è la seguente: ORDER \<nome colonna> ASC&#124;DESC. È possibile elencare qualsiasi numero di colonne e l'indicazione del tipo di ordinamento è facoltativa. Se il tipo di ordinamento viene omesso, l'operazione di inserimento verrà eseguita presupponendo che i dati non siano ordinati.<br /><br /> Nota: è possibile migliorare le prestazioni usando l'opzione ORDER per ordinare i dati di input in base all'indice cluster nella tabella.|  
  
 Anche se nelle parole chiave non viene rilevata la distinzione tra maiuscole e minuscole, le parole chiave [!INCLUDE[tsql](../../includes/tsql-md.md)] vengono in genere digitate in maiuscolo.  
  
 Per sapere di più sulle opzioni di caricamento rapido, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
## Risoluzione dei problemi relativi alla destinazione OLE DB  
 È possibile registrare le chiamate eseguite dalla destinazione OLE DB a provider di dati esterni. Questa funzionalità di registrazione può essere utilizzata per risolvere i problemi relativi al salvataggio di dati in origini dati esterne da parte della destinazione OLE DB. Per registrare le chiamate eseguite dalla destinazione OLE DB a provider di dati esterni, attivare la registrazione dei pacchetti e selezionare l'evento **Diagnostic** a livello di pacchetto. Per altre informazioni, vedere [Risoluzione dei problemi relativi agli strumenti per l'esecuzione del pacchetto](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## Configurazione della destinazione OLE DB  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor destinazione OLE DB**, fare clic su uno degli argomenti seguenti:  
  
-   [Editor destinazione OLE DB &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/ole-db-destination-editor-connection-manager-page.md)  
  
-   [Editor destinazione OLE DB &#40;pagina Mapping&#41;](../../integration-services/data-flow/ole-db-destination-editor-mappings-page.md)  
  
-   [Editor destinazione OLE DB &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/ole-db-destination-editor-error-output-page.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate OLE DB](../../integration-services/data-flow/ole-db-custom-properties.md)  
  
 Per ulteriori informazioni sulle procedure per l'impostazione delle proprietà, fare clic su uno degli argomenti seguenti:  
  
-   [Caricamento dei dati tramite la destinazione OLE DB](../../integration-services/data-flow/load-data-by-using-the-ole-db-destination.md)  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Contenuto correlato  
 [Origine OLE DB](../../integration-services/data-flow/ole-db-source.md)  
  
 [Variabili di Integration Services &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  
  
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  