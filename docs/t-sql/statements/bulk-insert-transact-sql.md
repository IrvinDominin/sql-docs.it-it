---
title: INSERIMENTO BULK (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- BULK_TSQL
- BULK INSERT
- BULK_INSERT_TSQL
- BULK
dev_langs:
- TSQL
helpviewer_keywords:
- tables [SQL Server], importing data into
- inserting files
- views [SQL Server], importing data into
- BULK INSERT statement
- views [SQL Server], exporting data from
- importing data, bulk import
- bulk importing [SQL Server], BULK INSERT statement
- file importing [SQL Server]
ms.assetid: be3984e1-5ab3-4226-a539-a9f58e1e01e2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ec29eaa73339980516f4a3de4b67fa195953d80a
ms.sourcegitcommit: 7673ad0e84a6de69420e19247a59e39ca751a8aa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="bulk-insert-transact-sql"></a>BULK INSERT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Importa un file di dati in una tabella o una vista di database in un formato specificato dall'utente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BULK INSERT   
   [ database_name . [ schema_name ] . | schema_name . ] [ table_name | view_name ]   
      FROM 'data_file'   
     [ WITH   
    (   
   [ [ , ] BATCHSIZE = batch_size ]   
   [ [ , ] CHECK_CONSTRAINTS ]   
   [ [ , ] CODEPAGE = { 'ACP' | 'OEM' | 'RAW' | 'code_page' } ]   
   [ [ , ] DATAFILETYPE =   
      { 'char' | 'native'| 'widechar' | 'widenative' } ]   
   [ [ , ] DATASOURCE = 'data_source_name' ]
   [ [ , ] ERRORFILE = 'file_name' ]
   [ [ , ] ERRORFILE_DATASOURCE = 'data_source_name' ]   
   [ [ , ] FIRSTROW = first_row ]   
   [ [ , ] FIRE_TRIGGERS ]   
   [ [ , ] FORMATFILE_DATASOURCE = 'data_source_name' ]
   [ [ , ] KEEPIDENTITY ]   
   [ [ , ] KEEPNULLS ]   
   [ [ , ] KILOBYTES_PER_BATCH = kilobytes_per_batch ]   
   [ [ , ] LASTROW = last_row ]   
   [ [ , ] MAXERRORS = max_errors ]   
   [ [ , ] ORDER ( { column [ ASC | DESC ] } [ ,...n ] ) ]   
   [ [ , ] ROWS_PER_BATCH = rows_per_batch ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
   [ [ , ] TABLOCK ]   

   -- input file format options
   [ [ , ] FORMAT = 'CSV' ]
   [ [ , ] FIELDQUOTE = 'quote_characters']
   [ [ , ] FORMATFILE = 'format_file_path' ]   
   [ [ , ] FIELDTERMINATOR = 'field_terminator' ]   
   [ [ , ] ROWTERMINATOR = 'row_terminator' ]   
    )]   
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database contenente la tabella o la vista specificata. Se viene omesso, il valore predefinito è il database corrente.  
  
 *schema_name*  
 Nome dello schema della tabella o della vista. *schema_name* è facoltativo se lo schema predefinito per l'utente che esegue l'operazione di importazione bulk corrisponde allo schema della tabella specificata o della vista. Se *schema* non è specificato e lo schema predefinito dell'utente che esegue l'operazione di importazione bulk è diverso dalla tabella specificata o della vista, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce un messaggio di errore e l'operazione di importazione bulk viene annullata.  
  
 *table_name*  
 Nome della tabella o della vista in cui eseguire l'importazione bulk dei dati. È possibile utilizzare solo le viste in cui tutte le colonne fanno riferimento alla stessa tabella di base. Per ulteriori informazioni sulle restrizioni per il caricamento dei dati nelle viste, vedere [INSERT &#40; Transact-SQL &#41; ](../../t-sql/statements/insert-transact-sql.md).  
  
 **'** *data_file* **'**  
 Percorso completo del file contenente i dati da importare nella tabella o nella vista specificata. L'istruzione BULK INSERT consente di importare dati da un disco, ad esempio unità di rete, dischi floppy, dischi rigidi e così via.   
 
 *data_file* deve specificare un percorso valido dal server in cui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione. Se *data_file* è remota di file, specificare il nome UNC Universal Naming Convention (). Il formato di un nome UNC è \\ \\ *NomeSistema*\\*ShareName*\\*percorso* \\ *FileName*. Ad esempio, `\\SystemX\DiskZ\Sales\update.txt`.   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP1.1, il data_file può essere nell'archiviazione blob di Azure.

**'** *data_source_name* **'**   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Un'origine dati esterna denominata che punta al percorso di archiviazione Blob di Azure del file che verrà importato. L'origine dati esterna deve essere creata usando il `TYPE = BLOB_STORAGE` opzione aggiunto in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).    
  
 BATCHSIZE  **=**  *batch_size*  
 Specifica il numero di righe in un batch. Ogni batch viene copiato nel server come singola transazione. In caso di errori, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] esegue il commit o il rollback della transazione per ogni batch. Per impostazione predefinita, tutti i dati inclusi nel file di dati specificato costituiscono un batch. Per alcune considerazioni relative alle prestazioni, vedere la sezione "Osservazioni" di seguito in questo argomento.  
  
 CHECK_CONSTRAINTS  
 Specifica che tutti i vincoli sulla tabella o sulla vista di destinazione devono essere controllati durante l'operazione di importazione bulk. Se non si specifica l'opzione CHECK_CONSTRAINTS, i vincoli CHECK e FOREIGN KEY vengono ignorati e al termine dell'operazione il vincolo sulla tabella viene contrassegnato come non attendibile.  
  
