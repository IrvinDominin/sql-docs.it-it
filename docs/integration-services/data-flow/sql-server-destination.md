---
title: "Destinazione SQL Server | Microsoft Docs"
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
  - "sql13.dts.designer.sqlserverdest.f1"
helpviewer_keywords: 
  - "SQL Server - destinazione"
  - "caricamento di dati"
  - "destinazioni [Integration Services], SQL Server"
  - "inserimento di dati"
  - "caricamento bulk [Integration Services]"
ms.assetid: a0227cd8-6944-4547-87e8-7b2507e26442
caps.latest.revision: 65
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 65
---
# Destinazione SQL Server
  La destinazione SQL Server si connette a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] locale ed esegue il caricamento bulk dei dati nelle tabelle e nelle viste di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Non è possibile usare la destinazione SQL Server nei pacchetti che accedono a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un server remoto. Per tali pacchetti, utilizzare la destinazione OLE DB. Per altre informazioni, vedere [OLE DB Destination](../../integration-services/data-flow/ole-db-destination.md).  
  
## Permissions  
 Gli utenti che eseguono pacchetti che includono la destinazione SQL Server devono disporre dell'autorizzazione "Creazione oggetti globali", che può essere concessa tramite lo strumento Criteri di sicurezza locali, accessibile dal menu **Strumenti di amministrazione**. Se durante l'esecuzione di un pacchetto che utilizza la destinazione SQL Server viene visualizzato un messaggio di errore, verificare che l'account utilizzato per eseguire il pacchetto disponga dell'autorizzazione "Creazione oggetti globali".  
  
## Inserimenti bulk  
 Se si tenta di utilizzare la destinazione SQL Server per il caricamento bulk dei dati in un database remoto di SQL Server, potrebbe venire visualizzato un messaggio di errore simile a "È disponibile un record OLE DB. Origine: "Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client" Hresult: 0x80040E14 Descrizione: "Impossibile eseguire il caricamento bulk perché non è stato possibile aprire l'oggetto di mapping dei file SSIS 'Global\DTSQLIMPORT'. Codice di errore del sistema operativo 2 (Impossibile trovare il file specificato). Verificare che l'accesso venga effettuato a un server locale tramite la sicurezza di Windows.""  
  
 La destinazione SQL Server offre lo stesso tipo di inserimento dei dati ad alta velocità in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] garantito dall'attività Inserimento bulk. Se si usa la destinazione SQL Server, tuttavia, un pacchetto può applicare le trasformazioni ai dati delle colonne prima che vengano caricati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Per il caricamento dei dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], è consigliabile utilizzare la destinazione SQL Server invece della destinazione OLE DB.  
  
### Opzioni per l'inserimento bulk  
 Se la destinazione SQL Server utilizza una modalità di accesso ai dati con caricamento rapido, sarà possibile specificare le opzioni di caricamento rapido seguenti:  
  
-   È possibile mantenere i valori Identity del file di dati importato o utilizzare valori univoci assegnati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   È possibile mantenere i valori Null durante l'operazione di caricamento bulk.  
  
-   È possibile verificare i vincoli sulla tabella o vista di destinazione durante l'operazione di importazione bulk.  
  
-   È possibile acquisire un blocco a livello di tabella per la durata dell'operazione di caricamento bulk.  
  
-   È possibile eseguire trigger di inserimento definiti sulla tabella di destinazione durante l'operazione di caricamento bulk.  
  
-   È possibile specificare il numero della prima riga nell'input da caricare durante l'operazione di inserimento bulk.  
  
-   È possibile specificare il numero dell'ultima riga nell'input da caricare durante l'operazione di inserimento bulk.  
  
-   È possibile specificare il numero massimo di errori che si possono verificare prima che l'operazione di caricamento bulk venga annullata. Ogni riga che non può essere importata viene conteggiata come errore.  
  
