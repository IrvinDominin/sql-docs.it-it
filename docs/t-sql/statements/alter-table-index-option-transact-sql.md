---
title: index_option (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/08/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- index_option
ms.assetid: 8a14f12d-2fbf-4036-b8b2-8db3354e0eb7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 646b46501abd345a35c0e90547391e5181105a00
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-table-indexoption-transact-sql"></a>ALTER TABLE index_option (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Specifica un set di opzioni che possono essere applicati a un indice che fa parte di una definizione di vincolo creata tramite [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
{   
    PAD_INDEX = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | IGNORE_DUP_KEY = { ON | OFF }  
  | STATISTICS_NORECOMPUTE = { ON | OFF }  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | SORT_IN_TEMPDB = { ON | OFF }   
  | ONLINE = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = { NONE |ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE }  
      [ ON PARTITIONS ( { <partition_number_expression> | <range> }   
      [ , ...n ] ) ]  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<range> ::=   
<partition_number_expression> TO <partition_number_expression>  
  
<single_partition_rebuild__option> ::=  
{  
    SORT_IN_TEMPDB = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
  | DATA_COMPRESSION = {NONE | ROW | PAGE | COLUMNSTORE | COLUMNSTORE_ARCHIVE } }  
  | ONLINE = { ON [ ( <low_priority_lock_wait> ) ] | OFF }  
}  
  
<low_priority_lock_wait>::=  
{  
    WAIT_AT_LOW_PRIORITY ( MAX_DURATION = <time> [ MINUTES ] ,   
                           ABORT_AFTER_WAIT = { NONE | SELF | BLOCKERS } )   
}  
```  
  
## <a name="arguments"></a>Argomenti  
 PAD_INDEX  **=**  {ON | **OFF** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica il riempimento dell'indice. Il valore predefinito è OFF.  
  
 ON  
 La percentuale di spazio disponibile specificata in FILLFACTOR viene applicata alle pagine di livello intermedio dell'indice.  
  
 DISATTIVARE o *fillfactor* non è specificato  
 Le pagine di livello intermedio vengono riempite quasi completamente, ma viene lasciato spazio sufficiente per almeno una riga avente le dimensioni massime consentite dall'indice, in base al set di chiavi nelle pagine intermedie.  
  
 Fattore di riempimento  **=**  *fattore di riempimento*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica una percentuale indicante il livello di riempimento del livello foglia di ogni pagina di indice applicato dal [!INCLUDE[ssDE](../../includes/ssde-md.md)] durante la creazione o la modifica dell'indice. Il valore specificato deve essere un valore integer compreso tra 1 e 100. Il valore predefinito è 0.  
  
> [!NOTE]  
>  I valori 0 e 100 relativi al fattore di riempimento sono equivalenti.  
  
 IGNORE_DUP_KEY  **=**  {ON | **OFF** }  
 Specifica l'errore restituito quando un'operazione di inserimento tenta di inserire valori di chiave duplicati in un indice univoco. L'opzione IGNORE_DUP_KEY viene applicata solo alle operazioni di inserimento eseguite dopo la creazione o la ricompilazione dell'indice. L'opzione non ha alcun effetto quando si esegue [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md), [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md), o [aggiornamento](../../t-sql/queries/update-transact-sql.md). Il valore predefinito è OFF.  
  
 ON  
 Un messaggio di avviso si verifica quando i valori di chiave duplicati vengono inseriti in un indice univoco. Esito negativo solo le righe che violano il vincolo di univocità.  
  
 OFF  
 Un messaggio di errore si verifica quando i valori di chiave duplicati vengono inseriti in un indice univoco. Viene eseguito il rollback dell'intera operazione INSERT.  
  
 Impossibile impostare IGNORE_DUP_KEY su ON per gli indici creati in una vista, gli indici non univoci, gli indici XML, gli indici spaziali e indici filtrati.  
  
 Per visualizzare IGNORE_DUP_KEY, utilizzare [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).  
  
 Per quanto riguarda la sintassi compatibile con le versioni precedenti, WITH IGNORE_DUP_KEY equivale a WITH IGNORE_DUP_KEY = ON.  
  
 STATISTICS_NORECOMPUTE  **=**  {ON | **OFF** }  
 Specifica se vengono ricalcolate le statistiche. Il valore predefinito è OFF.  
  
 ON  
 Le statistiche non aggiornate non vengono ricalcolate automaticamente.  
  
 OFF  
 Abilita l'aggiornamento automatico delle statistiche.  
  
 ALLOW_ROW_LOCKS  **=**  { **ON** | OFF}  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica se sono consentiti blocchi di riga. Il valore predefinito è ON.  
  
 ON  
 I blocchi di riga sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga.  
  
 OFF  
 I blocchi di riga non vengono utilizzati.  
  
 ALLOW_PAGE_LOCKS  **=**  { **ON** | OFF}  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica se sono consentiti blocchi a livello di pagina. Il valore predefinito è ON.  
  
 ON  
 I blocchi a livello di pagina sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina.  
  
 OFF  
 I blocchi a livello di pagina non vengono utilizzati.  
  
 L'OPZIONE SORT_IN_TEMPDB  **=**  {ON | **OFF** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica se archiviare i risultati dell'ordinamento in **tempdb**. Il valore predefinito è OFF.  
  
 ON  
 I risultati intermedi dell'ordinamento utilizzati per compilare l'indice vengono archiviati **tempdb**. Questo potrebbe ridurre il tempo necessario per creare un indice se **tempdb** si trova in un set di dischi diverso rispetto al database utente. La quantità di spazio su disco utilizzata durante la compilazione dell'indice sarà tuttavia maggiore.  
  
 OFF  
 I risultati intermedi dell'ordinamento vengono archiviati nello stesso database dell'indice.  
  
 ONLINE  **=**  {ON | **OFF** }  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica se le tabelle sottostanti e gli indici associati sono disponibili per le query e la modifica dei dati durante l'operazione sugli indici. Il valore predefinito è OFF. L'opzione REBUILD può essere eseguita come operazione ONLINE.  
  
> [!NOTE]  
>  Non è possibile creare online indici non cluster univoci, tra cui gli indici creati a causa di un vincolo UNIQUE o PRIMARY KEY.  
  
 ON  
 I blocchi di tabella a lungo termine non vengono mantenuti per la durata dell'operazione sugli indici. Durante la fase principale dell'operazione viene mantenuto solo un blocco preventivo condiviso (IS, Intent Shared) sulla tabella di origine, in modo da consentire l'esecuzione di query o l'aggiornamento della tabella sottostante e degli indici. All'inizio dell'operazione viene mantenuto un blocco condiviso (S) sull'oggetto di origine per un periodo molto breve. Al termine dell'operazione, per un breve periodo viene acquisito un blocco condiviso (S) sull'origine, in caso di creazione di un indice non cluster. In caso di creazione o di eliminazione di un indice cluster online o di ricompilazione di un indice cluster o non cluster, viene acquisito un blocco di modifica dello schema (SCH-M). Sebbene i blocchi sull'indice online siano blocchi di metadati brevi, soprattutto il blocco Sch-M deve attendere il completamento di tutte le transazioni bloccanti su questa tabella. Durante il tempo di attesa il blocco Sch-M impedisce tutte le altre transazioni in attesa dietro il blocco stesso per l'accesso alla stessa tabella. L'opzione ONLINE non può essere impostata su ON quando viene creato un indice per una tabella temporanea locale.  
  
> [!NOTE]  
>  Ricompilazione dell'indice online è possibile impostare il *low_priority_lock_wait* opzioni descritte più avanti in questa sezione. *low_priority_lock_wait* gestisce priorità dei blocchi Sch-M e S durante la ricompilazione dell'indice online.  
  
 OFF  
 I blocchi di tabella vengono applicati per la durata dell'operazione sugli indici. Il blocco impedisce agli utenti di accedere alla tabella sottostante per la durata dell'operazione. Un'operazione sugli indici offline che crea, ricompila o elimina un indice cluster oppure ricompila o elimina un indice non cluster acquisisce un blocco di modifica dello schema (SCH-M) sulla tabella. Il blocco impedisce agli utenti di accedere alla tabella sottostante per la durata dell'operazione. Un'operazione sugli indici offline che crea un indice non cluster acquisisce un blocco condiviso (S) sulla tabella. Tale blocco impedisce l'aggiornamento della tabella sottostante ma consente operazioni di lettura, ad esempio l'esecuzione di istruzioni SELECT.  
  
 Per ulteriori informazioni, vedere [come funzionano le operazioni di indice Online](../../relational-databases/indexes/how-online-index-operations-work.md).  
  
> [!NOTE]  
>  Le operazioni sugli indici online sono disponibili solo in alcune edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 MAXDOP  **=**  *max_degree_of_parallelism*  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Esegue l'override di **massimo grado di parallelismo** opzione di configurazione per la durata dell'operazione sull'indice. Per altre informazioni, vedere [Configurare l'opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md). Utilizzare MAXDOP per limitare il numero di processori utilizzati durante l'esecuzione di un piano parallelo. Il valore massimo è 64 processori.  
  
 *max_degree_of_parallelism* può essere:  
  
 - 1 - disattiva la generazione di piani paralleli.  
 - \>1 - limita il numero massimo di processori utilizzati in un'operazione parallela sugli indici per il numero specificato.  
 - 0 (impostazione predefinita) - corrisponde al numero effettivo di processori o meno in base al carico di lavoro di sistema corrente.  
  
 Per altre informazioni, vedere [Configurazione di operazioni parallele sugli indici](../../relational-databases/indexes/configure-parallel-index-operations.md).  
  
> [!NOTE]  
>  Operazioni parallele sugli indici non sono disponibili in ogni edizione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 DATA_COMPRESSION  
 **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica l'opzione di compressione dei dati per la tabella, il numero di partizione o l'intervallo di partizioni specificato. Sono disponibili le opzioni seguenti:  
  
 NONE  
 La tabella o le partizioni specificate non vengono compresse. Si applica solo alle tabelle rowstore, non si applica alle tabelle columnstore.  
  
 ROW  
 La tabella o le partizioni specificate vengono compresse utilizzando la compressione di riga. Si applica solo alle tabelle rowstore, non si applica alle tabelle columnstore.  
  
 PAGE  
 La tabella o le partizioni specificate vengono compresse utilizzando la compressione di pagina. Si applica solo alle tabelle rowstore, non si applica alle tabelle columnstore.  
  
 COLUMNSTORE  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo alle tabelle columnstore. Con COLUMNSTORE si specifica di decomprimere una partizione compressa con l'opzione COLUMNSTORE_ARCHIVE. Quando il ripristino dei dati, l'indice COLUMNSTORE continua a essere compressi con la compressione columnstore utilizzata per tutte le tabelle columnstore.  
  
 COLUMNSTORE_ARCHIVE  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Si applica solo alle tabelle columnstore, ovvero tabelle archiviate con un indice columnstore cluster. COLUMNSTORE_ARCHIVE ulteriormente comprime la partizione specificata a una dimensione inferiore. Può essere utilizzata per l'archiviazione o in altre situazioni in cui sono richieste dimensioni di archiviazione inferiori ed è possibile concedere più tempo per l'archiviazione e il recupero.  
  
 Per ulteriori informazioni sulla compressione, vedere [la compressione dei dati](../../relational-databases/data-compression/data-compression.md).  
  
PARTIZIONI **(** { \<partition_number_expression > | \<intervallo >} [ **,**...  *n*  ] **)** **Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Specifica le partizioni alle quali si applica l'impostazione DATA_COMPRESSION. Se la tabella non è partizionata, l'argomento ON PARTITIONS genererà un errore. Se la clausola ON PARTITIONS non viene specificata, l'opzione DATA_COMPRESSION si applica a tutte le partizioni di una tabella partizionata.  
  
\<partition_number_expression > possono essere specificati nei modi seguenti:  
  
-   Fornire il numero di una partizione, ad esempio ON PARTITIONS (2).  
-   Fornire i numeri di partizione per più partizioni singole separati da virgole, ad esempio ON PARTITIONS (1, 5).  
-   Fornire sia intervalli, sia singole partizioni, ad esempio ON PARTITIONS (2, 4, 6 TO 8).  
  
\<intervallo > possono essere specificati come numeri di partizione separati dalla parola TO, ad esempio: ON PARTITIONS (6 TO 8).  
  
 Per impostare tipi diversi di compressione dei dati per partizioni diverse, specificare più volte l'opzione DATA_COMPRESSION, ad esempio:  
  
```sql  
--For rowstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = NONE ON PARTITIONS (1),   
DATA_COMPRESSION = ROW ON PARTITIONS (2, 4, 6 TO 8),   
DATA_COMPRESSION = PAGE ON PARTITIONS (3, 5)  
)  
  
