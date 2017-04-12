---
title: "Impostazione delle propriet&#224; di un pacchetto | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di Integration Services, proprietà"
  - "proprietà [Integration Services]"
  - "checkpoint [Integration Services]"
  - "proprietà di esecuzione [Integration Services]"
  - "pacchetti [Integration Services], proprietà"
  - "proprietà di identificazione [Integration Services]"
  - "password [Integration Services]"
  - "pacchetti SSIS, proprietà"
  - "proprietà relative alle transazioni [Integration Services]"
  - "aggiornamento di proprietà dei pacchetti"
  - "proprietà del valore di esecuzione forzato [Integration Services]"
  - "proprietà di sicurezza [Integration Services]"
  - "proprietà di versione [Integration Services]"
  - "pacchetti di SQL Server Integration Services, proprietà"
ms.assetid: 13f81c3e-2b18-4f83-b445-a2f4a2c560aa
caps.latest.revision: 40
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 39
---
# Impostazione delle propriet&#224; di un pacchetto
  Quando viene creato un pacchetto in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] utilizzando l'interfaccia grafica offerta da [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , è possibile impostare le proprietà dell'oggetto pacchetto nella finestra Proprietà.  
  
 In tale finestra **** le proprietà possono essere elencate per categorie o in ordine alfabetico. Per elencare gli elementi della finestra **Proprietà** per categoria, fare clic sull'icona Per categoria.  
  
 Quando si utilizza questa modalità, le proprietà visualizzate nella finestra **Proprietà** vengono raggruppate nelle categorie seguenti:  
  
