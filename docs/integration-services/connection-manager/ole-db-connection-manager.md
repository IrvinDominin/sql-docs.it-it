---
title: "Gestione connessione OLE DB | Microsoft Docs"
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
  - "gestione connessione OLE DB"
  - "origini dati [Integration Services], connessioni"
  - "gestioni connessioni [Integration Services], OLE DB"
  - "connessioni [Integration Services], OLE DB"
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
caps.latest.revision: 59
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 59
---
# Gestione connessione OLE DB
  Una gestione connessione OLE DB consente la connessione di un pacchetto a un'origine dati tramite un provider OLE DB. In una gestione connessione OLE DB tramite che si connette a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio, è possibile usare il provider [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].    
    
> [!NOTE]    
>  Il provider OLE DB di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 non supporta le nuove parole chiave per le stringhe di connessione (MultiSubnetFailover=True) per il clustering di failover su più subnet. Per altre informazioni, vedere le [note sulla versione di SQL Server](http://go.microsoft.com/fwlink/?LinkId=247824) e il post di blog [Always On Multi-Subnet Failover and SSIS](http://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/) (Failover su più subnet Always On e SSIS) nel sito www.mattmasson.com.    
    
> [!NOTE]    
>  Se l'origine dati è [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Excel 2007 o [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access 2007, è richiesto un provider di dati diverso rispetto alle versioni precedenti di Excel o Access. Per altre informazioni, vedere [Connettersi a una cartella di lavoro di Excel](../../integration-services/connection-manager/connect-to-an-excel-workbook.md) e [Connettersi a un database di Access](../../integration-services/connection-manager/connect-to-an-access-database.md).    
    
 La gestione connessione OLE DB viene usata da diversi componenti di flusso di dati e attività di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. L'origine e la destinazione OLE DB, ad esempio, usano questa gestione connessione per estrarre e caricare i dati, mentre l'attività Esegui SQL può usarla per connettersi a un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'esecuzione delle query.    
    
 La gestione connessione OLE DB viene inoltre utilizzata per accedere alle origini dei dati OLE DB nelle attività personalizzate scritte in codice non gestito che utilizza un linguaggio quale C++.    
    
 Quando si aggiunge una gestione connessione OLE DB a un pacchetto, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crea una gestione connessione che in fase di esecuzione verrà risolta in una connessione OLE DB, imposta le proprietà di tale gestione connessione e quindi la aggiunge alla raccolta **Connessioni** del pacchetto.    
    
 La proprietà **ConnectionManagerType** della gestione connessione viene impostata su **OLEDB**.    
    
 Per configurare la gestione connessione OLE DB, procedere nel modo seguente:    
    
-   Specificare una stringa di connessione configurata in modo da soddisfare i requisiti del provider selezionato.    
    
-   Se richiesto dal provider, includere il nome dell'origine dei dati a cui connettersi.    
    
-   Specificare le credenziali di sicurezza come previsto dal provider selezionato.    
    
-   Indicare se la connessione creata dalla gestione connessione deve essere mantenuta in fase di esecuzione.    
    
## Registrazione    
 È possibile registrare le chiamate eseguite dalla gestione connessione OLE DB a provider di dati esterni. Questa nuova funzionalità di registrazione può essere utilizzata per risolvere i problemi relativi alle connessioni stabilite dalla gestione connessione OLE DB a origini dati esterne. Per registrare le chiamate eseguite dalla gestione connessione OLE DB a provider di dati esterni, abilitare la registrazione dei pacchetti e selezionare l'evento **Diagnostic** a livello di pacchetto. Per altre informazioni, vedere [Strumenti per la risoluzione dei problemi relativi all'esecuzione dei pacchetti](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md).    
    
## Configurazione della gestione connessione OLEDB    
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice. Per altre informazioni sulle proprietà che è possibile impostare in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)], vedere [Configura gestione connessione OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md). Per informazioni sulla configurazione di una gestione connessione a livello di programmazione, vedere la documentazione per la classe **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** nella Guida per gli sviluppatori.    
    
## Contenuto correlato    
    
-   Articolo di Wiki [SSIS with Oracle Connectors](http://go.microsoft.com/fwlink/?LinkId=220670) (Connettori SSIS con Oracle) nel sito Web social.technet.microsoft.com.    
    
-   Articolo tecnico [Connection Strings for OLE DB Providers](http://go.microsoft.com/fwlink/?LinkId=220744) (Stringhe di connessione per i provider OLE DB) nel sito Web carlprothman.net.    
    
## Vedere anche    
 [Origine OLE DB](../../integration-services/data-flow/ole-db-source.md)     
 [Destinazione OLE DB](../../integration-services/data-flow/ole-db-destination.md)     
 [Attività Esegui SQL](../../integration-services/control-flow/execute-sql-task.md)     
 [Connessioni in Integration Services &#40;SSIS&#41;](../../integration-services/connection-manager/integration-services-ssis-connections.md)    
    
  