---
title: Indici columnstore - Panoramica | Microsoft Docs
ms.custom: 
ms.date: 03/07/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Active
ms.openlocfilehash: a7a01a3b1aab2ffa1850434928f4de3bce39bcd4
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="columnstore-indexes---overview"></a>Indici columnstore - Panoramica
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Gli *indici columnstore* rappresentano lo standard per l'archiviazione di tabelle dei fatti di data warehousing di grandi dimensioni e per l'esecuzione di query su queste tabelle. Grazie all'archiviazione dei dati basata su colonne, l'indice columnstore riesce a ottenere nel data warehouse un **miglioramento delle prestazioni delle query fino a 10 volte** rispetto all'archiviazione tradizionale orientata alle righe e una **compressione dei dati fino a 10 volte** rispetto alla dimensione dei dati non compressi. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]gli indici columnstore consentono l'analisi operativa, rendendo possibile l'esecuzione di analisi in tempo reale ad alte prestazioni su carichi di lavoro transazionali.  
  
 Scenari correlati:  
  
-   [Indici columnstore per il data warehousing](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)  
-   [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)  
  
## <a name="what-is-a-columnstore-index"></a>Che cos'è un indice columnstore?  
 L' *columnstore index* è una tecnologia per l'archiviazione, il recupero e la gestione dei dati utilizzando un formato di dati in colonna, detto columnstore.  
  
### <a name="key-terms-and-concepts"></a>Termini e concetti chiave  
 Di seguito sono definiti termini e concetti chiave associati agli indici columnstore.  
  
 columnstore  
 Un *indice columnstore* è costituito da dati organizzati logicamente in una tabella con righe e colonne e archiviati fisicamente in un formato di dati a colonne.  
  
 rowstore  
 Un *indice rowstore* è costituito da dati organizzati logicamente in una tabella con righe e colonne e archiviati fisicamente in un formato di dati a righe. È stata la modalità di archiviazione tradizionale per archiviare dati relazionali di tabella. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], rowstore indica la tabella in cui il formato di archiviazione dati sottostante è un heap, un indice cluster o una tabella ottimizzata per la memoria.  
  
> [!NOTE]  
> Quando si parla di indici columnstore, si usano i termini *rowstore* e *columnstore* per enfatizzare il formato per l'archiviazione dei dati.  
  
 rowgroup  
 Un *rowgroup* è un gruppo di righe che vengono compresse nel formato columnstore contemporaneamente. Un rowgroup contiene in genere il numero massimo di righe per rowgroup, pari a 1.048.576 righe.  
  
 Per garantire prestazioni elevate e un alto tasso di compressione, l'indice columnstore suddivide la tabella in gruppi di righe, dette rowgroup, quindi comprime ogni rowgroup per colonne. Il numero di righe nel rowgroup deve essere sufficientemente grande da migliorare il tasso di compressione e sufficientemente ridotto da poter trarre vantaggio dall'esecuzione delle operazioni in memoria.  
 segmento di colonna  
 Un *segmento di colonna* è una colonna di dati all'interno del rowgroup.  
  
