---
title: sys.dm_db_index_operational_stats (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, pdw, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_index_operational_stats
- sys.dm_db_index_operational_stats_TSQL
- sys.dm_db_index_operational_stats
- dm_db_index_operational_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_index_operational_stats dynamic management function
ms.assetid: 13adf2e5-2150-40a6-b346-e74a33ce29c6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3866f4dfbd25fc665949455969b1546bd906462a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmdbindexoperationalstats-transact-sql"></a>sys.dm_db_index_operational_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  Restituisce l'attività corrente del metodo di I/O di basso livello, blocco, latch e accesso per ogni partizione di una tabella o un indice nel database.    
    
 Gli indici con ottimizzazione per la memoria non vengono visualizzati in questa DMV.    
    
> [!NOTE]    
>  **Sys.dm db_index_operational_stats** non restituisce informazioni sugli indici con ottimizzazione per la memoria. Per informazioni sull'uso degli indici con ottimizzazione per la memoria, vedere [sys.dm_db_xtp_index_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-xtp-index-stats-transact-sql.md).    
        
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Sintassi    
    
```    
    
sys.dm_db_index_operational_stats (    
    { database_id | NULL | 0 | DEFAULT }    
  , { object_id | NULL | 0 | DEFAULT }    
  , { index_id | 0 | NULL | -1 | DEFAULT }    
  , { partition_number | NULL | 0 | DEFAULT }    
)    
```    
    
## <a name="arguments"></a>Argomenti    
 *database_id* | NULL | 0 | DEFAULT    
 ID del database. *database_id* è **smallint**. Gli input validi sono il numero di ID di un database, NULL, 0 o DEFAULT. Il valore predefinito è 0. NULL, 0 e DEFAULT sono valori equivalenti in questo contesto.    
    
 Specificare NULL per restituire informazioni per tutti i database presenti nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si specifica NULL per *database_id*, è necessario specificare NULL anche per *object_id*, *index_id*, e *numero_partizione*.    
    
 La funzione predefinita [DB_ID](../../t-sql/functions/db-id-transact-sql.md) può essere specificato.    
    
 *object_id* | NULL | 0 | DEFAULT    
 ID oggetto della tabella o vista in cui si trova l'indice. *object_id* è di tipo **int**.    
    
 Gli input validi sono il numero di ID di una tabella o vista, NULL, 0 o DEFAULT. Il valore predefinito è 0. NULL, 0 e DEFAULT sono valori equivalenti in questo contesto.    
    
 Specificare NULL per restituire le informazioni memorizzate nella cache per tutte le tabelle e le viste nel database specificato. Se si specifica NULL per *object_id*, è necessario specificare NULL anche per *index_id* e *numero_partizione*.    
    
 *index_id* | 0 | NULL | -1 | IMPOSTAZIONE PREDEFINITA    
 ID dell'indice. *index_id* è **int**. Gli input validi sono il numero di ID di un indice, 0 se *object_id* è un heap, NULL, -1 o DEFAULT. Il valore predefinito è -1. NULL, -1 e DEFAULT sono valori equivalenti in questo contesto.    
    
 Specificare NULL per restituire le informazioni memorizzate nella cache per tutti gli indici per una vista o tabella di base. Se si specifica NULL per *index_id*, è necessario specificare NULL anche per *numero_partizione*.    
    
 *numero_partizione* | NULL | 0 | IMPOSTAZIONE PREDEFINITA    
 Numero di partizione nell'oggetto. *numero_partizione* è **int**. Gli input validi sono il *partion_number* di un indice o heap, NULL, 0 o DEFAULT. Il valore predefinito è 0. NULL, 0 e DEFAULT sono valori equivalenti in questo contesto.    
    
 Specificare NULL per restituire informazioni memorizzate nella cache per tutte le partizioni dell'indice o dell'heap.    
    
 *numero_partizione* è basato su 1. Un indice non partizionato o l'heap contiene *numero_partizione* impostato su 1.    
    
## <a name="table-returned"></a>Tabella restituita    
    
|Nome colonna|Tipo di dati|Description|    
|-----------------|---------------|-----------------|    
|**database_id**|**smallint**|ID del database.|    
|**object_id**|**int**|ID della tabella o vista.|    
|**index_id**|**int**|ID dell'indice o dell'heap.<br /><br /> 0 = heap|    
|**hobt_id**|**bigint**|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br /> ID dell'heap di dati o set di righe dell'albero B che tiene traccia dei dati interni per un indice columnstore.<br /><br /> NULL: non si tratta di un set di righe columnstore interno.<br /><br /> Per ulteriori informazioni, vedere [sys.internal_partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)|    
|**partition_number**|**int**|Numero di partizione in base 1 all'interno dell'indice o heap.|    
|**leaf_insert_count**|**bigint**|Conteggio cumulativo degli inserimenti al livello foglia.|    
|**leaf_delete_count**|**bigint**|Conteggio cumulativo delle eliminazioni al livello foglia. leaf_delete_count viene incrementato solo per i record eliminati non contrassegnati come ghost prima. Per i record eliminati vengono innanzitutto fantasma **leaf_ghost_count** viene incrementato invece.|    
|**leaf_update_count**|**bigint**|Conteggio cumulativo degli aggiornamenti al livello foglia.|    
|**leaf_ghost_count**|**bigint**|Conteggio cumulativo delle righe al livello foglia contrassegnate come eliminate ma non ancora rimosse. Questo conteggio non include i record vengono eliminati immediatamente senza essere contrassegnati come ghost. Queste righe vengono rimosse da un thread di pulizia a intervalli impostati. Questo valore non include righe memorizzate a causa di una transazione di isolamento dello snapshot in sospeso.|    
|**nonleaf_insert_count**|**bigint**|Conteggio cumulativo degli inserimenti sopra il livello foglia.<br /><br /> 0 = heap o columnstore|    
|**nonleaf_delete_count**|**bigint**|Conteggio cumulativo delle eliminazioni sopra il livello foglia.<br /><br /> 0 = heap o columnstore|    
|**nonleaf_update_count**|**bigint**|Conteggio cumulativo degli aggiornamenti sopra il livello foglia.<br /><br /> 0 = heap o columnstore|    
|**leaf_allocation_count**|**bigint**|Conteggio cumulativo delle allocazioni di pagina al livello foglia nell'indice o heap.<br /><br /> Per un indice un'allocazione di pagina corrisponde a una suddivisione di pagina.|    
|**nonleaf_allocation_count**|**bigint**|Conteggio cumulativo delle allocazioni di pagina provocate da suddivisioni di pagina sopra il livello foglia.<br /><br /> 0 = heap o columnstore|    
|**leaf_page_merge_count**|**bigint**|Conteggio cumulativo delle unioni di pagina in corrispondenza del livello foglia. Sempre 0 per un indice columnstore.|    
|**nonleaf_page_merge_count**|**bigint**|Conteggio cumulativo delle unioni di pagina sopra il livello foglia.<br /><br /> 0 = heap o columnstore|    
|**range_scan_count**|**bigint**|Conteggio cumulativo delle analisi di intervallo e tabella avviate nell'indice o nell'heap.|    
|**singleton_lookup_count**|**bigint**|Conteggio cumulativo dei recuperi di singole righe dall'indice o heap.|    
|**forwarded_fetch_count**|**bigint**|Conteggio delle righe recuperate tramite un record di inoltro.<br /><br /> 0 = Indici|    
|**lob_fetch_in_pages**|**bigint**|Conteggio cumulativo delle pagine LOB recuperate dall'unità di allocazione LOB_DATA. Queste pagine contengono dati archiviati nelle colonne di tipo **testo**, **ntext**, **immagine**, **varchar (max)**, **(nvarchar max)**, **varbinary (max)**, e **xml**. Per altre informazioni, vedere [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md).|    
|**lob_fetch_in_bytes**|**bigint**|Conteggio cumulativo dei byte di dati LOB recuperati.|    
|**lob_orphan_create_count**|**bigint**|Conteggio cumulativo dei valori LOB isolati (orfani) creati per le operazioni bulk.<br /><br /> 0 = Indice non cluster|    
|**lob_orphan_insert_count**|**bigint**|Conteggio cumulativo dei valori LOB isolati (orfani) inseriti durante le operazioni bulk.<br /><br /> 0 = Indice non cluster|    
|**row_overflow_fetch_in_pages**|**bigint**|Conteggio cumulativo delle pagine di dati di overflow della riga recuperate dall'unità di allocazione ROW_OVERFLOW_DATA.<br /><br /> Queste pagine contengono dati archiviati nelle colonne di tipo **varchar (n)**, **nvarchar (n)**, **varbinary**, e **sql_variant** che è stato inserito all'esterno di righe.|    
|**row_overflow_fetch_in_bytes**|**bigint**|Conteggio cumulativo dei byte di dati di overflow della riga recuperati.|    
|**column_value_push_off_row_count**|**bigint**|Conteggio cumulativo dei valori di colonna per i dati LOB e di overflow della riga spostati all'esterno di righe per adattare una riga inserita o aggiornata all'interno di una pagina.|    
|**column_value_pull_in_row_count**|**bigint**|Conteggio cumulativo dei valori di colonna per i dati LOB e di overflow della riga esclusi dalla riga. Ciò si verifica quando un'operazione di aggiornamento libera spazio in un record e offre l'opportunità di includere uno o più valori all'esterno di righe dall'unità di allocazione LOB_DATA o ROW_OVERFLOW_DATA nell'unità di allocazione IN_ROW_DATA.|    
|**row_lock_count**|**bigint**|Numero cumulativo di blocchi di riga richiesti.|    
|**row_lock_wait_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un blocco di riga.|    
|**row_lock_wait_in_ms**|**bigint**|Numero totale di millisecondi che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un blocco di riga.|    
|**page_lock_count**|**bigint**|Numero cumulativo di blocchi di pagina richiesti.|    
|**page_lock_wait_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un blocco di pagina.|    
|**page_lock_wait_in_ms**|**bigint**|Numero totale di millisecondi che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un blocco di pagina.|    
|**index_lock_promotion_attempt_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha tentato di alzare di livello i blocchi.|    
|**index_lock_promotion_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha alzato di livello i blocchi.|    
|**page_latch_wait_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] è rimasto in attesa a causa di una contesa di latch.|    
|**page_latch_wait_in_ms**|**bigint**|Numero cumulativo di millisecondi che [!INCLUDE[ssDE](../../includes/ssde-md.md)] è rimasto in attesa a causa di una contesa di latch.|    
|**page_io_latch_wait_count**|**bigint**|Numero cumulativo di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un latch della pagina di I/O.|    
|**page_io_latch_wait_in_ms**|**bigint**|Numero cumulativo di millisecondi che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha atteso un latch di I/O della pagina.|    
|**tree_page_latch_wait_count**|**bigint**|Subset di **page_latch_wait_count** che include solo le pagine dell'albero B di livello superiore. Sempre 0 per un heap o un indice columnstore.|    
|**tree_page_latch_wait_in_ms**|**bigint**|Subset di **page_latch_wait_in_ms** che include solo le pagine dell'albero B di livello superiore. Sempre 0 per un heap o un indice columnstore.|    
|**tree_page_io_latch_wait_count**|**bigint**|Subset di **page_io_latch_wait_count** che include solo le pagine dell'albero B di livello superiore. Sempre 0 per un heap o un indice columnstore.|    
|**tree_page_io_latch_wait_in_ms**|**bigint**|Subset di **page_io_latch_wait_in_ms** che include solo le pagine dell'albero B di livello superiore. Sempre 0 per un heap o un indice columnstore.|    
|**page_compression_attempt_count**|**bigint**|Numero di pagine valutate per la compressione di tipo PAGE per partizioni specifiche di una tabella, un indice o una vista indicizzata. Sono incluse le pagine che non sono state compresse perché la compressione non avrebbe comportato risparmi significativi. Sempre 0 per un indice columnstore.|    
|**page_compression_success_count**|**bigint**|Numero di pagine di dati valutate compresse utilizzando la compressione di tipo PAGE per partizioni specifiche di una tabella, un indice o una vista indicizzata. Sempre 0 per un indice columnstore.|    
    
