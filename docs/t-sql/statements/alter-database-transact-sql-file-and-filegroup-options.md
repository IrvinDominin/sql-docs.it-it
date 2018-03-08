---
title: ALTER DATABASE opzioni File e Filegroup (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD FILE
- ADD_FILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting files
- removing files
- deleting filegroups
- file modifications [SQL Server]
- databases [SQL Server], size
- relocating files
- databases [SQL Server], modifying
- file additions [SQL Server], ALTER DATABASE
- file moving [SQL Server]
- default filegroups
- ALTER DATABASE statement, files and filegroups
- initializing files [SQL Server]
- database files [SQL Server]
- moving files
- filegroups [SQL Server], deleting
- adding filegroups
- adding files
- database filegroups [SQL Server]
- adding log files
- modifying files
- filegroups [SQL Server], adding
- file initialization [SQL Server]
- files [SQL Server], deleting
- files [SQL Server], adding
- databases [SQL Server], moving
ms.assetid: 1f635762-f7aa-4241-9b7a-b51b22292b07
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 826b8a5abb14ee677f89f1c77956215ec72f90c6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="alter-database-transact-sql-file-and-filegroup-options"></a>File e Filegroup opzioni ALTER DATABASE (Transact-SQL) 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifica i file e i filegroup associati al database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Consente inoltre di aggiungere file e filegroup a un database, di rimuoverli da esso e di modificare gli attributi di un database o i relativi file e filegroup. Per altre opzioni di ALTER DATABASE, vedere [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
ALTER DATABASE database_name   
{  
    <add_or_modify_files>  
  | <add_or_modify_filegroups>  
}  
[;]  
  
<add_or_modify_files>::=  
{  
    ADD FILE <filespec> [ ,...n ]   
        [ TO FILEGROUP { filegroup_name } ]  
  | ADD LOG FILE <filespec> [ ,...n ]   
  | REMOVE FILE logical_file_name   
  | MODIFY FILE <filespec>  
}  
  
<filespec>::=   
(  
    NAME = logical_file_name    
    [ , NEWNAME = new_logical_name ]   
    [ , FILENAME = {'os_file_name' | 'filestream_path' | 'memory_optimized_data_path' } ]   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB| % ] ]   
    [ , OFFLINE ]  
)   
  