-   Ogni rowgroup contiene un segmento di colonna per ogni colonna della tabella.  
-   Ogni segmento di colonna è compresso e archiviato su un supporto fisico.  
  
 ![Column segment](../../relational-databases/indexes/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")  
  
 indice columnstore cluster  
 Un *indice columnstore cluster* rappresenta l'archivio fisico per l'intera tabella.  
  
 ![Clustered Columnstore Index](../../relational-databases/indexes/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")  
  
 Per ridurre la frammentazione dei segmenti di colonna e migliorare le prestazioni, l'indice columnstore può archiviare temporaneamente alcuni dati in un indice cluster, denominato deltastore, e in un BTree di ID per le righe eliminate. Le operazioni deltastore sono gestite in modo automatico. Per tornare ai risultati della query corretti, l'indice columnstore cluster combina i risultati della query da columnstore e deltastore.  
  
 deltastore  
 Usato solo con indici columnstore cluster, un *deltastore* è un indice cluster che migliora la compressione e le prestazioni dei columnstore archiviando le righe finché il numero di queste non raggiunge una soglia specifica e spostandole quindi nel columnstore.  
  
 Durante un caricamento bulk di grandi dimensioni, la maggior parte delle righe viene direttamente indirizzata al columnstore senza passare per il deltastore. È possibile che alla fine del caricamento bulk il numero delle righe sia insufficiente a soddisfare le dimensioni minime di un rowgroup, pari a 102.400. In questo caso, le righe finali vengono indirizzate al deltastore anziché al columnstore. Per i caricamenti bulk di piccole dimensioni, con meno di 102.400 righe, tutte le righe passano direttamente al deltastore.  
  
 Quando il deltastore raggiunge il numero massimo di righe, viene chiuso. Un processo di motore di tuple controlla se sono presenti rowgroup chiusi. Quando trova il rowgroup chiuso, lo comprime e lo archivia nel columnstore.  
  
 indice columnstore non cluster  
 Un *indice columnstore non cluster* e un indice columnstore cluster funzionano allo stesso modo. La differenza è che un indice non cluster è un indice secondario creato per una tabella rowstore, mentre un indice columnstore cluster rappresenta l'archiviazione primaria per l'intera tabella.  
  
 L'indice non cluster contiene una copia totale o parziale delle righe e delle colonne della tabella sottostante. L'indice è definito sotto forma di una o più colonne della tabella e ha una condizione facoltativa che consente di filtrare le righe.  
  
 Un indice columnstore non cluster consente l'analisi operativa in tempo reale, durante la quale il carico di lavoro OLTP usa l'indice cluster sottostante, mentre l'analisi viene eseguita simultaneamente sull'indice columnstore. Per altre informazioni, vedere l' [articolo introduttivo sull'uso di columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
 esecuzione batch  
 L'*esecuzione batch* è un metodo di elaborazione delle query in base al quale le query elaborano più righe contemporaneamente. Le query sugli indici columnstore usano l'esecuzione in modalità batch, che migliora le prestazioni delle query in genere da 2 a 4 volte. L'esecuzione batch è strettamente integrata al formato di archiviazione columnstore, per il quale è ottimizzata. L'esecuzione in modalità batch talvolta è detta esecuzione basata su vettore o vettorizzata.  
  
##  <a name="benefits"></a> Perché usare un indice columnstore?  
 Un indice columnstore può garantire un livello di compressione dei dati molto elevato, in genere di 10 volte, riducendo in modo significativo i costi di archiviazione del data warehouse. Per l'analisi, gli indici columnstore offrono anche prestazioni decisamente migliori rispetto agli indici BTree e rappresentano il formato di archiviazione di dati preferito per i carichi di lavoro di analisi e data warehousing. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]è possibile usare gli indici columnstore per l'analisi in tempo reale del carico di lavoro operativo.  
  
 Ecco perché gli indici columnstore sono così rapidi:  
  
-   Le colonne memorizzano valori provenienti dallo stesso dominio. Si tratta in genere di valori simili, il che consente un tasso di compressione elevato. Ciò riduce al minimo o elimina completamente i colli di bottiglia di I/O all'interno del sistema, riducendo nello stesso tempo il footprint di memoria in modo significativo.  
  
-   Le frequenze di compressione elevate migliorano le prestazioni delle query utilizzando un footprint di memoria più piccolo. A loro volta, le prestazioni delle query costituiscono un miglioramento in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in quanto è possibile eseguire un numero maggiore di operazioni di dati e query in memoria.  
  
-   L'esecuzione batch migliora le prestazioni delle query, in genere, da 2 a 4 volte grazie all'elaborazione di più righe contemporaneamente.  
  
-   Le query spesso selezionano solo alcune colonne di una tabella, riducendo il totale delle operazioni di I/O su un supporto fisico.  
  
## <a name="when-should-i-use-a-columnstore-index"></a>Quando usare un indice columnstore?  
 Usi consigliati:  
  
-   Usare un indice columnstore cluster per archiviare tabelle dei fatti e tabelle di grandi dimensioni per i carichi di lavoro di data warehousing. Ciò migliora le prestazioni delle query e la compressione dei dati di un massimo di 10 volte. Vedere [Columnstore Indexes for Data Warehousing](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md).  
  
-   Usare un indice columnstore non cluster per eseguire l'analisi in tempo reale di un carico di lavoro OLTP. Vedere l' [articolo introduttivo sull'uso di columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md).  
  
### <a name="how-do-i-choose-between-a-rowstore-index-and-a-columnstore-index"></a>Come scegliere tra un indice rowstore e un indice columnstore?  
 Gli indici rowstore offrono prestazioni ottimali con le query che eseguono la ricerca di un valore specifico o all'interno di un intervallo di valori di piccole dimensioni. Usare gli indici rowstore con carichi di lavoro transazionali, poiché per i carichi di lavoro di questo tipo sono in genere necessarie ricerche all'interno delle tabelle anziché scansioni di queste.  
  
 Gli indici columnstore garantiscono prestazioni notevolmente elevate per le query analitiche su grandi quantità di dati, soprattutto per le tabelle di grandi dimensioni.  Usare gli indici columnstore per i carichi di lavoro di data warehousing e analisi, soprattutto sulle tabelle dei fatti, poiché in genere questi carichi di lavoro richiedono scansioni complete delle tabelle anziché ricerche all'interno di queste.  
  
### <a name="can-i-combine-rowstore-and-columnstore-on-the-same-table"></a>È possibile combinare indici rowstore e columnstore nella stessa tabella?  
 Sì. A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]è possibile creare un indice columnstore non cluster aggiornabile in una tabella rowstore. L'indice columnstore archivia una copia delle colonne selezionate. È quindi necessario spazio aggiuntivo, ma la compressione applicata è in media di 10 volte. In questo modo è possibile eseguire allo stesso tempo analisi sull'indice columnstore e transazioni sull'indice rowstore. Il columnstore viene aggiornato quando i dati nella tabella rowstore vengono modificati. In questo modo entrambi gli indici possono usare gli stessi dati.  
  
 A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]è possibile avere uno o più indici rowstore non cluster per un indice columnstore. Ciò consente di eseguire ricerche efficienti all'interno delle tabelle del columnstore sottostante. Sono disponibili anche altre opzioni. È possibile, ad esempio, applicare un vincolo di chiave primaria tramite un vincolo UNIQUE nella tabella rowstore. Dato che non è possibile inserire un valore non univoco nella tabella rowstore, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non può inserire il valore nel columnstore.  
  
## <a name="metadata"></a>Metadati  
 Tutte le colonne di un indice columnstore vengono archiviate nei metadati come colonne incluse. L'indice columnstore non contiene colonne chiave.  

|||
|-|-|  
|[sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)|[sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)|  
|[sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)|[sys.internal_partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-internal-partitions-transact-sql.md)|  
|[sys.column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-segments-transact-sql.md)|[sys.column_store_dictionaries &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)|  
|[sys.column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql.md)|[sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)|  
|[sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)|[sys.dm_column_store_object_pool &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-column-store-object-pool-transact-sql.md)|  
|[sys.dm_db_column_store_row_group_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-operational-stats-transact-sql.md)|[sys.dm_db_index_operational_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql.md)|  
|[sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)||  
  
## <a name="related-tasks"></a>Related Tasks  
 Tutte le tabelle relazionali, se non specificate come indice columnstore cluster, usano rowstore come formato dei dati sottostanti. `CREATE TABLE` crea una tabella rowstore, a meno che non si specifichi l'opzione `WITH CLUSTERED COLUMNSTORE INDEX`.  
  
 Quando si crea una tabella con l'istruzione `CREATE TABLE` è possibile creare la tabella come columnstore specificando l'opzione `WITH CLUSTERED COLUMNSTORE INDEX`. Se si ha già una tabella rowstore e si vuole convertirla in una tabella columnstore, è possibile usare l'istruzione `CREATE COLUMNSTORE INDEX`.  
  
|Attività|Argomenti di riferimento|Note|  
|----------|----------------------|-----------|  
|Creare una tabella come columnstore.|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]è possibile creare la tabella come indice columnstore cluster. Non è necessario creare prima una tabella rowstore e quindi convertirla in columnstore.|  
|Creare una tabella in memoria con un indice columnstore.|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] è possibile creare una tabella in memoria ottimizzata con un indice columnstore. L'indice columnstore può anche essere aggiunto dopo aver creato la tabella, usando la sintassi ALTER TABLE ADD INDEX.|  
|Convertire una tabella rowstore in un columnstore.|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Convertire un heap o un albero binario esistente o in un columnstore. Gli esempi illustrano come gestire gli indici esistenti e il nome dell'indice quando si esegue questa conversione.|  
|Convertire una tabella columnstore in un rowstore.|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Di solito non è necessario eseguire questa conversione, ma talvolta potrebbe presentarsene la necessità. Gli esempi illustrano come convertire un columnstore in un heap o in un indice cluster.|  
|Creare un indice columnstore per una tabella rowstore.|[CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)|Una tabella rowstore può avere un solo indice columnstore.  A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]l'indice columnstore può avere una condizione di filtro. Gli esempi illustrano la sintassi di base.|  
|Creare indici ad alte prestazioni per l'analisi operativa.|[Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)|Descrive come creare indici columnstore e BTree complementari in modo che le query OLTP usino gli indici BTree e le query di analisi usino gli indici columnstore.|  
|Creare indici columnstore efficienti per il data warehousing.|[Indici columnstore per il data warehousing](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|Descrive come usare gli indici BTree con le tabelle columnstore per creare query di data warehousing ad alte prestazioni.|  
|Usare un indice BTree per imporre un vincolo di chiave primaria per un indice columnstore.|[Indici columnstore per il data warehousing](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)|Illustra come combinare indici BTree e columnstore per imporre vincoli di chiave primaria per l'indice columnstore.|  
|Rimuovere un indice columnstore|[DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)|Per rimuovere un indice columnstore si usa la sintassi DROP INDEX standard usata dagli indici BTree. La rimozione di un indice columnstore cluster converte la tabella columnstore in un heap.|  
|Eliminare una riga da un indice columnstore|[DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)|Usare [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md) per eliminare una riga.<br /><br /> Riga**columnstore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrassegna la riga come eliminata logicamente ma recupera lo spazio di archiviazione fisico della riga solo dopo che l'indice è stato ricompilato.<br /><br /> Riga**deltastore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] elimina la riga logicamente e fisicamente.|  
|Aggiornare una riga nell'indice columnstore|[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)|Usare [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md) per aggiornare una ruga.<br /><br /> Riga**columnstore** :  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contrassegna la riga come eliminata logicamente e quindi inserisce la riga aggiornata nel deltastore.<br /><br /> Riga**deltastore** : [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aggiorna la riga nel deltastore.|  
|Caricare dati in un indice columnstore|[Caricamento dati di indici columnstore](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)||  
|Forzare il passaggio di tutte le righe del deltastore nel columnstore.|[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md) ... REBUILD<br /><br /> [Deframmentazione degli indici columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)|ALTER INDEX con l'opzione REBUILD forza il passaggio di tutte le righe nel columnstore.|  
|Deframmentare un indice columnstore|[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)|ALTER INDEX … REORGANIZE consente di deframmentare indici columnstore online.|  
|Unire tabelle con indici columnstore.|[MERGE &#40;Transact-SQL&#41;](../../t-sql/statements/merge-transact-sql.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Caricamento dati di indici columnstore](~/relational-databases/indexes/columnstore-indexes-data-loading-guidance.md)   
 [Riepilogo delle funzionalità con versione degli indici columnstore](~/relational-databases/indexes/columnstore-indexes-what-s-new.md)   
 [Prestazioni delle query per gli indici columnstore](~/relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [Introduzione a columnstore per l'analisi operativa in tempo reale](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [Indici columnstore per il data warehousing](~/relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
 [Deframmentazione degli indici columnstore](~/relational-databases/indexes/columnstore-indexes-defragmentation.md)   
 [Guida per la progettazione di indici di SQL Server](../../relational-databases/sql-server-index-design-guide.md)   
 [Architettura degli indici columnstore](../../relational-databases/sql-server-index-design-guide.md#columnstore_index)   
  
  