--For columnstore tables  
REBUILD WITH   
(  
DATA_COMPRESSION = COLUMNSTORE ON PARTITIONS (1, 3, 5),   
DATA_COMPRESSION = COLUMNSTORE_ARCHIVE ON PARTITIONS (2, 4, 6 TO 8)  
)  
```  
  
**\<single_partition_rebuild__option >**  
 Nella maggior parte dei casi, la ricompilazione di un indice determina la ricompilazione di tutte le partizioni di un indice partizionato. Le opzioni seguenti, in caso di applicazione a una partizione singola, non ricompilano tutte le partizioni.  
  
-   SORT_IN_TEMPDB  
-   MAXDOP  
-   DATA_COMPRESSION  
  
**low_priority_lock_wait**  
 **Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Oggetto **COMMUTATORE** o ricompilazione dell'indice online viene completata non appena non sono presenti operazioni di blocco per questa tabella. *WAIT_AT_LOW_PRIORITY* indica che, se il **COMMUTATORE** o Impossibile completare l'operazione di ricompilazione indice online immediatamente, è in attesa. L'operazione contiene blocchi con priorità bassa, consentendo di altre operazioni che mantengono blocchi in conflitto con l'istruzione DDL di continuare. L'omissione di **WAIT AT LOW PRIORITY** equivale all'opzione `WAIT_AT_LOW_PRIORITY ( MAX_DURATION = 0 minutes, ABORT_AFTER_WAIT = NONE)`.  
  
MAX_DURATION = *ora* [**minuti** ]  
 Il tempo (valore intero specificato in minuti) che il **COMMUTATORE** o attese di blocco di ricompilazione di indici online che deve essere acquisito, durante l'esecuzione del comando DDL. L'operazione SWITCH o di ricompilazione dell'indice online tenta il completamento immediato. Se l'operazione è bloccata per la **MAX_DURATION** tempo, uno del **ABORT_AFTER_WAIT** azioni viene eseguita. **MAX_DURATION** ora è sempre espresso in minuti e la parola **minuti** può essere omesso.  
  
ABORT_AFTER_WAIT = [**NONE** | **SELF** | **BLOCCHI** }]  
 Nessuno  
 Continua la **COMMUTATORE** o senza modificare la priorità dei blocchi (utilizzando la priorità normale) operazione di ricompilazione dell'indice online.  
  
SELF  
 Chiusura di **COMMUTATORE** o operazione DDL di ricompilazione indice online attualmente in esecuzione senza eseguire alcuna azione.  
  
BLOCKERS  
 Termina tutte le transazioni utente che attualmente bloccano il **COMMUTATORE** o di operazione DDL di ricompilazione in modo da poter continuare l'operazione di indice online.  
 BLOCCHI richiede il **l'autorizzazione ALTER ANY CONNECTION** autorizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 Per una descrizione completa delle opzioni dell'indice, vedere [CREATE INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [column_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-column-constraint-transact-sql.md)   
 [computed_column_definition &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-computed-column-definition-transact-sql.md)   
 [table_constraint &#40; Transact-SQL &#41;](../../t-sql/statements/alter-table-table-constraint-transact-sql.md)  
  
 
