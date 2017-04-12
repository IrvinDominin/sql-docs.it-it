---
title: "Connessione a un file dBASE o a un altro file DBF | Microsoft Docs"
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
  - "connessione a file DBF"
  - "file dBase"
  - "DBF, file"
ms.assetid: b0e8c831-9f96-475c-82a4-4f5b02692752
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Connessione a un file dBASE o a un altro file DBF
  È possibile connettersi a un file dBASE o un altro file di database con estensione dbf in un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] utilizzando una gestione connessione OLE DB e selezionando il provider Microsoft OLE DB per Jet 4.0.  
  
> [!NOTE]  
>  l'Importazione/Esportazione guidata SQL Server disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta l'importazione da o l'esportazione in file dBASE o altri file DBF. È possibile utilizzare Microsoft Access o Microsoft Excel per importare i dati dai file DBF in un database di Access o in fogli di calcolo di Excel e quindi utilizzare l'Importazione/Esportazione guidata SQL Server.  
  
### Per configurare una gestione connessione per la connessione a un file dBASE o a un altro file DBF  
  
1.  Aggiungere una nuova gestione connessione OLE DB al pacchetto. Per altre informazioni, vedere [Add, Delete, or Share a Connection Manager in a Package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
2.  Nella pagina **Connessione** della finestra di dialogo **Gestione connessione** selezionare il provider OLE DB nativo o il provider OLE DB Microsoft Jet 4.0 come **Provider**.  
  
3.  Quando si utilizzano i file DBF, la cartella rappresenta il database e i singoli file DBF rappresentano le tabelle. La casella di testo **Nome file di database** deve pertanto contenere il percorso della cartella in cui si trova il file DBF e non deve includere il nome di file. È possibile digitare o incollare il percorso della cartella oppure usare il pulsante **Sfoglia** per selezionare il file DBF e quindi rimuovere il nome di file dalla parte finale del percorso.  
  
4.  Nella pagina **Tutte** della finestra di dialogo **Gestione connessione** immettere **dBASE III**, **dBASE IV** o **dBASE 5.0**, in base a quanto necessario, come valore delle proprietà estese.  
  
5.  Fare clic su **Test connessione** per convalidare i valori immessi. Verrà visualizzato il messaggio "Test della connessione riuscito". Fare clic su **OK** per chiudere la finestra di messaggio.  
  
6.  Fare clic su **OK** per salvare la configurazione per la gestione connessione.  
  
7.  Per utilizzare la gestione connessione nel flusso di dati del pacchetto, selezionare un'origine o una destinazione OLE DB e configurarla per l'utilizzo della gestione connessione creata tramite la procedura precedente.  
  
## Vedere anche  
 [Gestione connessione OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md)  
  
  