<add_or_modify_filegroups>::=  
{  
    | ADD FILEGROUP filegroup_name   
        [ CONTAINS FILESTREAM | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    | REMOVE FILEGROUP filegroup_name   
    | MODIFY FILEGROUP filegroup_name  
        { <filegroup_updatability_option>  
        | DEFAULT  
        | NAME = new_filegroup_name   
        | { AUTOGROW_SINGLE_FILE | AUTOGROW_ALL_FILES }  
        }  
}  
<filegroup_updatability_option>::=  
{  
    { READONLY | READWRITE }   
    | { READ_ONLY | READ_WRITE }  
}  
  
```  
  
## <a name="arguments"></a>Argomenti  
**\<add_or_modify_files >:: =**
  
 Specifica i file da aggiungere, rimuovere o modificare.  
  
 *database_name*  
 Nome del database da modificare.  
  
 ADD FILE  
 Aggiunge un file al database.  
  
 AL FILEGROUP { *filegroup_name* }  
 Specifica il filegroup in cui aggiungere il file specificato. Per visualizzare i filegroup correnti e il filegroup è quello predefinito corrente, utilizzare il [Sys. FileGroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md) vista del catalogo.  
  
 ADD LOG FILE  
 Aggiunge un file di log al database specificato.  
  
 REMOVE FILE *nome_file_logico*  
 Rimuove la descrizione del file logico da un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ed elimina il file fisico. Il file può essere rimosso solo se è vuoto.  
  
 *nome_file_logico*  
 Nome logico utilizzato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per fare riferimento al file.  
  
> [!WARNING]  
> Rimozione di un file di database con FILE_SNAPSHOT associati backup avrà esito positivo, ma non verranno eliminati tutti gli snapshot associati per evitare di invalidare i backup che fanno riferimento al file di database. Il file verrà troncato, ma non verranno fisicamente eliminato per mantenere i backup FILE_SNAPSHOT intatto. Per altre informazioni, vedere [Backup e ripristino di SQL Server con il servizio di archiviazione BLOB di Microsoft Azure](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md). **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).  
  
 MODIFY FILE  
 Specifica il file da modificare. Un solo \<filespec > proprietà può essere modificata alla volta. NOME deve sempre essere specificato nella \<filespec > per identificare il file da modificare. Se si specifica l'opzione SIZE, le nuove dimensioni del file devono essere superiori a quelle correnti.  
  
 Per modificare il nome logico di un file di dati o di un file di log, specificare il nome del file logico da rinominare nella clausola `NAME` e specificare il nuovo nome logico per il file nella clausola `NEWNAME`. Ad esempio  
  
```  
MODIFY FILE ( NAME = logical_file_name, NEWNAME = new_logical_name )   
```  
  
 Per spostare un file di dati o un file di log in una nuova posizione, specificare il nome di file logico corrente nella clausola `NAME` e specificare il nuovo percorso e il nome del file nel sistema operativo nella clausola `FILENAME`. Ad esempio  
  
```  
MODIFY FILE ( NAME = logical_file_name, FILENAME = ' new_path/os_file_name ' )  
```  
  
 Per lo spostamento di un catalogo full-text, specificare solo il nuovo percorso nella clausola FILENAME, senza indicare il nome del file nel sistema operativo.  
  
 Per ulteriori informazioni, vedere [spostare i file di Database](../../relational-databases/databases/move-database-files.md).  
  
 Per un filegroup FILESTREAM, NAME può essere modificato online. Sebbene FILENAME possa essere modificato online, la modifica non diventa effettiva fino a quando il contenitore non viene rilocato fisicamente e il server non viene arrestato e successivamente riavviato.  
  
 È possibile impostare un file FILESTREAM su OFFLINE. Quando un file FILESTREAM è offline, il filegroup padre sarà contrassegnato internamente come offline. Di conseguenza, ogni accesso a dati FILESTREAM all'interno del filegroup specifico avrà esito negativo.  
  
> [!NOTE]  
>  \<add_or_modify_files > opzioni non sono disponibili in un Database indipendente.
  
 **\<filespec >:: =**  
  
 Controlla le proprietà del file.  
  
 NOME *nome_file_logico*  
 Specifica il nome logico del file.  
  
 *nome_file_logico*  
 Nome logico utilizzato in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per fare riferimento al file.  
  
 NEWNAME *new_logical_file_name*  
 Specifica un nuovo nome logico per il file.  
  
 *new_logical_file_name*  
 Nome con cui sostituire il nome di file logico esistente. Il nome deve essere univoco all'interno del database e conforme alle regole per [identificatori](../../relational-databases/databases/database-identifiers.md). Il nome può essere costituito da una costante per valori di carattere o Unicode, da un identificatore regolare o da un identificatore delimitato.  
  
 Nome del file { **'***os_file_name***'** | **'***filestream_path* **'** | **'***memory_optimized_data_path***'**}  
 Specifica il nome del file (fisico) del sistema operativo.  
  
 ' *os_file_name* '  
 Per un filegroup standard (ROWS), questo è il percorso e il nome di file utilizzato dal sistema operativo al momento della creazione del file. Il file deve trovarsi nel server in cui è installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il percorso specificato deve essere esistente prima di eseguire l'istruzione ALTER DATABASE.  
  
 Non è possibile impostare i parametri SIZE, MAXSIZE e FILEGROWTH se è specificato un percorso UNC per il file.  
  
> [!NOTE]  
> Database di sistema non possono trovarsi nella directory di condivisione UNC.  
  
 I file di dati non dovrebbero essere memorizzati in file system compressi, a meno che tali file non siano file secondari di sola lettura o il database non sia di sola lettura. I file di log non devono mai essere archiviati in file system compressi.  
  
 Se il file si trova in una partizione non elaborata, *os_file_name* deve specificare solo la lettera di unità di una partizione non elaborata esistente. In ogni partizione non formattata è possibile inserire un solo file.  
  
 **'** *filestream_path* **'**  
 Per un filegroup FILESTREAM, FILENAME si riferisce a un percorso in cui verrà archiviato FILESTREAM. È necessario che il percorso fino all'ultima cartella esista già, mentre l'ultima cartella non deve essere presente. Se, ad esempio, si specifica il percorso C:\MyFiles\MyFilestreamData, C:\MyFiles deve esistere già prima di eseguire ALTER DATABASE, mentre la cartella MyFilestreamData non deve essere presente.  
  
 Le proprietà SIZE e FILEGROWTH non si applicano a un filegroup FILESTREAM.  
  
 **'** *memory_optimized_data_path* **'**  
 Per un filegroup ottimizzato per la memoria, FILENAME fa riferimento a un percorso in cui verranno archiviati dati ottimizzati per la memoria. È necessario che il percorso fino all'ultima cartella esista già, mentre l'ultima cartella non deve essere presente. Se, ad esempio, si specifica il percorso C:\MyFiles\MyData, C:\MyFiles deve esistere già prima di eseguire ALTER DATABASE, mentre la cartella MyData non deve essere presente.  
  
 Il filegroup e il file (`<filespec>`) devono essere creati nella stessa istruzione.  
  
 Le proprietà SIZE, MAXSIZE e FILEGROWTH non si applicano a un filegroup ottimizzato per la memoria.  
  
 DIMENSIONI *dimensioni*  
 Specifica le dimensioni del file. SIZE non si applica a filegroup FILESTREAM.  
  
 *size*  
 Dimensioni del file.  
  
 Quando viene specificato con ADD FILE *dimensioni* è la dimensione iniziale per il file. Quando viene specificato con MODIFY FILE, *dimensioni* è la nuova dimensione per il file e deve essere maggiore delle dimensioni di file corrente.  
  
 Quando *dimensioni* non viene fornito per il file primario, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza le dimensioni del file primario di **modello** database. Quando viene specificato un file di dati secondario o un file di log, ma *dimensioni* non è specificato per il file, il [!INCLUDE[ssDE](../../includes/ssde-md.md)] rende il file di 1 MB.  
  
 È possibile utilizzare i suffissi KB, MB, GB e TB per indicare kilobyte, megabyte, gigabyte e terabyte. Il valore predefinito è MB. Specificare un numero intero, ovvero non includere decimali. Se si desidera specificare una frazione di megabyte, convertire il valore in kilobyte moltiplicando il numero per 1024. Ad esempio, specificare 1536 KB anziché 1,5 MB (1,5 x 1024 = 1536).  
  
 MAXSIZE { *max_size*| UNLIMITED}  
 Specifica le dimensioni massime consentite per l'aumento di dimensioni del file.  
  
 *max_size*  
 Dimensioni massime del file. È possibile utilizzare i suffissi KB, MB, GB e TB per indicare kilobyte, megabyte, gigabyte e terabyte. Il valore predefinito è MB. Specificare un numero intero, ovvero non includere decimali. Se *max_size* non viene specificato, le dimensioni del file aumentano fino a quando il disco è pieno.  
  
 UNLIMITED  
 Specifica che le dimensioni del file aumentano fino a quando il disco risulta pieno. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un file di log specificato con aumento delle dimensioni illimitato può raggiungere una dimensione massima di 2 TB, mentre un file di dati può raggiungere una dimensione massima di 16 TB. Non vi sono dimensioni massime se questa opzione viene specificata per un contenitore FILESTREAM, il quale continua a crescere finché il disco non è pieno.  
  
 FILEGROWTH *growth_increment*  
 Specifica l'incremento automatico per l'aumento delle dimensioni del file. Il valore impostato per il parametro FILEGROWTH di un file non può essere superiore al valore del parametro MAXSIZE. FILEGROWTH non si applica a filegroup FILESTREAM.  
  
 *growth_increment*  
 Quantità di spazio aggiunta al file ogni volta che è necessario spazio aggiuntivo.  
  
 È possibile specificare il valore in megabyte (MB), kilobyte (KB), gigabyte (GB) o terabyte (TB) oppure in forma di percentuale (%). Se si specifica un valore senza il suffisso MB, KB o %, il suffisso predefinito è MB. Se si utilizza il suffisso %, l'incremento corrisponde alla percentuale delle dimensioni del file specificata quando si verifica l'incremento. Le dimensioni specificate vengono arrotondate al blocco di 64 KB più prossimo.  
  
 Il valore 0 indica che l'aumento automatico delle dimensioni è disattivato e non è consentita l'allocazione di spazio aggiuntivo.  
  
 Se FILEGROWTH viene omesso, i valori predefiniti sono:  
  
|Versione|Valori predefiniti|  
|-------------|--------------------|  
|A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|Dati 64 MB. File di log 64 MB.|  
|A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Dati 1 MB. File di log % 10.|  
|Nelle versioni precedenti a[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|Dati del 10%. File di log % 10.|  
  
 OFFLINE  
 Imposta il file offline e rende inaccessibili tutti gli oggetti nel filegroup.  
  
> [!CAUTION]  
>  Utilizzare questa opzione solo quando il file è danneggiato e non è possibile ripristinarlo. Un file impostato su OFFLINE può essere riportato online solo tramite il ripristino del file dal backup. Per altre informazioni sul ripristino di un singolo file, vedere [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).  
  
> [!NOTE]  
> \<filespec > opzioni non sono disponibili in un Database indipendente.  
  
 **\<add_or_modify_filegroups >:: =**  
  
 Aggiunge, modifica o rimuove un filegroup nel database.  
  
 Aggiungi FILEGROUP *filegroup_name*  
 Aggiunge un filegroup nel database.  
  
 CONTAINS FILESTREAM  
 Specifica che tramite il filegroup vengono archiviati oggetti binari di grandi dimensioni (BLOB) nel file system.  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Specifica che il filegroup archivia i dati con ottimizzazione per la memoria nel file system. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md). È ammesso un solo filegroup MEMORY_OPTIMIZED_DATA per database. Per la creazione di tabelle con ottimizzazione per la memoria, il filegroup non può essere vuoto. Deve essere presente almeno un file. *filegroup_name* fa riferimento a un percorso. È necessario che il percorso fino all'ultima cartella esista già, mentre l'ultima cartella non deve essere presente.  
  
 Nell'esempio seguente viene creato un filegroup che viene aggiunto a un database denominato xtp_db, quindi viene aggiunto un file al filegroup. Nel filegroup vengono archiviati i dati memory_optimized.  
  
```sql  
ALTER DATABASE xtp_db ADD FILEGROUP xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA;  
GO  
ALTER DATABASE xtp_db ADD FILE (NAME='xtp_mod', FILENAME='d:\data\xtp_mod') TO FILEGROUP xtp_fg;  
```  
  
 RIMUOVERE FILEGROUP *filegroup_name*  
 Rimuove un filegroup dal database. Il filegroup può essere rimosso solo se è vuoto. Rimuove tutti i file a partire dal filegroup. Per ulteriori informazioni, vedere "REMOVE FILE *nome_file_logico*," più indietro in questo argomento.  
  
> [!NOTE]  
> A meno che il Garbage Collector per FILESTREAM non abbia rimosso tutti i file da un contenitore FILESTREAM, l'operazione ALTER DATABASE REMOVE FILE per rimuovere un contenitore FILESTREAM avrà esito negativo e verrà restituito un errore. Vedere la sezione relativa alla rimozione del contenitore FILESTREAM in "Osservazioni" di seguito in questo argomento.  
  
Modifica FILEGROUP *filegroup_name* { \<filegroup_updatability_option > | PREDEFINITO | NOME  **=**  *new_filegroup_name* } modifica il filegroup impostando lo stato su READ_ONLY o READ_WRITE, impostando il filegroup come filegroup predefinito per il database, o modifica il nome del filegroup.  
  
 \<filegroup_updatability_option >  
 Imposta la proprietà di sola lettura o di lettura/scrittura per il filegroup.  
  
 DEFAULT  
 Modifica il filegroup di database predefinito per *filegroup_name*. In un database può esistere un solo filegroup predefinito. Per altre informazioni, vedere [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md).  
  
 NOME = *new_filegroup_name*  
 Modifica il nome del filegroup per il *new_filegroup_name*.  
  
 OPZIONI AUTOGROW_SINGLE_FILE  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Quando un file nel filegroup soddisfa la soglia di aumento automatico delle dimensioni, cresce solo tale file. Impostazione predefinita.  
  
 AUTOGROW_ALL_FILES  

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])
  
 Quando un file nel filegroup soddisfa la soglia di aumento automatico delle dimensioni, tutti i file nel filegroup di aumento delle dimensioni.  
  
 **\<filegroup_updatability_option >:: =**  
  
 Imposta la proprietà di sola lettura o di lettura/scrittura per il filegroup.  
  
 READ_ONLY | READONLY  
 Specifica che il filegroup è di sola lettura. Non sono consentiti aggiornamenti degli oggetti nel filegroup. Non è possibile rendere di sola lettura il filegroup primario. Per modificare questo stato, è necessario disporre dell'accesso esclusivo al database. Per altre informazioni, vedere la clausola SINGLE_USER.  
  
 I database di sola lettura non consentono modifiche dei dati e pertanto:  
  
-   Non viene eseguito il recupero automatico all'avvio del sistema.  
-   La compattazione del database non è possibile.  
-   Non vengono attivati blocchi nei database di sola lettura e ciò può portare a migliori prestazioni di esecuzione delle query.  
  
> [!NOTE]  
>  La parola chiave READONLY verrà rimossa in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitarne l'utilizzo in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Utilizzare READ_ONLY in alternativa.  
  
 READ_WRITE | READWRITE  
 Specifica che il filegroup è di lettura/scrittura. Sono consentiti aggiornamenti degli oggetti contenuti nel filegroup. Per modificare questo stato, è necessario disporre dell'accesso esclusivo al database. Per altre informazioni, vedere la clausola SINGLE_USER.  
  
> [!NOTE]  
>  La parola chiave `READWRITE` verrà rimossa in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di utilizzare `READWRITE` nello sviluppo di nuove di lavoro e pianificare la modifica delle applicazioni che attualmente utilizzano `READWRITE` utilizzare `READ_WRITE` invece.  
  
 Per determinare lo stato di queste opzioni, è possibile esaminare il **is_read_only** colonna il **Sys. Databases** vista del catalogo o **aggiornabilità** proprietà del `DATABASEPROPERTYEX` (funzione).  
  
## <a name="remarks"></a>Remarks  
 Per ridurre le dimensioni di un database, utilizzare [DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md).  
  
È possibile aggiungere o rimuovere un file durante un `BACKUP` è in esecuzione.  
  
Per ogni database è possibile specificare un massimo di 32.767 file e 32.767 filegroup.  
  
A partire da [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], lo stato di un file di database (ad esempio, online o offline), viene mantenuto indipendentemente dallo stato del database. Per ulteriori informazioni, vedere [degli stati di File](../../relational-databases/databases/file-states.md). 
-  Lo stato dei file all'interno di un filegroup determina la disponibilità dell'intero filegroup. Un filegroup è disponibile se tutti i file in esso inclusi sono online. 
-  Se un filegroup è offline, qualsiasi tentativo di accesso al filegroup tramite un'istruzione SQL avrà esito negativo e verrà generato un errore. Quando si compilano i piani di query per `SELECT` istruzioni, query optimizer evita gli indici non cluster e viste indicizzate che risiedono nel filegroup offline. Ciò consente la corretta esecuzione di tali istruzioni. Tuttavia, se il filegroup offline contiene l'heap o indice cluster della tabella di destinazione, il `SELECT` istruzione avrà esito negativo. Inoltre, qualsiasi `INSERT`, `UPDATE`, o `DELETE` istruzioni che modificano una tabella con un indice incluso in un filegroup offline avrà esito negativo.  
  
## <a name="moving-files"></a>Spostamento di file  
È possibile spostare file di dati e di log, di sistema o definiti dall'utente, specificando la nuova posizione in FILENAME. Questa procedura può risultare utile nei casi seguenti:  
  
-   Recupero da errore. ad esempio quando il database è in modalità sospetta o viene chiuso a causa di un errore hardware.  
-   Rilocazione pianificata.  
-   Rilocazione per una manutenzione pianificata del disco.  
  
Per ulteriori informazioni, vedere [spostare i file di Database](../../relational-databases/databases/move-database-files.md).  
  
## <a name="initializing-files"></a>Inizializzazione dei file  
Per impostazione predefinita, i file di dati e di log vengono inizializzati tramite il riempimento con zeri quando si esegue una delle operazioni seguenti:  
  
-   Creazione di un database.   
-   Aggiunta di file a un database esistente.   
-   Aumento delle dimensioni di un file esistente.   
-   Ripristino di un database o un filegroup.   
  
I file di dati possono essere inizializzati immediatamente. Ciò consente l'esecuzione rapida di queste operazioni sui file. Per ulteriori informazioni, vedere [Inizializzazione di file di database](../../relational-databases/databases/database-instant-file-initialization.md). 
  
## <a name="removing-a-filestream-container"></a>Rimozione di un contenitore FILESTREAM  
 Anche se il contenitore FILESTREAM potrebbe essere stato svuotato mediante l'operazione "DBCC SHRINKFILE", potrebbe essere ancora necessario mantenere nel database i riferimenti ai file eliminati per vari motivi di manutenzione del sistema. [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) eseguirà il Garbage Collector di FILESTREAM per rimuovere questi file quando è possibile farlo. A meno che il Garbage Collector per FILESTREAM non abbia rimosso tutti i file da un contenitore FILESTREAM, l'operazione ALTER DATABASEREMOVE FILE avrà esito negativo per la rimozione di un contenitore FILESTREAM e verrà restituito un errore. È consigliabile utilizzare il processo seguente per rimuovere un contenitore FILESTREAM.  
  
1.  Eseguire [DBCC SHRINKFILE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md) con l'opzione EMPTYFILE per spostare il contenuto di questo contenitore attivo in altri contenitori.  
  
2.  Assicurarsi che siano stati eseguiti i backup del log, nel modello di recupero FULL o BULK_LOGGED.  
  
3.  Assicurarsi che sia stato eseguito il processo di lettura log repliche, se rilevante.  
  
4.  Eseguire [sp_filestream_force_garbage_collection &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md) per forzare garbage collector di eliminare i file che non sono più necessari in questo contenitore.  
  
5.  Eseguire ALTER DATABASE con l'opzione REMOVE FILE per rimuovere questo contenitore.  
  
6.  Ripetere i passaggi da 2 a 4 ancora una volta per completare la Garbage Collection.  
  
7.  Utilizzare ALTER Database...REMOVE FILE per rimuovere questo contenitore.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-adding-a-file-to-a-database"></a>A. Aggiunta di un file a un database  
 Nell'esempio seguente viene aggiunto un file di dati da 5 MB al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = Test1dat2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat2.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="b-adding-a-filegroup-with-two-files-to-a-database"></a>B. Aggiunta di un filegroup con due file a un database  
 Nell'esempio seguente viene creato il filegroup `Test1FG1` nel database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] e vengono aggiunti due file da 5 MB al filegroup.  
  
```sql  
USE master  
GO  
ALTER DATABASE AdventureWorks2012  
ADD FILEGROUP Test1FG1;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = test1dat3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat3.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1dat4,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat4.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
)  
TO FILEGROUP Test1FG1;  
GO  
  
