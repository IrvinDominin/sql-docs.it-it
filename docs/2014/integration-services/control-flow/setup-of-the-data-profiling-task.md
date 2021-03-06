---
title: Impostazione dell'attività Profiling dati | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- Data Profiling task [Integration Services], configuring
ms.assetid: fe050ca4-fe45-43d7-afa9-99478041f9a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 8309a4d66fbcf36aca4e5e4d817c2bb34722bc08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48072971"
---
# <a name="setup-of-the-data-profiling-task"></a>Impostazione dell'attività Profiling dati
  Prima di poter esaminare un profilo dei dati di origine, configurare ed eseguire l'attività Profiling dati. È necessario creare questa attività all'interno di un pacchetto di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Per configurare l'attività Profiling dati, utilizzare lo strumento Editor attività Profiling dati. Questo editor consente di selezionare la destinazione dell'output dei profili e i profili da calcolare. Dopo avere configurato l'attività, è necessario eseguire il pacchetto per calcolare i profili dati.  
  
## <a name="requirements-and-limitations"></a>Requisiti e limitazioni  
 L'attività Profiling dati funziona solo con i dati archiviati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'attività non può essere utilizzata con origini dati di terze parti o basate su file.  
  
 Per eseguire un pacchetto contenente l'attività Profiling dati, inoltre, è necessario utilizzare un account che disponga di autorizzazioni di lettura/scrittura per il database tempdb.  
  
## <a name="data-profiling-task-in-a-package"></a>Attività Profiling dati in un pacchetto  
 L'attività Profiling dati consente solo di configurare i profili e creare il file di output contenente i profili calcolati. Per esaminare questo file di output, è necessario utilizzare Visualizzatore profilo dati, un programma di visualizzazione autonomo. Poiché è necessario visualizzare separatamente l'output, è possibile utilizzare l'attività Profiling dati in un pacchetto che non contiene altre attività.  
  
 Non è tuttavia necessario utilizzare Profiling dati come unica attività in un pacchetto. Se si desidera eseguire l'attività Profiling dati nel flusso di lavoro o nel flusso di dati di un pacchetto più complesso, sono disponibili le opzioni seguenti:  
  
-   Per implementare la logica condizionale basata sul file di output dell'attività, nel flusso di controllo del pacchetto inserire un'attività Script dopo l'attività Profiling dati. Tale attività Script potrà essere utilizzata per eseguire query sul file di output.  
  