-   [Checkpoint](#Checkpoints)  
  
-   [Esecuzione](#Execution)  
  
-   [Valore esecuzione forzato](#ForcedExecutionValue)  
  
-   [Identificazione](#Identification)  
  
-   [Varie](#Misc)  
  
-   [Sicurezza](#Security)  
  
-   [Transazioni](#Transactions)  
  
-   [Version](#Version)  
  
 Per informazioni sulle proprietà aggiuntive di un pacchetto che non è possibile impostare nella finestra **Proprietà**, vedere <xref:Microsoft.SqlServer.Dts.Runtime.Package>.  
  
### Per impostare le proprietà di un pacchetto nella finestra Proprietà  
  
-   [Impostazione delle proprietà di un pacchetto](../Topic/Set%20the%20Properties%20of%20a%20Package.md)  
  
## Proprietà per categoria  
 Nelle tabelle seguenti vengono elencate le proprietà di un pacchetto in base alla categoria.  
  
###  <a name="Checkpoints"></a> Checkpoint  
 È possibile utilizzare le proprietà in questa categoria per riavviare il pacchetto da un punto problematico nel flusso di controllo, anziché rieseguire il pacchetto dall'inizio del flusso di controllo. Per ulteriori informazioni, vedere [Restart Packages by Using Checkpoints](../integration-services/packages/restart-packages-by-using-checkpoints.md).  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**CheckpointFileName**|Nome del file in cui vengono acquisite le informazioni di checkpoint che consentono il riavvio del pacchetto. Se l'esecuzione del pacchetto viene completata correttamente, questo file verrà eliminato.|  
|**CheckpointUsage**|Specifica quando è possibile riavviare il pacchetto. I possibili valori sono **Never**, **IfExists**e **Always**. Il valore predefinito della proprietà è **Never**, che indica che il pacchetto non può essere riavviato. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSCheckpointUsage>.|  
|**SaveCheckpoints**|Specifica se i checkpoint vengono scritti nel file del checkpoint durante l'esecuzione del pacchetto. Il valore predefinito di questa proprietà è **False**.|  
  
> [!NOTE]  
>  L'opzione **/CheckPointing on** di dtexec equivale a impostare la proprietà **SaveCheckpoints** del pacchetto su True e la proprietà **CheckpointUsage** su Always. Per altre informazioni, vedere [dtexec Utility](../integration-services/packages/dtexec-utility.md).  
  
###  <a name="Execution"></a> Esecuzione  
 Le proprietà di questa categoria consentono di configurare il comportamento in fase di esecuzione dell'oggetto di pacchetto.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**DelayValidation**|Indica se la convalida del pacchetto viene posticipata fino all'esecuzione del pacchetto. Il valore predefinito di questa proprietà è **False**.|  
|**Disable**|Indica se il pacchetto è disabilitato. Il valore predefinito di questa proprietà è **False**.|  
|**DisableEventHandlers**|Specifica se i gestori di eventi del pacchetto vengono eseguiti. Il valore predefinito di questa proprietà è **False**.|  
|**FailPackageOnFailure**|Indica se il pacchetto deve essere interrotto in caso di errore in uno dei suoi componenti. L'unico valore valido di questa proprietà è **False**.|  
|**FailParentOnError**|Indica se il contenitore padre deve essere interrotto in caso di errore in uno dei contenitori figli. Il valore predefinito della proprietà è **False**.|  
|**MaxConcurrentExecutables**|Numero di file eseguibili che il pacchetto è in grado di eseguire contemporaneamente. Il valore predefinito della proprietà è **-1**, che indica l'assenza di limiti.|  
|**MaximumErrorCount**|Numero massimo di errori che si possono verificare prima che l'esecuzione del pacchetto venga arrestata. Il valore predefinito di questa proprietà è **1**.|  
|**PackagePriorityClass**|Classe di priorità del thread Win32 del pacchetto. I possibili valori sono **Default**, **AboveNormal**, **Normal**, **BelowNormal**e **Idle**. Il valore predefinito di questa proprietà è **Default**. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSPriorityClass>.|  
  
###  <a name="ForcedExecutionValue"></a> Valore esecuzione forzato  
 Le proprietà di questa categoria consentono di configurare un valore di esecuzione facoltativo per il pacchetto.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**ForcedExecutionValue**|Se la proprietà ForceExecutionValue è impostata su **True**, rappresenta il valore che specifica il valore di esecuzione facoltativo restituito dal pacchetto. Il valore predefinito di questa proprietà è **0**.|  
|**ForcedExecutionValueType**|Il tipo di dati di ForcedExecutionValue. Il valore predefinito di questa proprietà è **Int32**.|  
|**ForceExecutionValue**|Valore booleano che specifica se il valore di esecuzione facoltativo del contenitore deve essere forzato in modo da contenere un valore specifico. Il valore predefinito di questa proprietà è **False**.|  
  
###  <a name="Identification"></a> Identificazione  
 Le proprietà di questa categoria forniscono informazioni quali l'identificatore univoco e il nome del pacchetto.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**CreationDate**|Data di creazione del pacchetto.|  
|**CreatorComputerName**|Nome del computer in cui è stato creato il pacchetto.|  
|**CreatorName**|Nome dell'utente che ha creato il pacchetto.|  
|**Description**|Descrizione delle funzionalità del pacchetto.|  
|**ID**|GUID del pacchetto, assegnato al momento della creazione. Questa proprietà è di sola lettura. Per generare un nuovo valore casuale per la proprietà **ID**, selezionare **\<Genera nuovo ID>** nell'elenco a discesa.|  
|**Nome**|Nome del pacchetto.|  
|**PackageType**|Tipo di pacchetto. I possibili valori sono **Default**, **DTSDesigner**, **DTSDesigner100**, **DTSWizard**, **SQLDBMaint**e **SQLReplication**. Il valore predefinito di questa proprietà è **Default**. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType>.|  
  
###  <a name="Misc"></a> Varie  
 Le proprietà di questa categoria vengono utilizzate per l'accesso alle configurazioni e alle espressioni utilizzate dal pacchetto e per fornire informazioni sulle impostazioni locali e sulla modalità di registrazione del pacchetto. Per altre informazioni, vedere [Utilizzo delle espressioni di proprietà nei pacchetti](../integration-services/expressions/use-property-expressions-in-packages.md).  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**Configurazioni**|Raccolta delle configurazioni utilizzate dal pacchetto. Per visualizzare e configurare le configurazioni del pacchetto, fare clic sul pulsante Sfoglia **(…)**.|  
|**Espressioni**|Per creare espressioni per le proprietà del pacchetto, fare clic sul pulsante Sfoglia **(…)**.<br /><br /> È possibile creare espressioni di proprietà per tutte le proprietà del pacchetto incluse nel modello a oggetti, non solo per quelle elencate nella finestra Proprietà.<br /><br /> Per altre informazioni, vedere [Utilizzo delle espressioni di proprietà nei pacchetti](../integration-services/expressions/use-property-expressions-in-packages.md).<br /><br /> Per visualizzare le espressioni di proprietà esistenti, espandere **Expressions**. Per modificare e valutare un'espressione, fare clic sul pulsante Sfoglia **(…)** nella casella di testo dell'espressione.|  
|**ForceExecutionResult**|Risultato dell'esecuzione del pacchetto. I valori sono **None**, **Success**, **Failure**e **Completion**. Il valore predefinito di questa proprietà è **None**. Per altre informazioni, vedere T:Microsoft.SqlServer.Dts.Runtime.DTSForcedExecResult.|  
|**LocaleId**|Impostazioni locali Microsoft Win32. Il valore predefinito di questa proprietà è costituito dalle impostazioni locali del sistema operativo sul computer locale.|  
|**LoggingMode**|Valore che specifica il comportamento di registrazione del pacchetto. I possibili valori sono **Disabled**, **Enabled**e **UseParentSetting**. Il valore predefinito di questa proprietà è **UseParentSetting**. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.|  
|**OfflineMode**|Indica se il pacchetto è in modalità offline. Questa proprietà è di sola lettura. e viene impostata a livello di progetto. In genere, Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] tenta di connettersi a ogni origine dei dati utilizzata dal pacchetto per convalidare i metadati associati alle origini e alle destinazioni. È possibile attivare l'opzione **Offline** dal menu **SSIS** anche prima di aprire un pacchetto, per impedire questi tentativi di connessione e gli errori di convalida risultanti quando le origini dei dati non sono disponibili. È anche possibile abilitare l'opzione **Offline** per rendere più veloci le operazioni di progettazione e disabilitarla solo quando si vuole convalidare il pacchetto.|  
|**SuppressConfigurationWarnings**|Indica se gli avvisi generati dalle configurazioni vengono soppressi. Il valore predefinito di questa proprietà è **False**.|  
|**UpdateObjects**|Indica se il pacchetto viene aggiornato in modo da utilizzare le versioni più recenti, se disponibili, degli oggetti che contiene. Se ad esempio la proprietà è impostata su **True**, un pacchetto che include un'attività Inserimento bulk viene aggiornato in modo da usare la versione più recente dell'attività Inserimento bulk disponibile in [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Il valore predefinito di questa proprietà è **False**.|  
  
###  <a name="Security"></a> Sicurezza  
 Le proprietà di questa categoria consentono di impostare il livello di protezione del pacchetto. Per altre informazioni, vedere [Access Control for Sensitive Data in Packages](../integration-services/packages/access-control-for-sensitive-data-in-packages.md).  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**PackagePassword**|Password per i livelli di protezione del pacchetto che richiedono una password (**EncryptSensitiveWithPassword** e **EncryptAllWithPassword**).|  
|**ProtectionLevel**|Livello di protezione del pacchetto. I possibili valori sono **DontSaveSensitive**, **EncryptSensitiveWithUserKey**, **EncryptSensitiveWithPassword**, **EncryptAllWithPassword**e **ServerStorage**. Il valore predefinito di questa proprietà è **EncryptSensitiveWithUserKey**. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSProtectionLevel>.|  
  
###  <a name="Transactions"></a> Transazioni  
 Le proprietà di questa categoria consentono di configurare il livello di isolamento e l'opzione relativa alle transazioni per il pacchetto. Per altre informazioni, vedere [Transazioni di Integration Services](../integration-services/integration-services-transactions.md).  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**IsolationLevel**|Livello di isolamento della transazione del pacchetto. I valori sono **Unspecified**, **Chaos**, **ReadUncommitted**, **ReadCommitted**, **RepeatableRead**, **Serializable** e **Snapshot**. Il valore predefinito di questa proprietà è **Serializable**.<br /><br /> Nota: il valore **Snapshot** della proprietà **IsolationLevel** non è compatibile con le transazioni del pacchetto e quindi non è possibile utilizzare la proprietà **IsolationLevel** per impostare il livello di isolamento delle transazioni del pacchetto su **Shapshot**. È necessario invece eseguire una query SQL per impostare le transazioni del pacchetto su **Snapshot**. Per altre informazioni, vedere [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](../t-sql/statements/set-transaction-isolation-level-transact-sql.md).<br /><br /> La proprietà **IsolationLevel** viene applicata automaticamente alle transazioni del pacchetto solo quando il valore della proprietà **TransactionOption** è **Required**.<br /><br /> Il valore della proprietà **IsolationLevel** richiesta da un contenitore figlio viene ignorato quando le condizioni seguenti sono vere:<br />Il valore della proprietà **TransactionOption** del contenitore figlio è **Supported**.<br />Il contenitore figlio partecipa alla transazione di un contenitore padre.<br /><br /> Il valore della proprietà **IsolationLevel** richiesta dal contenitore viene rispettato solo quando il contenitore avvia una nuova transazione. Un contenitore avvia una nuova transazione quando le condizioni seguenti sono vere:<br />Il valore della proprietà **TransactionOption** del contenitore è **Required**.<br />Non è stata ancora avviata alcuna transazione da parte del padre.<br /><br /> <br /><br /> Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.|  
|**TransactionOption**|Supporto delle transazioni da parte del pacchetto. I possibili valori sono **NotSupported**, **Supported**e **Required**. Il valore predefinito di questa proprietà è **Supported**. Per altre informazioni, vedere <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.|  
  
###  <a name="Version"></a> Version  
 Le proprietà di questa categoria forniscono informazioni sulla versione dell'oggetto di pacchetto.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|**VersionBuild**|Numero di build del pacchetto.|  
|**VersionComments**|Commenti sulla versione del pacchetto.|  
|**VersionGUID**|GUID della versione del pacchetto. Questa proprietà è di sola lettura.|  
|**VersionMajor**|Versione principale più recente del pacchetto.|  
|**VersionMinor**|Versione secondaria più recente del pacchetto.|  
  
  