```  
  
### <a name="c-adding-two-log-files-to-a-database"></a>C. Aggiunta di due file di log a un database  
 Nell'esempio seguente vengono aggiunti due file di log da 5 MB al database [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD LOG FILE   
(  
    NAME = test1log2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\test2log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1log3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\test3log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="d-removing-a-file-from-a-database"></a>D. Rimozione di un file da un database  
 Nell'esempio seguente viene rimosso uno dei file aggiunti nell'esempio B.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4;  
GO  
```  
  
### <a name="e-modifying-a-file"></a>E. Modifica di un file  
Nell'esempio seguente vengono aumentate le dimensioni di uno dei file aggiunti nell'esempio B.  
 L'istruzione ALTER DATABASE con il comando MODIFY FILE effettuare una dimensione dei file più grande, pertanto se è necessario per ridurne le dimensioni del file è necessario utilizzare DBCC SHRINKFILE.  
  
```sql  
USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO  
```

In questo esempio viene ridotta la dimensione di un file di dati a 100 MB e quindi specifica le dimensioni in tale quantità. 

```sql
USE AdventureWorks2012;
GO

DBCC SHRINKFILE (AdventureWorks2012_data, 100);
GO

USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO
```
 
  
### <a name="f-moving-a-file-to-a-new-location"></a>F. Spostamento di un file in un diverso percorso  
 Nell'esempio seguente il file `Test1dat2` creato nell'esempio A viene spostato in una nuova directory.  
  