## <a name="remarks"></a>Osservazioni    
 Questo oggetto a gestione dinamica non accetta parametri correlati da CROSS APPLY e OUTER APPLY.    
    
 È possibile utilizzare **Sys.dm db_index_operational_stats** per tenere traccia della quantità di tempo in cui gli utenti devono attendere per leggere o scrivere in una tabella, un indice o una partizione e identificare le tabelle o indici che vengono rilevata una significativa attività dei / o o a caldo aree sensibili.    
    
 Utilizzare le colonne seguenti per identificare le aree di contesa.    
    
 **Per analizzare un comune modello di accesso alla partizione di tabella o indice**, utilizzare le colonne:    
    
-   **leaf_insert_count**    
    
-   **leaf_delete_count**    
    
-   **leaf_update_count**    
    
-   **leaf_ghost_count**    
    
-   **range_scan_count**    
    
-   **singleton_lookup_count**    
    
 Per identificare le contese a livello di latch e blocchi, utilizzare le colonne seguenti:    
    
-   **page_latch_wait_count** e **page_latch_wait_in_ms**    
    
     Queste colonne indicano se è presente una contesa di latch nell'indice o nell'heap e specificano l'importanza di tale contesa.    
    
-   **row_lock_count** e **page_lock_count**    
    
     Queste colonne indicano il numero di volte che [!INCLUDE[ssDE](../../includes/ssde-md.md)] ha cercato di acquisire blocchi di riga e pagina.    
    