> [!NOTE]  
>  I vincoli UNIQUE e PRIMARY KEY vengono sempre applicati. Durante l'importazione in una colonna di tipo carattere definita con un vincolo NOT NULL, tramite BULK INSERT viene inserita una stringa vuota se non è presente alcun valore nel file di testo.  
  
 A un certo punto, sarà necessario esaminare i vincoli nell'intera tabella. Se prima dell'operazione di importazione bulk la tabella non era vuota, il costo per la riconvalida dei vincoli può essere superiore a quello correlato all'applicazione dei vincoli CHECK ai dati incrementali.  
  
 Una situazione in cui può essere necessario disabilitare i vincoli (comportamento predefinito) è rappresentata dal caso in cui i dati di input contengono righe che violano i vincoli. Se si disabilitano i vincoli CHECK, è possibile importare i dati e quindi utilizzare istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per rimuovere i dati non validi.  
  
> [!NOTE]  
>  L'opzione MAXERRORS non viene applicata al controllo dei vincoli.  
  
 Tabella codici  **=**  { **'**ACP**'** | **'**OEM**'**  |  **'**RAW**'** | **'***code_page***'** }  
 Specifica la tabella codici dei dati contenuti nel file di dati. CODEPAGE è rilevante solo se i dati contengono **char**, **varchar**, o **testo** colonne con valori di carattere maggiore di **127** o minore di rispetto a **32**.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)]consiglia di specificare un nome di regole di confronto per ogni colonna in un [file di formato](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md).  
  
|Valore CODEPAGE|Description|  
|--------------------|-----------------|  
|ACP|Colonne di **char**, **varchar**, o **testo** tipo di dati vengono convertiti dal [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] / [!INCLUDE[msCoName](../../includes/msconame-md.md)] codici di Windows (ISO 1252) per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tabella codici.|  
|OEM (predefinito)|Colonne di **char**, **varchar**, o **testo** tipo di dati vengono convertiti dalla tabella codici OEM di sistema per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] codici.|  
|RAW|Non viene eseguita alcuna conversione da una tabella codici a un'altra. Si tratta dell'opzione più rapida.|  
|*code_page*|Numero specifico della tabella codici, ad esempio 850.<br /><br /> **\*\*Importante \* \***  versioni precedenti a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] non supportano la tabella codici 65001 (codifica UTF-8).|  
  
 La proprietà DATAFILETYPE  **=**  { **'char'** | **'native'** | **'widechar'**  |  **'widenative'** }  
 Specifica che l'operazione di importazione viene eseguita tramite BULK INSERT utilizzando il valore specificato per il tipo di file di dati.  
  