-   Per eseguire l'attività Profiling dati del flusso di dati in seguito al caricamento e alla trasformazione dei dati, è necessario salvare temporaneamente i dati modificati in una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . A questo punto, è possibile eseguire il profiling dei dati salvati.  
  
 Per altre informazioni, vedere [Incorporamento di un'attività Profiling dati nel flusso di lavoro del pacchetto](incorporate-a-data-profiling-task-in-package-workflow.md).  
  
## <a name="setup-of-the-task-output"></a>Impostazione dell'output dell'attività  
 Quando l'attività Profiling dati si trova in un pacchetto, è necessario configurare l'output per i profili che verranno calcolati dall'attività. Per configurare l'output per i profili, è necessario usare la pagina **Generale** dello strumento Editor attività Profiling dati. Oltre a consentire di specificare la destinazione per l'output, la pagina **Generale** offre la possibilità di eseguire un rapido profiling dei dati. Quando si seleziona **Profilo rapido**, l'attività Profiling dati esegue il profiling di una tabella o di una vista usando alcuni o tutti i profili predefiniti con le relative impostazioni predefinite.  
  
 Per altre informazioni, vedere [Editor attività Profiling dati &#40;pagina Generale&#41;](../general-page-of-integration-services-designers-options.md) e [Form profilo rapido singola tabella &#40;Attività Profiling dati&#41;](data-profiling-task.md).  
  
> [!IMPORTANT]  
>  Il file di output potrebbe contenere dati sensibili sul database e i dati inclusi nel database. Per suggerimenti su come migliorare la protezione di questo file, vedere [Accesso ai file utilizzati dai pacchetti](../access-to-files-used-by-packages.md).  
  
## <a name="selection-and-configuration-of-the-profiles-to-be-computed"></a>Selezione e configurazione dei profili da calcolare  
 Dopo avere configurato il file di output, è necessario selezionare i profili dati da calcolare. L'attività Profiling dati consente di calcolare otto profili dati diversi. Cinque di questi profili analizzano singole colonne e i tre rimanenti analizzano più colonne o relazioni tra colonne e tabelle. In una singola attività Profiling dati è possibile calcolare più profili per più colonne o combinazioni di colonne in più tabelle o viste.  
  
 Nella tabella seguente vengono descritti i report calcolati da ciascun profilo e i tipi di dati per cui il profilo è valido.  
  
|Elementi da calcolare|Valori identificati|Profilo da utilizzare|  
|----------------|-------------------------|----------------------|  
|Tutte le singole lunghezze dei valori stringa nella colonna selezionata e la percentuale di righe della tabella rappresentata da ogni lunghezza.|**Valori stringa non validi**: si analizza, ad esempio, una colonna che dovrebbe usare due caratteri per i codici di stato negli Stati Uniti, ma in cui si individua la presenza di valori più lunghi di due caratteri.|**Distribuzione lunghezze di colonna, ovvero**valido per una colonna con uno di questi tipi di dati:<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`|  
|Set di espressioni regolari relative alla percentuale specificata di valori in una colonna stringa.<br /><br /> Inoltre, espressioni regolari da utilizzare in futuro per convalidare nuovi valori.|**Valori stringa non validi o in formato non corretto**: un profilo di criteri di ricerca di una colonna Codice postale, ad esempio, potrebbe produrre le espressioni regolari \d{5}-\d{4}, \d{5} e \d{9}. Se l'output contiene altre espressioni regolari, i dati contengono valori non validi o in formato non corretto.|**Profilo criteri di ricerca colonna, ovvero**valido per una colonna con uno di questi tipi di dati:<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`|  
|Percentuale di valori Null nella colonna selezionata.|**Rapporto inaspettatamente elevato di valori Null in una colonna**: si analizza, ad esempio, una colonna che dovrebbe contenere i codici postali ZIP (Stati Uniti) ma si individua una percentuale troppo elevata di codici postali mancanti.|**Colonna rapporto di valori Null, ovvero**valido per una colonna con questi tipi di dati:<br /><br /> Qualsiasi tipo di dati, inclusi i tipi `image`, `text`, `xml`, variant e i tipi definiti dall'utente.|  
|Statistiche, ad esempio sulla deviazione minima, massima, media e standard per le colonne numeriche e sulla deviazione minima e massima per le colonne di tipo `datetime`.|**Valori numerici e date non validi**: si analizza, ad esempio, una colonna di date storiche, ma si individua una data massima successiva a quella corrente.|**Profilo statistiche di colonna, ovvero**valido per una colonna con uno di questi tipi di dati:<br /><br /> Tipi di dati numerici: tipi integer, ad eccezione di `bit`, `money`, `smallmoney`, `decimal`, `float`, `real` e `numeric`<br /><br /> Tipi di dati di data e ora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` e `datetimeoffset`.<br />Nota: per una colonna con un tipo di dati di data e ora, il profilo calcola esclusivamente il minimo e il massimo.|  
|Tutti i valori distinct nella colonna selezionata e percentuale di righe della tabella rappresentata da ciascun valore. In alternativa, valori che rappresentano più di una percentuale specificata nella tabella.|**Numero non corretto di valori distinct in un colonna**: si analizza, ad esempio, una colonna contenente gli stati degli Stati Uniti ma si individuano più di 50 valori distinct.|**Distribuzione valori di colonna, ovvero**valido per una colonna con uno di questi tipi di dati:<br /><br /> Tipi di dati numerici: tipi integer, ad eccezione di `bit`, `money`, `smallmoney`, `decimal`, `float`, `real` e `numeric`<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`<br /><br /> Tipi di dati di data e ora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` e `datetimeoffset`.|  
|Se una colonna o un set di colonne è una chiave o una chiave approssimativa per la tabella selezionata.|**Valori duplicati in una colonna chiave potenziale**: si analizzano, ad esempio, le colonne Name e Address di una tabella Customer e si individuano valori duplicati laddove la combinazione di nome e indirizzo dovrebbe essere univoca.|**Chiave candidata**: profilo per più colonne che segnala se una colonna o un set di colonne può fungere da chiave per la tabella selezionata. Valido per colonne con uno dei tipi di dati indicati di seguito.<br /><br /> Tipi di dati integer: `bit`, `tinyint`, `smallint`, `int` e `bigint`<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`<br /><br /> Tipi di dati di data e ora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` e `datetimeoffset`.|  
|Grado di dipendenza dei valori inclusi in una colonna (colonna dipendente) dai valori presenti in un'altra colonna o set di colonne (colonna determinante).|**Valori non validi nelle colonne dipendenti**: si analizza, ad esempio, una dipendenza tra una colonna contenente i codici postali ZIP (Stati Uniti) e una colonna contenente gli stati degli Stati Uniti. Ciascun codice postale dovrebbe corrispondere sempre allo stesso stato. Il profilo individua tuttavia violazioni della dipendenza.|**Dipendenza funzionale, ovvero**valido per le colonne con uno di questi tipi di dati:<br /><br /> Tipi di dati integer: `bit`, `tinyint`, `smallint`, `int` e `bigint`<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`<br /><br /> Tipi di dati di data e ora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` e `datetimeoffset`.|  
|Se una colonna o un set di colonne può fungere da chiave esterna tra le tabelle selezionate.<br /><br /> Ovvero, il profilo segnala la sovrapposizione nei valori tra due colonne o set di colonne.|**Valori non validi**: si analizza, ad esempio, la colonna ProductID di una tabella Sales. Il profilo individua che la colonna contiene valori non inclusi nella colonna ProductID della tabella Products.|**Inclusione valore**: valido per le colonne con uno dei tipi di dati indicati di seguito:<br /><br /> Tipi di dati integer: `bit`, `tinyint`, `smallint`, `int` e `bigint`<br /><br /> Tipi di dati carattere: `char`, `nchar`, `varchar` e `nvarchar`<br /><br /> Tipi di dati di data e ora: `datetime`, `smalldatetime`, `timestamp`, `date`, `time`, `datetime2` e `datetimeoffset`.|  
  
 Per selezionare i profili da calcolare, usare la pagina **Richieste profilo** di Editor attività Profiling dati. Per altre informazioni, vedere [Editor attività Profiling dati &#40;pagina Richieste profilo&#41;](data-profiling-task-editor-profile-requests-page.md).  
  
 Nella pagina **Richieste profilo** è inoltre possibile specificare l'origine dati e configurare i profili dati. Quando si configura l'attività, tenere presenti le informazioni seguenti:  
  
-   Per semplificare la configurazione e l'individuazione delle caratteristiche di dati poco noti, è possibile usare il carattere jolly **(\*)** al posto di un singolo nome di colonna. Se si utilizza questo carattere jolly, l'attività eseguirà il profiling di tutte le colonne con un tipo di dati appropriato, il che rallenterà ulteriormente l'elaborazione.  
  
-   Quando la tabella o la vista selezionata è vuota, l'attività Profiling dati non calcola i profili.  
  
-   Quando tutti i valori nella colonna selezionata sono Null, l'attività Profiling dati calcola solo il profilo Rapporto di valori Null nella colonna. Non calcola il profilo Distribuzione lunghezze di colonna, Criteri di ricerca colonna, Statistiche di colonna o Distribuzione valori di colonna per la colonna vuota.  
  
 A ognuno dei profili dati disponibili si applicano opzioni di configurazione specifiche. Per ulteriori informazioni su tali opzioni, vedere gli argomenti seguenti:  
  
-   [Opzioni di richiesta profilo chiave candidata &#40;attività Profiling dati&#41;](candidate-key-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo distribuzione lunghezze di colonna &#40;attività Profiling dati&#41;](column-length-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo rapporto di valori Null di colonna &#40;attività Profiling dati&#41;](column-null-ratio-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo criteri di ricerca colonna &#40;attività Profiling dati&#41;](column-pattern-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo statistiche di colonna &#40;attività Profiling dati&#41;](column-statistics-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo distribuzione valori di colonna &#40;attività Profiling dati&#41;](column-value-distribution-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo dipendenza funzionale &#40;attività Profiling dati&#41;](functional-dependency-profile-request-options-data-profiling-task.md)  
  
-   [Opzioni di richiesta profilo inclusione valore &#40;attività Profiling dati&#41;](value-inclusion-profile-request-options-data-profiling-task.md)  
  
## <a name="execution-of-the-package-that-contains-the-data-profiling-task"></a>Esecuzione del pacchetto contenente l'attività Profiling dati  
 Dopo avere configurato l'attività Profiling dati, è possibile eseguirla. L'attività calcola quindi i profili dati e restituisce queste informazioni in formato XML in un file o una variabile del pacchetto. La struttura di tale formato XML segue lo schema DataProfile.xsd. È possibile aprire lo schema in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o in un altro editor di schemi, in un editor XML o in un editor di testo, ad esempio Blocco note. Questo schema per le informazioni sulla qualità dei dati può essere utile nelle situazioni seguenti:  
  
-   Scambio di informazioni sulla qualità dei dati all'interno di un'organizzazione e tra organizzazioni diverse.  
  
-   Compilazione di strumenti personalizzati da utilizzare con le informazioni sulla qualità dei dati.  
  
 Lo spazio dei nomi di destinazione viene identificato nello schema come [http://schemas.microsoft.com/sqlserver/2008/DataDebugger/](http://schemas.microsoft.com/sqlserver/2008/DataDebugger/).  
  
## <a name="next-step"></a>Passaggio successivo  
 [Visualizzatore profilo dati](data-profile-viewer.md).  
  
  