> [!NOTE]  
> È necessario spostare fisicamente il file nella nuova directory prima di eseguire l'esempio. In seguito, arrestare e avviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oppure impostare il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] su OFFLINE e quindi su ONLINE per implementare la modifica.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
MODIFY FILE  
(  
    NAME = Test1dat2,  
    FILENAME = N'c:\t1dat2.ndf'  
);  
GO  
```  
  
### <a name="g-moving-tempdb-to-a-new-location"></a>G. Spostamento del database tempdb in un diverso percorso  
 Nell'esempio seguente viene spostato il database `tempdb` dal percorso corrente nel disco a un'altro percorso nel disco. Poiché `tempdb` viene ricreato a ogni avvio del servizio MSSQLSERVER, non è necessario spostare fisicamente i dati e i file di log. I file vengono creati quando il servizio viene riavviato nel passaggio 3. Fino a quando il servizio non viene riavviato, `tempdb` continua a funzionare nel percorso esistente.  
  
1.  Determinare i nomi di file logici del database `tempdb` e il rispettivo percorso corrente su disco.  
  
    ```sql  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    GO  
    ```  
  
2.  Modificare il percorso di ogni file tramite `ALTER DATABASE`.  
  
    ```sql  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE  tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'E:\SQLData\templog.ldf');  
    GO  
    ```  
  
3.  Arrestare e riavviare l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
4.  Verificare la modifica ai file.  
  
    ```sql  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    ```  
  
5.  Eliminare i file tempdb.mdf e templog.ldf dai percorsi originali.  
  
### <a name="h-making-a-filegroup-the-default"></a>H. Impostazione di un filegroup come predefinito  
 Nell'esempio seguente il `Test1FG1` filegroup creato nell'esempio B il filegroup predefinito. Il filegroup `PRIMARY` viene quindi reimpostato come filegroup predefinito. Si noti che il nome `PRIMARY` deve essere delimitato da parentesi quadre o virgolette.  
  
```sql  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP Test1FG1 DEFAULT;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP [PRIMARY] DEFAULT;  
GO  
```  
  
### <a name="i-adding-a-filegroup-using-alter-database"></a>I. Aggiunta di un filegroup utilizzando ALTER DATABASE  
 Nell'esempio seguente viene aggiunto un `FILEGROUP` che contiene la clausola `FILESTREAM` al database `FileStreamPhotoDB`.  
  
```sql  
--Create and add a FILEGROUP that CONTAINS the FILESTREAM clause to  
--the FileStreamPhotoDB database.  
ALTER DATABASE FileStreamPhotoDB  
ADD FILEGROUP TodaysPhotoShoot  
CONTAINS FILESTREAM;  
GO  
  