|Valore DATAFILETYPE|Rappresentazione di tutti i dati|  
|------------------------|------------------------------|  
|**Char** (impostazione predefinita)|Formato carattere.<br /><br /> Per altre informazioni, vedere [Usare il formato carattere per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md).|  
|**native**|Tipi di dati nativi (database). Creare il file di dati nativi eseguendo l'importazione bulk di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il **bcp** utilità.<br /><br /> Il valore native rappresenta un'alternativa con prestazioni superiori rispetto al valore char.<br /><br /> Per altre informazioni, vedere [Usare il formato nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md).|  
|**tipo widechar**|Caratteri Unicode.<br /><br /> Per altre informazioni, vedere [Usare il formato carattere Unicode per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md).|  
|**widenative**|Tipi di dati nativi (database), tranne che in **char**, **varchar**, e **testo** colonne, in cui i dati vengono archiviati come Unicode. Creare il **widenative** file dati, importazione bulk di dati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il **bcp** utilità.<br /><br /> Il **widenative** valore offre un'alternativa con prestazioni migliori per **widechar**. Se il file di dati contiene [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)] caratteri estesi, specificare **widenative**.<br /><br /> Per altre informazioni, vedere [Usare il formato Unicode nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md).|  
  
  ERRORFILE **='***file_name***'**  
 Specifica il file utilizzato per raccogliere le righe che contengono errori di formattazione e non possono essere convertite in un set di righe OLE DB. Tali righe vengono copiate nel file degli errori dal file di dati così come sono.  
  
 Il file degli errori viene creato durante l'esecuzione del comando. Se il file esiste già, viene generato un errore. Viene inoltre creato un file di controllo con estensione ERROR.txt. Questo file contiene un riferimento a ogni riga nel file degli errori e offre informazioni di diagnostica. Una volta corretti gli errori, è possibile caricare i dati.   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)], `error_file_path` può essere nell'archiviazione blob di Azure.

'errorfile_data_source_name'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.
Un'origine dati esterna denominata che punta al percorso di archiviazione Blob di Azure che conterrà gli errori rilevati durante l'importazione degli errori. L'origine dati esterna deve essere creata usando il `TYPE = BLOB_STORAGE` opzione aggiunto in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
 
 FIRSTROW  **=**  *first_row*  
 Specifica il numero della prima riga da caricare. Il valore predefinito è la prima riga nel file di dati specificato. FIRSTROW è in base 1.  
  
> [!NOTE]  
>  L'attributo FIRSTROW non è progettato per ignorare le intestazioni di colonna. Nell'istruzione BULK INSERT non è possibile ignorare le intestazioni. Quando vengono ignorate righe specifiche, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] esegue la ricerca solo nei caratteri di terminazione dei campi e non convalida i dati nei campi delle righe ignorate.  
  
 FIRE_TRIGGERS  
 Specifica che gli eventuali trigger di inserimento definiti nella tabella di destinazione vengono eseguiti durante l'operazione di importazione bulk. Se sono presenti trigger definiti per operazioni INSERT nella tabella di destinazione, questi trigger vengono attivati per ogni batch completato.  
  
 Se non si specifica FIRE_TRIGGERS, non viene eseguito alcun trigger di inserimento.  