-   È possibile specificare le colonne nell'input che contengono dati ordinati.  
  
 Per altre informazioni sulle opzioni di caricamento bulk, vedere [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md).  
  
#### Miglioramenti alle prestazioni  
 Per migliorare le prestazioni dell'inserimento bulk e dell'accesso ai dati delle tabelle durante un'operazione di inserimento bulk, modificare le opzioni predefinite nel modo seguente:  
  
-   Non verificare i vincoli sulla tabella o vista di destinazione durante l'operazione di importazione bulk.  
  
-   Non eseguire trigger di inserimento definiti sulla tabella di destinazione durante l'operazione di caricamento bulk.  
  
-   Non applicare blocchi alla tabella, in modo che rimanga disponibile ad altri utenti e applicazioni durante l'operazione di inserimento bulk.  
  
## Configurazione della destinazione SQL Server  
 È possibile configurare la destinazione SQL Server nei modi seguenti:  
  
-   Specificare la tabella o vista in cui eseguire il caricamento bulk dei dati.  
  
-   Personalizzare l'operazione di caricamento bulk specificando opzioni quale il controllo dei vincoli.  
  
-   Specificare se deve essere eseguito il commit di tutte le righe in un batch oppure impostare il numero massimo di righe di cui eseguire il commit in un batch.  
  
-   Specificare un timeout per l'operazione di caricamento bulk.  
  
 Per connettersi a un'origine dei dati questa destinazione utilizza una gestione connessione OLE DB, che specifica il provider OLE DB da utilizzare. Per altre informazioni, vedere [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md).  
  
 Un progetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fornisce inoltre l'oggetto origine dei dati da cui è possibile creare una gestione connessione OLE DB, in modo da rendere disponibili le origini dei dati e le viste origine dati alla destinazione SQL Server.  
  
 La destinazione SQL Server include un input. Non supporta un output degli errori.  
  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Per altre informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor destinazione SQL Server**, fare clic su uno degli argomenti seguenti:  
  
-   [Editor destinazione SQL &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/sql-destination-editor-connection-manager-page.md)  
  
-   [Editor destinazione SQL &#40;pagina Mapping&#41;](../../integration-services/data-flow/sql-destination-editor-mappings-page.md)  
  
-   [Editor destinazione SQL &#40;pagina Avanzate&#41;](../../integration-services/data-flow/sql-destination-editor-advanced-page.md)  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../Topic/Common%20Properties.md)  
  
-   [Proprietà personalizzate della destinazione SQL Server](../../integration-services/data-flow/sql-server-destination-custom-properties.md)  
  
 Per ulteriori informazioni sulle procedure per l'impostazione delle proprietà, fare clic su uno degli argomenti seguenti:  
  
-   [Caricamento bulk dei dati tramite la destinazione SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Attività correlate  
  
-   [Caricamento bulk dei dati tramite la destinazione SQL Server](../../integration-services/data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
-   [Impostazione delle proprietà di un componente del flusso di dati](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
## Contenuto correlato  
  
-   Articolo tecnico [You may get "Unable to prepare the SSIS bulk insert for data insertion" error on UAC enabled systems](http://go.microsoft.com/fwlink/?LinkId=199482) (Possibile visualizzazione dell'errore "Impossibile preparare l'attività Inserimento bulk SSIS per l'inserimento dei dati" nei sistemi con Controllo account utente abilitato) nel sito support.microsoft.com.  
  
-   Articolo tecnico [The Data Loading Performance Guide](http://go.microsoft.com/fwlink/?LinkId=233700) (Guida alle prestazioni del caricamento dati) nel sito msdn.microsoft.com.  
  
-   Articolo tecnico [Using SQL Server Integration Services to Bulk Load Data](http://go.microsoft.com/fwlink/?LinkId=233701) (Uso di SQL Server Integration Services per il caricamento bulk dei dati) nel sito Web simple-talk.com.  
  
## Vedere anche  
 [Flusso di dati](../../integration-services/data-flow/data-flow.md)  
  
  