--Add a file for storing database photos to FILEGROUP   
ALTER DATABASE FileStreamPhotoDB  
ADD FILE  
(  
    NAME= 'PhotoShoot1',  
    FILENAME = 'C:\Users\Administrator\Pictures\TodaysPhotoShoot.ndf'  
)  
TO FILEGROUP TodaysPhotoShoot;  
GO  
```      
        
### <a name="j-change-filegroup-so-that-when-a-file-in-the-filegroup-meets-the-autogrow-threshold-all-files-in-the-filegroup-grow"></a>J. Modificare filegroup, in modo che quando un file nel filegroup soddisfa la soglia di aumento automatico delle dimensioni, tutti i file nel filegroup di aumento delle dimensioni
 Nell'esempio seguente genera l'errore obbligatorio `ALTER DATABASE` istruzioni per modificare il filegroup di lettura / scrittura con la `AUTOGROW_ALL_FILES` impostazione.  
  
```sql  
--Generate ALTER DATABASE ... MODIFY FILEGROUP statements  
--so that all read-write filegroups grow at the same time.  
SET NOCOUNT ON;

DROP TABLE IF EXISTS #tmpdbs
CREATE TABLE #tmpdbs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, isdone bit);

DROP TABLE IF EXISTS #tmpfgs
CREATE TABLE #tmpfgs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, fgname sysname, isdone bit);

