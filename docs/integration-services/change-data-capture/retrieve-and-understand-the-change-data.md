---
title: "Recupero e comprensione dei dati delle modifiche | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "caricamento incrementale [Integration Services], recupero di dati"
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# Recupero e comprensione dei dati delle modifiche
  La prima attività nel flusso di dati di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] che esegue un caricamento incrementale dei dati delle modifiche consiste nell'eseguire la query per il recupero dei dati delle modifiche. Questa query deve essere eseguita all'interno di un componente di origine in un'attività Flusso di dati. È quindi possibile utilizzare trasformazioni a valle e destinazioni per applicare i dati delle modifiche alla destinazione.  
  
> [!NOTE]  
>  La creazione di una query contenente una funzione valutata a livello di tabella costituisce il terzo passaggio del processo di creazione di un pacchetto per l'esecuzione di un caricamento incrementale dei dati delle modifiche. Per altre informazioni su questa query, vedere, [Creazione della funzione per il recupero dei dati delle modifiche](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md). Per una descrizione del processo complessivo di creazione di un pacchetto in cui viene eseguito un caricamento incrementale dei dati delle modifiche, vedere [Change Data Capture &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## Aggiunta dell'attività Flusso di dati  
 Nel flusso di dati del pacchetto è necessario recuperare i dati delle modifiche, separare le righe in base al tipo di modifica apportata e quindi applicare le modifiche alla destinazione.  
  
#### Per aggiungere un'attività Flusso di dati al pacchetto  
  
1.  Nella scheda **Flusso di controllo** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aggiungere un'attività Flusso di dati.  
  
2.  Connettere l'attività precedente tramite cui è stata preparata la stringa di query all'attività Flusso di dati.  
  
## Configurazione del componente di origine per l'esecuzione della query per le modifiche  
 Il componente di origine utilizza la stringa di query preparata e archiviata in una variabile per chiamare la funzione valutata a livello di tabella che recupera i dati modificati.  
  
> [!NOTE]  
>  Per altre informazioni sulla stringa di query preparata e archiviata in una variabile, vedere [Preparazione dell'esecuzione di una query per i dati delle modifiche](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md). Per altre informazioni sulla funzione valutata a livello di tabella che recupera i dati delle modifiche, vedere [Creazione della funzione per il recupero dei dati delle modifiche](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
#### Per configurare un'origine OLE DB per recuperare i dati delle modifiche  
  
1.  Nella scheda **Flusso di dati** in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] aggiungere un'origine OLE DB.  
  
2.  Nella pagina **Gestione connessione** in **Editor origine OLE DB** selezionare le opzioni seguenti:  
  
    1.  Configurare una connessione valida al database di origine.  
  
    2.  Per **Modalità di accesso ai dati** selezionare **Comando SQL da variabile**.  
  
    3.  Per **Nome variabile** selezionare **User::SqlDataQuery**.  
  
3.  Nella pagina **Colonne** in **Editor origine OLE DB** verificare che su tutte le colonne desiderate sia eseguito il mapping a colonne di output.  
  
## Passaggio successivo  
 Dopo avere configurato un'origine OLE DB per recuperare i dati delle modifiche, il passaggio successivo consiste nell'iniziare a progettare il flusso di dati nel pacchetto.  
  
 **Argomento successivo:** [Elaborazione di inserimenti, aggiornamenti ed eliminazioni](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md)  
  
  