FORMATFILE_DATASOURCE  **=**  'data_source_name'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1.   
Un'origine dati esterna denominata che punta al percorso di archiviazione Blob di Azure del file di formato che definisce lo schema dei dati importati. L'origine dati esterna deve essere creata usando il `TYPE = BLOB_STORAGE` opzione aggiunto in [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1. Per ulteriori informazioni, vedere [CREATE EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md).
  
 KEEPIDENTITY  
 Specifica che il valore o i valori Identity presenti nel file di dati importato devono essere usati per la colonna Identity. Se KEEPIDENTITY viene omesso, i valori Identity per la colonna vengono verificati ma non importati e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna automaticamente valori univoci in base ai valori di inizializzazione e di incremento specificati in fase di creazione della tabella. Se il file di dati non contiene valori per la colonna Identity nella tabella o nella vista, utilizzare un file di formato per specificare che durante l'importazione dei dati la colonna Identity nella tabella o nella vista deve essere ignorata. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna automaticamente valori univoci alla colonna. Per altre informazioni, vedere [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md).  
  
 Per ulteriori informazioni sul mantenimento identificare i valori, vedere [mantenere identità valori quando importazione Bulk di dati &#40; SQL Server &#41; ](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md).  
  
 KEEPNULLS  
 Specifica che durante l'operazione di importazione bulk le colonne vuote devono mantenere un valore Null. Ciò significa che durante l'operazione non verranno inseriti eventuali valori predefiniti per le colonne vuote. Per altre informazioni, vedere [Mantenere i valori Null o usare i valori predefiniti durante l'importazione in blocco &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md).  
  
 KILOBYTES_PER_BATCH  **=**  *kilobytes_per_batch*  
 Specifica il numero approssimativo di kilobyte (KB) di dati per ogni batch come *kilobytes_per_batch*. Per impostazione predefinita, il valore KILOBYTES_PER_BATCH è sconosciuto. Per alcune considerazioni relative alle prestazioni, vedere la sezione "Osservazioni" di seguito in questo argomento.  
  
 LASTROW**=***last_row*  
 Specifica il numero dell'ultima riga da caricare. Il valore predefinito è 0, che indica l'ultima riga nel file di dati specificato.  
  
 MAXERRORS  **=**  *max_errors*  
 Specifica il numero massimo di errori di sintassi consentiti nei dati prima dell'annullamento dell'operazione di importazione bulk. Ogni riga che non è possibile importare tramite l'operazione di importazione bulk viene ignorata e considerata come errore. Se *max_errors* non viene specificato, il valore predefinito è 10.  
  
> [!NOTE]  
>  L'opzione MAX_ERRORS non si applica alle verifiche dei vincoli o alla conversione **money** e **bigint** tipi di dati.  
  
 ORDINE ({ *colonna* [ASC | DESC]} [ **,**... *n* ] )  
 Specifica il tipo di ordinamento dei dati nel file. Le prestazioni dell'importazione bulk sono migliori se i dati da importare vengono ordinati in base all'indice cluster della tabella, se disponibile. Se il file di dati viene ordinato in modo diverso rispetto all'ordine di una chiave di indice cluster o se la tabella non include un indice cluster, la clausola ORDER viene ignorata. I nomi di colonna specificati devono corrispondere a nomi di colonna validi nella tabella di destinazione. Per impostazione predefinita, per l'operazione di inserimento bulk si presume che il file di dati non sia ordinato. Per garantire l'ottimizzazione dell'importazione bulk, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene inoltre verificato che i dati importati siano ordinati.  
  
 *n*  
 Segnaposto che indica la possibilità di specificare più colonne.  
  
 ROWS_PER_BATCH  **=**  *rows_per_batch*  
 Indica il numero approssimativo di righe di dati nel file di dati.  
  
 Per impostazione predefinita, tutti i dati nel file di dati vengono inviati al server come singola transazione e il numero di righe nel batch non è noto per Query Optimizer. Se si specifica ROWS_PER_BATCH (con valore > 0), il server utilizza questo valore per ottimizzare l'operazione di importazione bulk. Il valore specificato per ROWS_PER_BATCH deve essere più o meno uguale al numero effettivo di righe. Per alcune considerazioni relative alle prestazioni, vedere la sezione "Osservazioni" di seguito in questo argomento.  
  
 
 TABLOCK  
 Imposta l'acquisizione di un blocco a livello di tabella per l'intera durata dell'operazione di importazione bulk. Una tabella può essere caricata simultaneamente da più client se non include indici e si specifica TABLOCK. Per impostazione predefinita, la modalità di blocco è determinata dall'opzione **table lock on bulk load**della tabella. Quando un blocco viene mantenuto attivo solo per la durata dell'operazione di importazione bulk, la contesa tra blocchi nella tabella viene ridotta, producendo in alcuni casi un miglioramento significativo delle prestazioni. Per alcune considerazioni relative alle prestazioni, vedere la sezione "Osservazioni" di seguito in questo argomento.  
  
 Per un indice columnstore. il comportamento di blocco è diverso perché internamente è suddiviso in più set di righe.  Ogni thread carica i dati esclusivamente in ogni set di righe tramite l'aggiunta di un blocco X del set di righe che consente il caricamento parallelo dei dati con le sessioni di caricamento dati simultanee. L'uso dell'opzione TABLOCK causerà thread ottenere un blocco X sulla tabella (a differenza di blocco aggiornamenti bulk per set di righe tradizionale) in modo da evitare altri thread simultanei per caricare i dati contemporaneamente.  

### <a name="input-file-format-options"></a>Opzioni di formato di file di input
  
FORMATO  **=**  'CSV'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Specifica un file di valori separati da virgole conforme il [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.

FIELDQUOTE  **=**  'field_quote'   
**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
Specifica un carattere che verrà utilizzato come carattere di virgolette nel file CSV. Se non specificato, il carattere virgoletta (") da utilizzare come carattere di virgolette come definito nel [RFC 4180](https://tools.ietf.org/html/rfc4180) standard.
  
 FORMATFILE **='***format_file_path***'**  
 Specifica il percorso completo di un file di formato. Un file di formato descrive il file di dati contenente le risposte archiviate create tramite il **bcp** utilità nella stessa tabella o nella vista. È consigliabile utilizzare il file di formato nei casi seguenti:  
  
-   Il file di dati contiene un numero di colonne maggiore o minore rispetto alla tabella o alla vista.  
  
-   Le colonne sono in un ordine diverso.  
  
-   I delimitatori di colonna variano.  
  
-   Sono presenti altre modifiche di formato dei dati. File di formato vengono in genere creati utilizzando il **bcp** utilità e modificati in un editor di testo in base alle esigenze. Per altre informazioni, vedere [bcp Utility](../../tools/bcp-utility.md).  

**Si applica a:** [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1.   
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] CTP 1.1, il format_file_path può essere nell'archiviazione blob di Azure.

 FIELDTERMINATOR **='***field_terminator***'**  
 Specifica il carattere di terminazione del campo da utilizzare per **char** e **widechar** i file di dati. Il carattere di terminazione del campo predefinito è \t (carattere di tabulazione). Per altre informazioni, vedere [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  

 ROWTERMINATOR **='***row_terminator***'**  
 Specifica il carattere di terminazione di riga da utilizzare per **char** e **widechar** i file di dati. Il terminatore di riga predefinito è **\r\n** (carattere di nuova riga).  Per altre informazioni, vedere [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md).  

  
## <a name="compatibility"></a>Compatibilità  
 L'istruzione BULK INSERT consente di applicare meccanismi restrittivi di convalida e controllo dei dati letti da un file che potrebbero causare errori negli script esistenti eseguiti in dati non validi. L'istruzione BULK INSERT, ad esempio, prevede le verifiche seguenti:  
  
-   Le rappresentazioni native di **float** o **reale** tipi di dati sono validi.  
  
-   Lunghezza in byte pari dei dati Unicode.  
  
## <a name="data-types"></a>Tipi di dati  
  
### <a name="string-to-decimal-data-type-conversions"></a>Conversione del tipo di dati da string a decimal  
 Le conversioni del tipo di dati da string a decimal utilizzate in BULK INSERT seguono le stesse regole di [!INCLUDE[tsql](../../includes/tsql-md.md)] [CONVERTIRE](../../t-sql/functions/cast-and-convert-transact-sql.md) (funzione), che rifiuta le stringhe che rappresentano valori numerici con notazione scientifica. Tali stringhe vengono quindi considerate da BULK INSERT come valori non validi e vengono segnalati errori di conversione.  
  
 Per risolvere questo problema, utilizzare un file di formato per la notazione scientifica importazione bulk **float** dati in una colonna decimale. Nel file di formato, descrivere in modo esplicito la colonna come **reale** o **float** dati. Per ulteriori informazioni su questi tipi di dati, vedere [float e real &#40; Transact-SQL &#41; ](../../t-sql/data-types/float-and-real-transact-sql.md).  
  
> [!NOTE]  
>  Formato file rappresentano **reale** dati come il **SQLFLT4** tipo di dati e **float** dati come il **SQLFLT8** tipo di dati. Per informazioni sui file di formato non XML, vedere [specificare tipo di archiviazione File tramite bcp &#40; SQL Server &#41; ](../../relational-databases/import-export/specify-file-storage-type-by-using-bcp-sql-server.md).  
  
#### <a name="example-of-importing-a-numeric-value-that-uses-scientific-notation"></a>Esempio di importazione di un valore numerico con notazione scientifica  
 Nell'esempio viene utilizzata la tabella seguente:  
  
```  
CREATE TABLE t_float(c1 float, c2 decimal (5,4));  
```  
  
 Si desidera eseguire l'importazione bulk di dati nella tabella `t_float`. Il file di dati, C:\t_float-c.dat, include la notazione scientifica **float** dati, ad esempio:  
  
```  
8.0000000000000002E-28.0000000000000002E-2  
```  
  
 Non è tuttavia possibile importare i dati direttamente nella tabella `t_float` tramite BULK INSERT, in quanto la seconda colonna della tabella, `c2`, utilizza il tipo di dati `decimal`. È pertanto necessario un file di formato. Il file di formato è necessario mappare la notazione scientifica **float** dati nel formato decimale della colonna `c2`.  
  
 Nel file di formato seguente viene utilizzato il tipo di dati `SQLFLT8` per eseguire il mapping del secondo campo dati alla seconda colonna:  
  
 ```
 <?xml version="1.0"?> 
 <BCPFORMAT xmlns="http://schemas.microsoft.com/sqlserver/2004/bulkload/format" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> 
 <RECORD> 
 <FIELD ID="1" xsi:type="CharTerm" TERMINATOR="\t" MAX_LENGTH="30"/> 
 <FIELD ID="2" xsi:type="CharTerm" TERMINATOR="\r\n" MAX_LENGTH="30"/>  </RECORD>  <ROW> 
 <COLUMN SOURCE="1" NAME="c1" xsi:type="SQLFLT8"/> 
 <COLUMN SOURCE="2" NAME="c2" xsi:type="SQLFLT8"/>  </ROW> </BCPFORMAT> 
 ```
  
 Per importare i dati di prova nella tabella di prova utilizzando questo file di formato con il nome di file `C:\t_floatformat-c-xml.xml`, eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente:  
  
```  
BULK INSERT bulktest..t_float  
FROM 'C:\t_float-c.dat' WITH (FORMATFILE='C:\t_floatformat-c-xml.xml');  
GO  
```  
  
### <a name="data-types-for-bulk-exporting-or-importing-sqlxml-documents"></a>Tipi di dati per l'esportazione o l'importazione bulk di documenti SQLXML  
 Per eseguire l'esportazione o l'importazione bulk di dati SQLXML, utilizzare uno dei tipi di dati seguenti nel file di formato:  
  
|Tipo di dati|Effetto|  
|---------------|------------|  
|SQLCHAR o SQLVARCHAR|I dati vengono inviati nella tabella codici del client o nella tabella codici implicita delle regole di confronto. L'effetto è lo stesso ottenuto specificando DATAFILETYPE **= 'char'** senza specificare un file di formato.|  
|SQLNCHAR o SQLNVARCHAR|I dati vengono inviati in formato Unicode. L'effetto è lo stesso ottenuto specificando DATAFILETYPE **= 'widechar'** senza specificare un file di formato.|  
|SQLBINARY o SQLVARBIN|I dati vengono inviati senza conversione.|  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Per un confronto tra l'istruzione BULK INSERT, l'istruzione INSERT ... Selezionare \* da OPENROWSET e **bcp** command, vedere [importazione in blocco e l'esportazione di dati &#40; SQL Server &#41; ](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Per informazioni sulla preparazione dei dati per l'importazione bulk, vedere [preparazione dei dati per l'esportazione Bulk o importazione &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
 L'istruzione BULK INSERT può essere eseguita all'interno di una transazione definita dall'utente per importare dati in una tabella o una vista. Facoltativamente, per utilizzare più corrispondenze per l'importazione bulk dei dati, una transazione può consentire di specificare la clausola BATCHSIZE nell'istruzione BULK INSERT. Se una transazione con più batch viene sottoposta a rollback, tale operazione viene effettuata anche per ogni batch che è stato inviato a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dalla transazione.  
  
## <a name="interoperability"></a>Interoperabilità  
  
### <a name="importing-data-from-a-csv-file"></a>Importazione di dati da un file CSV  
A partire da [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1 CTP, BULK INSERT supporta il formato CSV.  
Prima di [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 1.1 CTP, valore delimitato da virgole (CSV) file non sono supportati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] operazioni di importazione bulk. In alcuni casi, tuttavia, è possibile usare un file CSV come file di dati per un'importazione bulk di dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per informazioni sui requisiti per l'importazione di dati da un file di dati CSV, vedere [preparazione dei dati per l'esportazione Bulk o importazione &#40; SQL Server &#41; ](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md).  
  
## <a name="logging-behavior"></a>Comportamento di registrazione  
 Per informazioni sui casi in cui le operazioni di inserimento di righe eseguite durante l'importazione in blocco vengono registrate nel log delle transazioni, vedere [Prerequisiti per la registrazione minima nell'importazione in blocco](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md).  
  
##  <a name="Limitations"></a> Restrizioni  
 Quando si utilizza un file di formato con BULK INSERT, è possibile specificare al massimo 1024 campi. Si tratta dello stesso numero massimo di colonne consentite in una tabella. Se si utilizza l'istruzione BULK INSERT con un file di dati contenente più di 1024 campi, verrà generato l'errore 4822. Il [utilità bcp](../../tools/bcp-utility.md) non dispone di questa limitazione, di conseguenza, per i file di dati che contengono più di 1024 campi, usare il **bcp** comando.  
  
## <a name="performance-considerations"></a>Considerazioni sulle prestazioni  
 Se il numero di pagine da scaricare in un singolo batch supera una soglia interna, è possibile che venga eseguita un'analisi completa del pool di buffer per identificare le pagine da scaricare durante il commit del batch. L'analisi completa può influire sulle prestazioni dell'importazione bulk. Un probabile caso di superamento della soglia interna si verifica quando un pool di buffer di grandi dimensioni è combinato a un sottosistema di I/O lento. Per evitare gli overflow del buffer in sistemi di grandi dimensioni, non utilizzare l'hint TABLOCK, che elimina l'ottimizzazione delle operazioni bulk, o utilizzare un batch di dimensioni minori, che mantiene l'ottimizzazione delle operazioni bulk.  
  
 È consigliabile testare diverse dimensioni del batch con il caricamento dei dati per individuare la soluzione più adatta per il computer in uso.  
  
## <a name="security"></a>Security  
  
### <a name="security-account-delegation-impersonation"></a>Delega degli account di sicurezza (rappresentazione)  
 Se un utente utilizza un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , viene utilizzato il profilo di sicurezza dell'account del processo di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Un account di accesso basato sull'autenticazione di SQL Server non può essere autenticato all'esterno del motore di database. Pertanto, quando un comando BULK INSERT viene avviato da un account di accesso che utilizza l'autenticazione di SQL, la connessione ai dati viene effettuata utilizzando il contesto di sicurezza dell'account del processo di SQL Server (l'account utilizzato dal servizio Motore di database di SQL Server). Per una lettura corretta dei dati di origine è necessario concedere all'account utilizzato dal motore di database di SQL Server l'accesso ai dati di origine. Al contrario, un utente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che esegue l'accesso utilizzando l'autenticazione di Windows potrà leggere solo i file a cui l'account utente può accedere, indipendentemente dal profilo di sicurezza del processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Quando si esegue l'istruzione BULK INSERT utilizzando **sqlcmd** o **osql**, da un computer, si inseriscono dati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un secondo computer e specificando un *data_file* nel terzo computer utilizzando un percorso UNC, è possibile che venga visualizzato l'errore 4861.  
  
 Per risolvere questo errore, utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione e specificare un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso che utilizza il profilo di sicurezza del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account processo oppure configurare Windows per consentire la delega degli account di sicurezza. Per informazioni sull'abilitazione di un account utente in modo che venga considerato attendibile per la delega, vedere la Guida di Windows.  
  
 Per ulteriori informazioni su questa e altre considerazioni sulla sicurezza per l'utilizzo di BULK INSERT, vedere [importazione Bulk dei dati per l'utilizzo di BULK INSERT o OPENROWSET &#40; BULK... &#41; &#40; SQL Server &#41; ](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md).  
  
### <a name="permissions"></a>Autorizzazioni  
 Sono necessarie le autorizzazioni INSERT e ADMINISTER BULK OPERATIONS. Nel Database di SQL Azure, sono necessarie autorizzazioni INSERT e ADMINISTER DATABASE BULK OPERATIONS. È inoltre richiesta l'autorizzazione ALTER TABLE se si verificano una o più delle condizioni seguenti:  
  
-   Sono presenti vincoli e l'opzione CHECK_CONSTRAINTS non è specificata.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i vincoli sono disabilitati. Per verificare i vincoli in modo esplicito, utilizzare l'opzione CHECK_CONSTRAINTS.  
  
-   Sono presenti trigger e l'opzione FIRE_TRIGGER non è specificata.  
  
    > [!NOTE]  
    >  Per impostazione predefinita, i trigger non sono attivati. Per attivare i trigger in modo esplicito, utilizzare l'opzione FIRE_TRIGGERS.  
  
-   Si utilizza l'opzione KEEPIDENTITY per importare valori Identity dal file di dati.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-using-pipes-to-import-data-from-a-file"></a>A. Utilizzo di barre verticali per l'importazione di dati da un file  
 Nell'esempio seguente vengono importate informazioni dettagliate sugli ordini nella tabella `AdventureWorks2012.Sales.SalesOrderDetail` dal file di dati specificato, utilizzando una barra verticale (`|`) come carattere di terminazione del campo e la combinazione `|\n` come carattere di terminazione della riga.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH   
      (  
         FIELDTERMINATOR =' |',  
         ROWTERMINATOR =' |\n'  
      );  
```  
  
### <a name="b-using-the-firetriggers-argument"></a>B. Utilizzo dell'argomento FIRE_TRIGGERS  
 Nell'esempio seguente viene specificato l'argomento `FIRE_TRIGGERS`.  
  
```  
BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
   FROM 'f:\orders\lineitem.tbl'  
   WITH  
     (  
        FIELDTERMINATOR =' |',  
        ROWTERMINATOR = ':\n',  
        FIRE_TRIGGERS  
      );  
```  
  
### <a name="c-using-line-feed-as-a-row-terminator"></a>C. Utilizzo del carattere di avanzamento riga come carattere di terminazione della riga  
 Nell'esempio seguente viene importato un file che utilizza il carattere di avanzamento riga come carattere di terminazione della riga, come nel caso di output UNIX:  
  
```  
DECLARE @bulk_cmd varchar(1000);  
SET @bulk_cmd = 'BULK INSERT AdventureWorks2012.Sales.SalesOrderDetail  
FROM ''<drive>:\<path>\<filename>''   
WITH (ROWTERMINATOR = '''+CHAR(10)+''')';  
EXEC(@bulk_cmd);  
```  
  
> [!NOTE]  
>  A causa di come Microsoft Windows considera i file di testo **(\n** ottiene automaticamente sostituito con **\r\n)**.  
  
### <a name="d-specifying-a-code-page"></a>D. Definizione di una tabella codici  
 Nell'esempio seguente viene illustrato come specificare una tabella codici.  
  
```  
BULK INSERT MyTable  
FROM 'D:\data.csv'  
WITH  
( CODEPAGE = '65001',  
    DATAFILETYPE = 'char',  
    FIELDTERMINATOR = ','  
);  
```  
### <a name="e-importing-data-from-a-csv-file"></a>E. Importazione di dati da un file CSV   
Nell'esempio seguente viene illustrato come specificare un file CSV.   
```
BULK INSERT Sales.Invoices
FROM '\\share\invoices\inv-2016-07-25.csv'
WITH (FORMAT = 'CSV'); 
```

### <a name="f-importing-data-from-a-file-in-azure-blob-storage"></a>F. Importazione di dati da un file nell'archiviazione blob di Azure   
Nell'esempio seguente viene illustrato come caricare dati da un file csv in un percorso di archiviazione blob di Azure, è stato configurato come un'origine dati esterna. Ciò richiede credenziali con ambito database tramite una firma di accesso condiviso.    

```sql
BULK INSERT Sales.Invoices
FROM 'inv-2017-01-19.csv'
WITH (DATA_SOURCE = 'MyAzureInvoices',
     FORMAT = 'CSV'); 
```

Per completare `BULK INSERT` esempi inclusi la configurazione di credenziali e l'origine dati esterna, vedere [esempi di massa di accesso ai dati nell'archiviazione Blob di Azure](../../relational-databases/import-export/examples-of-bulk-access-to-data-in-azure-blob-storage.md).
  
### <a name="additional-examples"></a>Esempi aggiuntivi  
 Altri `BULK INSERT` vengono forniti esempi negli argomenti seguenti:  
  
-   [Esempi di importazione ed esportazione bulk di documenti XML &#40;SQL Server&#41;](../../relational-databases/import-export/examples-of-bulk-import-and-export-of-xml-documents-sql-server.md)  
  
-   [Mantenere i valori Identity durante l'importazione in blocco dei dati &#40;SQL Server&#41;](../../relational-databases/import-export/keep-identity-values-when-bulk-importing-data-sql-server.md)  
  
-   [Mantenere i valori Null o usare i valori predefiniti durante l'importazione in blocco &#40;SQL Server&#41;](../../relational-databases/import-export/keep-nulls-or-use-default-values-during-bulk-import-sql-server.md)  
  
-   [Impostazione dei caratteri di terminazione del campo e della riga &#40;SQL Server&#41;](../../relational-databases/import-export/specify-field-and-row-terminators-sql-server.md)  
  
-   [Usare un file di formato per l'importazione in blocco dei dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-bulk-import-data-sql-server.md)  
  
-   [Usare il formato carattere per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Usare il formato nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo del formato carattere Unicode per l'importazione o l'esportazione di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo del formato nativo per importare o esportare dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
-   [Utilizzo di un file di formato per ignorare una colonna di una tabella &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-skip-a-table-column-sql-server.md)  
  
-   [Utilizzo di un file di formato per eseguire il mapping tra le colonne della tabella e i campi del file di dati &#40;SQL Server&#41;](../../relational-databases/import-export/use-a-format-file-to-map-table-columns-to-data-file-fields-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [Utilità bcp](../../tools/bcp-utility.md)   
 [File di formato per importare o esportare dati &#40; SQL Server &#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [Preparare i dati per l'importazione o esportazione Bulk &#40; SQL Server &#41;](../../relational-databases/import-export/prepare-data-for-bulk-export-or-import-sql-server.md)   
 [sp_tableoption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