INSERT INTO #tmpdbs ([dbid], [dbname], [isdone])
SELECT database_id, name, 0 FROM master.sys.databases (NOLOCK) WHERE is_read_only = 0 AND state = 0;

DECLARE @dbid int, @query VARCHAR(1000), @dbname sysname, @fgname sysname

WHILE (SELECT COUNT(id) FROM #tmpdbs WHERE isdone = 0) > 0
BEGIN
    SELECT TOP 1 @dbname = [dbname], @dbid = [dbid] FROM #tmpdbs WHERE isdone = 0

    SET @query = 'SELECT ' + CAST(@dbid AS NVARCHAR) + ', ''' + @dbname + ''', [name], 0 FROM [' + @dbname + '].sys.filegroups WHERE [type] = ''FG'' AND is_read_only = 0;'
    INSERT INTO #tmpfgs
    EXEC (@query)

    UPDATE #tmpdbs
    SET isdone = 1
    WHERE [dbid] = @dbid
END;

IF (SELECT COUNT(ID) FROM #tmpfgs) > 0
BEGIN
    WHILE (SELECT COUNT(id) FROM #tmpfgs WHERE isdone = 0) > 0
    BEGIN
        SELECT TOP 1 @dbname = [dbname], @dbid = [dbid], @fgname = fgname FROM #tmpfgs WHERE isdone = 0

        SET @query = 'ALTER DATABASE [' + @dbname + '] MODIFY FILEGROUP [' + @fgname + '] AUTOGROW_ALL_FILES;'

        PRINT @query

        UPDATE #tmpfgs
        SET isdone = 1
        WHERE [dbid] = @dbid AND fgname = @fgname
    END
END; 
GO  
```      
  
## <a name="see-also"></a>Vedere anche  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys. FileGroups &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [Sys. master_files &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [Dati BLOB (Binary Large Object) (SQL Server)](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)   
 [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
 [Inizializzazione di File di database](../../relational-databases/databases/database-instant-file-initialization.md)    
  
  
