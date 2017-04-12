---
title: "Editor origine OLE DB (pagina Gestione connessione) | Microsoft Docs"
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
  - "sql13.dts.designer.oledbsourceadapter.connection.f1"
helpviewer_keywords: 
  - "Editor origine OLE DB"
ms.assetid: 53699902-8699-4547-b56b-a5b2079e98b6
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 42
---
# Editor origine OLE DB (pagina Gestione connessione)
  Usare la pagina **Gestione connessione** della finestra di dialogo **Editor origine OLE DB** per selezionare la gestione connessione OLE DB per l'origine. Tramite questa pagina è inoltre possibile selezionare una tabella o una vista del database.  
  
> [!NOTE]  
>  Per caricare dati da un'origine dati basata su [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007, usare un'origine OLE DB. Non è possibile utilizzare un'origine Excel per caricare dati da un'origine dei dati Excel 2007. Per altre informazioni, vedere [Configura gestione connessione OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md).  
>   
>  Per caricare dati da un'origine dei dati che utilizza [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2003 o versione precedente, utilizzare un'origine Excel. Per altre informazioni, vedere [Editor origine Excel &#40;pagina Gestione connessione&#41;](../../integration-services/data-flow/excel-source-editor-connection-manager-page.md).  
  
> [!NOTE]  
>  La proprietà **CommandTimeout** dell'origine OLE DB non è disponibile nell'**Editor origine OLE DB**, tuttavia può essere impostata usando l'**Editor avanzato**. Per ulteriori informazioni su questa proprietà, vedere la sezione relativa all'origine Excel in [Proprietà personalizzate OLE DB](../../integration-services/data-flow/ole-db-custom-properties.md).  
  
 Per ulteriori informazioni sull'origine OLE DB, vedere [OLE DB Source](../../integration-services/data-flow/ole-db-source.md).  
  
## Aprire OLE DB Source Editor (pagina Gestione connessione)  
  
1.  Aggiungere l'origine OLE DB al pacchetto [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sul componente di origine, quindi scegliere **Modifica**.  
  
3.  Fare clic su **Gestione connessione**.  
  
## Opzioni statiche  
 **gestione connessione OLE DB**  
 Selezionare una gestione connessione esistente nell'elenco o crearne una nuova facendo clic su **Nuova**.  
  
 **Nuova**  
 Consente di creare una nuova gestione connessione usando la finestra di dialogo **Configura gestione connessione OLE DB**.  
  
 **Modalità di accesso ai dati**  
 Consente di specificare il metodo per la selezione dei dati dall'origine.  
  
|Opzione|Description|  
|------------|-----------------|  
|Tabella o vista|Consente di recuperare dati da una tabella o da una vista nell'origine dei dati OLE DB.|  
|Variabile nome vista o nome tabella|Consente di specificare il nome della vista o della tabella in una variabile.<br /><br /> **Informazioni correlate:** [Utilizzo di variabili nei pacchetti](../Topic/Use%20Variables%20in%20Packages.md)|  
|Comando SQL|Consente di recuperare dati dall'origine dei dati OLE DB utilizzando una query SQL.|  
|Comando SQL da variabile|Consente di specificare il testo della query SQL in una variabile.|  
  
 **Anteprima**  
 Consente di visualizzare in anteprima i risultati nella finestra di dialogo **Vista dati**. L'**anteprima** supporta la visualizzazione di un massimo di 200 righe.  
  
> [!NOTE]  
>  Quando vengono visualizzati i dati in anteprima, le colonne con tipo definito dall'utente CLR (UDT) non contengono dati. Vengono invece visualizzati i valori \<dimensione valore eccessiva per la visualizzazione> o System.Byte[]. Il primo viene visualizzato se si accede all'origine dati mediante il provider SQL OLE DB, il secondo se si usa il provider [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## Opzioni dinamiche relative alla modalità di accesso ai dati  
  
### Modalità di accesso ai dati = Tabella o vista  
 **Nome tabella o vista**  
 Consente di selezionare il nome della tabella o della vista nell'elenco dei nomi disponibili nell'origine dei dati.  
  
### Modalità di accesso ai dati = Variabile nome vista o nome tabella  
 **Nome variabile**  
 Consente di selezionare la variabile che contiene il nome della tabella o vista.  
  
### Modalità di accesso ai dati = Comando SQL  
 **Testo comando SQL**  
 Immettere il testo di una query SQL, fare clic su **Compila query** per compilare la query o fare clic su **Sfoglia** per individuare il file che contiene il testo della query.  
  
 **Parametri**  
 Se è stata immessa una query con parametri utilizzando ? come segnaposto per il parametro nel testo della query, usare la finestra di dialogo **Imposta parametri query** per eseguire il mapping tra i parametri di input della query e le variabili del pacchetto.  
  
 **Compila query**  
 Usare la finestra di dialogo **Generatore query** per creare la query SQL con strumenti grafici.  
  
 **Sfoglia**  
 Usare la finestra di dialogo **Apri** per individuare il file contenente il testo della query SQL.  
  
 **Analizza query**  
 Consente di verificare la sintassi del testo della query.  
  
### Modalità di accesso ai dati = Comando SQL da variabile  
 **Nome variabile**  
 Consente di selezionare la variabile contenente il testo della query SQL.  
  
## Vedere anche  
 [Guida di riferimento ai messaggi e agli errori di Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Editor origine OLE DB &#40;pagina Colonne&#41;](../../integration-services/data-flow/ole-db-source-editor-columns-page.md)   
 [Editor origine OLE DB &#40;pagina Output degli errori&#41;](../../integration-services/data-flow/ole-db-source-editor-error-output-page.md)   
 [Estrazione dei dati tramite l'origine OLE DB](../../integration-services/data-flow/extract-data-by-using-the-ole-db-source.md)   
 [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  