-   **row_lock_wait_in_ms** e **page_lock_wait_in_ms**    
    
     Queste colonne indicano se è presente una contesa di blocchi nell'indice o heap e l'importanza di tale contesa.    
    
 **Per analizzare le statistiche dei / o fisici in una partizione di indice o heap**    
    
-   **page_io_latch_wait_count** e **page_io_latch_wait_in_ms**    
    
     Queste colonne indicano se gli I/O fisici sono stati eseguiti per inserire le pagine di indice o heap in memoria e il numero di I/O eseguiti.    
    
## <a name="column-remarks"></a>Osservazioni relative alle colonne    
 I valori in **lob_orphan_create_count** e **lob_orphan_insert_count** devono essere sempre uguali.    
    
 Il valore nelle colonne **lob_fetch_in_pages** e **lob_fetch_in_bytes** può essere maggiore di zero per indici non cluster contenenti una o più colonne LOB come colonne incluse. Per altre informazioni, vedere [Creare indici con colonne incluse](../../relational-databases/indexes/create-indexes-with-included-columns.md). Analogamente, il valore nelle colonne **row_overflow_fetch_in_pages** e **row_overflow_fetch_in_bytes** può essere maggiore di 0 per indici non cluster se l'indice include colonne che possono essere distribuite all'esterno di righe.    
    
