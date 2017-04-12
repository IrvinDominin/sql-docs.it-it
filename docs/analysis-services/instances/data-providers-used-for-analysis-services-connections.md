---
title: "Provider di dati utilizzati per le connessioni ad Analysis Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128f6dde-409d-4c12-9820-3305bab57b75
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 18
---
# Provider di dati utilizzati per le connessioni ad Analysis Services
  Analysis Services fornisce tre provider di dati per l'accesso al server e ai dati. Tutte le applicazioni che si connettono ad Analysis Services effettuano l'accesso mediante una di tali provider. Due provider, ADOMD.NET e Analysis Services Management Objects (AMO), sono provider di dati gestiti, mentre il provider OLE DB di Analysis Services (MSOLAP DLL) è un provider di dati nativo.  
  
 Nelle organizzazioni in cui vengono eseguite più versioni di Analysis Services potrebbe essere necessario installare versioni più recenti dei provider di dati nelle workstation degli utenti che si connettono ai dati di Analysis Services. Le connessioni a versioni più recenti di Analysis Services richiedono provider di dati della stessa versione principale. Per accedere a [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)], ad esempio, in ogni workstation deve essere presente un provider di dati della stessa versione. Sebbene con Excel vengano installati provider di dati a cui è necessario connettersi, il provider fornito spesso non è aggiornato rispetto alle istanze di Analysis Services in uso.  
  
 In questo argomento è contenuta la sezione seguente:  
  
 [Come determinare la versione del server](#bkmk_ServVers)  
  
 [Come determinare la versione dei provider di dati di Analysis Services](#bkmk_LibUpdate)  
  
 [Dove trovare li provider di dati con la versione più recente](#bkmk_downloadsite)  
  
 [Provider OLE DB per Analysis Services](#bkmk_OLE)  
  
 [ADOMD.NET](#bkmk_ADOMD)  
  
 [AMO](#blkmk_AMO)  
  
##  <a name="bkmk_ServVers"></a> Come determinare la versione del server  
 Se si conosce la versione dell'istanza di Analysis Services, sarà possibile determinare se è necessario installare versioni più recenti dei provider di dati nelle workstation dell'organizzazione.  
  
-   In SQL Server Management Studio connettersi all'istanza di Analysis Services. È possibile visualizzare la versione in **Proprietà server** > **Generale** > **Versione**.  
  
 Il numero della build principale della versione iniziale di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] è 13.0.1601.5.  
  
  
##  <a name="bkmk_LibUpdate"></a> Come determinare la versione dei provider di dati di Analysis Services  
 I provider di dati vengono installati con Analysis Services e con le applicazioni client che si connettono normalmente ai database di Analysis Services, ad esempio Excel.  
  
 Office 2010 installa i provider di dati da SQL Server 2008. Office 2013 installa i provider di dati da SQL Server 2012 e versioni successive. Se si utilizzano più versioni di Office o di SQL Server e le connessioni e funzionalità disponibili non sono quelle previste, potrebbe essere necessario installare una versione più recente dei provider di dati. È possibile eseguire più versioni principali di ogni provider di dati side-by-side sullo stesso computer.  
  
#### Individuazione della versione del file del provider OLEDB  
  
1.  Passare a \Programmi\Microsoft Analysis Services\AS OLEDB\130.  
  
2.  Fare clic con il pulsante destro del mouse su **msolap130.dll** > **Proprietà** > **Dettagli**.  
  
 Se il file non è presente in questo percorso o se il percorso della cartella include AS OLEDB\110 o AS OLEDB\90, la libreria in uso è obsoleta ed è necessario installare una versione più recente (AS OLEDB\11) per connettersi a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
#### Individuazione della versione di ADOMD.NET e AMO  
  
1.  Passare a C:\Windows\Assembly  
  
2.  Fare clic con il pulsante destro del mouse su Microsoft.AnalysisServices.AdomdClient e scegliere **Proprietà**. Fare clic su **Versione**.  
  
     Per AMO, fare clic con il pulsante destro del mouse su Microsoft.AnalysisServices.  
  
##  <a name="bkmk_downloadsite"></a> Dove trovare li provider di dati con la versione più recente  
 La versione installata nel computer client deve corrispondere alla versione principale del server che fornisce i dati. Se l'installazione del server è più recente dei provider di dati installati nelle workstation in rete, potrebbe essere necessario installare librerie più recenti.  
  
#### Individuare i provider di dati nel sito di download  
  
1.  Passare all' [Area download Microsoft](http://go.microsoft.com/fwlink/p/?LinkID=296473).  
  
2.  Espandere **Istruzioni di installazione**. ADOMD.NET, il provider OLE DB e AMO sono inclusi nell'elenco. Ogni libreria è disponibile nelle versioni a 32 o 64 bit. I server e le workstation più recenti che eseguono un sistema operativo a 64 bit richiedono la versione a 64 bit.  
  
##  <a name="bkmk_OLE"></a> Provider OLE DB per Analysis Services  
 Il provider OLE DB per Analysis Services è il provider nativo per le connessioni di database Analysis Services. MSOLAP viene utilizzato indirettamente da ADOMD.NET e AMO, delegando le richieste di connessione al provider di dati. È inoltre possibile chiamare il provider OLE DB direttamente dal codice dell'applicazione, il che è possibile se i requisiti della soluzione precludono l'utilizzo di un'API gestita.  
  
 Il provider OLE DB per Analysis Services viene installato automaticamente dal programma di installazione di SQL Server, Excel e altre applicazioni utilizzate con frequenza per accedere ai database di Analysis Services. Può essere installato anche manualmente scaricandolo dall'Area download. Per impostazione predefinita, il provider è contenuto nella cartella \Programmi\Microsoft Analysis Services. Il provider deve essere installato su qualsiasi workstation utilizzata per accedere ai dati di Analysis Services.  
  
 MSOLAP130.dll è la versione del provider OLE DB per Analysis Services fornita con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Altre versioni precedenti recenti includono MSOLAP110.dll (per SQL Server 2008 e 2008 R2) e MSOLAP90.dll (per SQL Server 2005).  
  
 I provider OLE DB vengono spesso specificati nelle stringhe di connessione. Una stringa di connessione di Analysis Services usa una nomenclatura diversa per fare riferimento al provider OLE DB: MSOLAP.\<versione>.dll  
  
 MSOLAP.5.dll è il provider OLE DB per Analysis Services corrente installato con Excel 2013. Le versioni precedenti, ad esempio MSOLAP.4.dll o MSOLAP.3.dll, sono spesso disponibili nelle workstation che eseguono versioni meno recenti di Excel. Alcune funzionalità di Analysis Services, ad esempio il componente aggiuntivo [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], richiedono versioni specifiche del provider OLE DB. Per altre informazioni, vedere [Proprietà delle stringhe di connessione &#40;Analysis Services&#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
##  <a name="bkmk_ADOMD"></a> ADOMD.NET  
 ADOMD.NET è un provider di dati gestito utilizzata per eseguire query sui dati di Analysis Services. Excel utilizza ADOMD.NET per la connessione a un cubo di Analysis Services specifico. La stringa di connessione indicata in Excel è destinata a una connessione ADOMD.NET.  
  
 ADOMD.NET viene installato dal programma di installazione di SQL Server ed è utilizzato dalle applicazioni client SQL Server per la connessione ad Analysis Services. In Office questa libreria viene installata per supportare le connessioni dati da Excel. Come con altri provider di dati inclusi in SQL Server, è possibile ridistribuire ADOMD.NET se si utilizza la libreria nel codice personalizzato. È anche possibile scaricarlo e installarlo manualmente per ottenere la versione più recente. A questo proposito, vedere [Come determinare la versione dei provider di dati di Analysis Services](#bkmk_LibUpdate) in questo argomento.  
  
 Per controllare le informazioni sulla versione dei file, cercare ADOMD.NET nella Global Assembly Cache, dove è elencato come `Microsoft.AnalysisServices.AdomdClient`.  
  
 Quando ci si connette a un database, le proprietà della stringa di connessione per tutte e tre le librerie sono in gran parte corrispondenti. Quasi tutte le stringhe di connessione definite per ADOMD.NET (<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>) funzioneranno anche per AMO e per il provider OLE DB per Analysis Services. Per altre informazioni, vedere [Proprietà delle stringhe di connessione &#40;Analysis Services&#41;](../../analysis-services/instances/connection-string-properties-analysis-services.md).  
  
 Per ulteriori informazioni sulla connessione a livello di programmazione, vedere [Establishing Connections in ADOMD.NET](../Topic/Establishing%20Connections%20in%20ADOMD.NET.md).  
  
##  <a name="blkmk_AMO"></a> AMO  
 AMO è un provider di dati gestito utilizzato per l'amministrazione del server e la definizione dei dati. Ad esempio, in SQL Server Management Studio si utilizza AMO per connettersi ad Analysis Services.  
  
 AMO viene installato dal programma di installazione di SQL Server ed è utilizzato dalle applicazioni client SQL Server per la connessione ad Analysis Services. È anche possibile scaricarlo e installarlo manualmente quando si usa AMO nel codice personalizzato. A questo proposito, vedere [Come determinare la versione dei provider di dati di Analysis Services](#bkmk_LibUpdate) in questo argomento. AMO può essere presente nella Global Assembly Cache, come `Microsoft.AnalysisServices`.  
  
 Una connessione tramite AMO è in genere minima in quando costituita da “data source=\<servername>”. Dopo aver stabilito una connessione, utilizzare l'API per utilizzare le raccolte e gli oggetti principali del database. Sia SSDT che SSMS utilizzano AMO per connettersi a un'istanza di Analysis Services.  
  
 Per ulteriori informazioni sulla connessione a livello di programmazione, vedere [Programming AMO Fundamental Objects](../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md).  
  
## Vedere anche  
 [Connetti ad Analysis Services](../../analysis-services/instances/connect-to-analysis-services.md)  
  
  