## <a name="how-the-counters-in-the-metadata-cache-are-reset"></a>Procedura di ripristino dei contatori nella cache dei metadati    
 I dati restituiti da **Sys.dm db_index_operational_stats** esiste solo finché è disponibile l'oggetto cache dei metadati che rappresenta l'indice o heap. Questi dati non sono persistenti, né consistenti dal punto di vista transazionale. Ciò significa che non è possibile utilizzare questi contatori per determinare se un indice è stato utilizzato o meno oppure quando l'indice è stato utilizzato per l'ultima volta. Per ulteriori informazioni, vedere [Sys.dm db_index_usage_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md).    
    
 I valori di ogni colonna vengono impostati su zero ogni volta che i metadati per l'heap o l'indice vengono inseriti nella cache dei metadati e le statistiche vengono accumulate finché l'oggetto cache non viene rimosso dalla cache dei metadati. È pertanto possibile che un heap o un indice attivo disponga sempre dei relativi metadati nella cache e che il conteggio cumulativo rifletta l'attività dall'ultimo avvio dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I metadati di un heap o un indice meno attivo verranno inseriti nella e rimossi dalla cache in base al loro utilizzo. Ne consegue che i valori potrebbero non essere disponibili. L'eliminazione di un indice comporterà la rimozione delle statistiche corrispondenti dalla memoria e tali dati non verranno più rilevati dalla funzione. Altre operazioni DDL nell'indice potrebbero provocare l'azzeramento del valore delle statistiche.    
    
## <a name="using-system-functions-to-specify-parameter-values"></a>Utilizzo di funzioni di sistema per specificare i valori dei parametri    
 È possibile utilizzare il [!INCLUDE[tsql](../../includes/tsql-md.md)] funzioni [DB_ID](../../t-sql/functions/db-id-transact-sql.md) e [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md) per specificare un valore per il *database_id* e *object_id* parametri. Se si passano valori non validi a queste funzioni, tuttavia, si potrebbero provocare risultati imprevisti. Quando si usa DB_ID o OBJECT_ID, verificare sempre che venga restituito un ID valido. Per ulteriori informazioni, vedere la sezione Osservazioni in [Sys.dm db_index_physical_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md).    
    
## <a name="permissions"></a>Autorizzazioni    
 Sono richieste le autorizzazioni seguenti:    
    
-   Autorizzazione CONTROL per l'oggetto specificato nel database    
    
-   Autorizzazione VIEW DATABASE STATE per restituire informazioni su tutti gli oggetti all'interno del database specificato, utilizzando il carattere jolly di oggetto @*object_id* = NULL    
    
-   Autorizzazione VIEW SERVER STATE per restituire informazioni su tutti i database, utilizzando il carattere jolly di database @*database_id* = NULL    
    
 La concessione di VIEW DATABASE STATE consente la restituzione di tutti gli oggetti nel database, indipendentemente dalle eventuali autorizzazioni CONTROL negate per oggetti specifici.    
    
 La negazione di VIEW DATABASE STATE non consente la restituzione di tutti gli oggetti nel database, indipendentemente dalle eventuali autorizzazioni CONTROL concesse per oggetti specifici. Inoltre, quando il carattere jolly di database @*database_id*= NULL è specificato, il database viene omesso.    
    
 Per ulteriori informazioni, vedere [funzioni e viste a gestione dinamica &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).    
    
## <a name="examples"></a>Esempi    
    
### <a name="a-returning-information-for-a-specified-table"></a>A. Visualizzazione di informazioni per una tabella specifica    
 Nell'esempio seguente vengono restituite informazioni per tutti gli indici e le partizioni della tabella `Person.Address` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]. Per eseguire questa query, è necessario disporre almeno dell'autorizzazione CONTROL per la tabella `Person.Address`.    
    
> [!IMPORTANT]    
>  In caso di utilizzo delle funzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] DB_ID e OBJECT_ID per restituire un valore di parametro, assicurarsi sempre che venga restituito un ID valido. Se risulta impossibile trovare il nome del database o dell'oggetto, ad esempio quando tali nomi non esistono o sono stati immessi con un'ortografia errata, entrambe le funzioni restituiranno NULL. Il **Sys.dm db_index_operational_stats** funzione interpreta NULL come valore di carattere jolly che specifica tutti i database o tutti gli oggetti. Poiché può trattarsi di un'operazione accidentale, gli esempi riportati in questa sezione dimostrano la procedura sicura per determinare gli ID di database e oggetti.    
    
```    
DECLARE @db_id int;    
DECLARE @object_id int;    
SET @db_id = DB_ID(N'AdventureWorks2012');    
SET @object_id = OBJECT_ID(N'AdventureWorks2012.Person.Address');    
IF @db_id IS NULL     
  BEGIN;    
    PRINT N'Invalid database';    
  END;    
ELSE IF @object_id IS NULL    
  BEGIN;    
    PRINT N'Invalid object';    
  END;    
ELSE    
  BEGIN;    
    SELECT * FROM sys.dm_db_index_operational_stats(@db_id, @object_id, NULL, NULL);    
  END;    
GO    
    
```    
    
### <a name="b-returning-information-for-all-tables-and-indexes"></a>B. Restituzione delle informazioni per tutti gli indici e le tabelle    
 Nell'esempio seguente vengono restituite informazioni per tutte le tabelle e tutti gli indici nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'esecuzione di questa query richiede l'autorizzazione VIEW SERVER STATE.    
    
```    
SELECT * FROM sys.dm_db_index_operational_stats( NULL, NULL, NULL, NULL);    
GO    
    
```    
    
## <a name="see-also"></a>Vedere anche    
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)     
 [Funzioni a gestione dinamica e DMV correlate all'indice &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/index-related-dynamic-management-views-and-functions-transact-sql.md)     
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)     
 [sys.dm_db_index_usage_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-usage-stats-transact-sql.md)     
 [sys.dm_os_latch_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md)     
 [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql.md)     
 [sys.allocation_units &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)     
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)    
    
  

