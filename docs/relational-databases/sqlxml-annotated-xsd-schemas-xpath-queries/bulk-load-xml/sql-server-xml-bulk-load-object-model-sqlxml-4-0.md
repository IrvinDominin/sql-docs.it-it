---
title: SQL Server Bulk carico modello a oggetti XML (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
caps.latest.revision: "27"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ceefaed7dc9bc407880a8b7bc88240315a837f5f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a>Modello a oggetti per il caricamento bulk XML di SQL Server (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] modello a oggetti di caricamento Bulk XML è costituito da sqlxmlbulkload-oggetto. Questo oggetto supporta i metodi e le proprietà seguenti.  
  
## <a name="methods"></a>Metodi  
 Execute  
 Esegue il caricamento bulk dei dati utilizzando il file dello schema e il file di dati (o flusso) forniti come parametri.  
  
## <a name="properties"></a>Proprietà  
 Caricamento BULK  
 Specifica se deve essere eseguito un caricamento bulk. Questa proprietà è utile se si desidera generare solo gli schemi (vedere la proprietà SchemaGen, SGDropTables e SGUseID che seguono) e non esegue un caricamento bulk. Si tratta di una proprietà booleana. Quando la proprietà è impostata su TRUE, viene eseguito il caricamento bulk XML. Quando la proprietà è impostata su FALSE, il caricamento bulk XML non viene eseguito.  
  
 Il valore predefinito è TRUE.  
  
 CheckConstraints  
 Specifica se i vincoli (ad esempio vincoli dovuti alla relazione di chiave primaria/chiave esterna fra colonne) specificati nella colonna devono essere controllati quando il caricamento bulk XML inserisce dati nelle colonne. Si tratta di una proprietà booleana.  
  
 Quando la proprietà è impostata su TRUE, il caricamento bulk XML controlla i vincoli per ogni valore inserito. Di conseguenza, la violazione di un vincolo produce un errore.  
  
> [!NOTE]  
>  Per lasciare questa proprietà è FALSE, è necessario disporre **ALTER TABLE** autorizzazioni sulle tabelle di destinazione. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 Il valore predefinito è FALSE. Quando la proprietà è impostata su FALSE, il caricamento bulk XML ignora i vincoli durante un'operazione di inserimento. Nell'implementazione corrente è necessario definire le tabelle nell'ordine delle relazioni di chiave primaria/chiave esterna nello schema di mapping. Di conseguenza, una tabella con una chiave primaria deve essere definita prima della tabella corrispondente contenente la chiave esterna. In caso contrario, il caricamento bulk XML restituisce un errore.  
  
 Si noti che se viene eseguita la propagazione degli ID, questa opzione non viene applicata e il controllo dei vincoli resta attivato. Ciò si verifica quando `KeepIdentity=False` ed è presente una relazione definita in cui il padre è un campo di identità e il valore viene assegnato al figlio non appena generato.  
  
 ConnectionCommand  
 Identifica un oggetto connessione esistente (ad esempio, ADO o ICommand comando oggetto) che deve utilizzare il caricamento Bulk XML. È possibile utilizzare la proprietà ConnectionCommand anziché specificare una stringa di connessione con la proprietà ConnectionString. Se si utilizza ConnectionCommand, è necessario impostare la proprietà della transazione su TRUE.  
  
 Se si utilizza la proprietà ConnectionString sia ConnectionCommand, caricamento Bulk XML utilizza l'ultima proprietà specificato.  
  
 Il valore predefinito è NULL.  
  
 ConnectionString  
 Identifica la stringa di connessione OLE DB che fornisce le informazioni necessarie per stabilire una connessione a un'istanza del database. Se si utilizza la proprietà ConnectionString sia ConnectionCommand, caricamento Bulk XML utilizza l'ultima proprietà specificato.  
  
 Il valore predefinito è NULL.  
  
 ErrorLogFile  
 Specifica il nome del file in cui vengono registrati errori e messaggi dal caricamento bulk XML. Il valore predefinito è una stringa vuota, a indicare che non viene eseguita alcuna registrazione.  
  
 FireTriggers  
 Specifica se i trigger definiti nelle tabelle di destinazione devono essere attivati durante l'operazione di caricamento bulk. Il valore predefinito è FALSE.  
  
 Quando la proprietà è impostata su TRUE, i trigger vengono attivati normalmente durante le operazioni di inserimento.  
  
> [!NOTE]  
>  Per lasciare questa proprietà è FALSE, è necessario disporre **ALTER TABLE** autorizzazioni sulle tabelle di destinazione. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 Si noti che se viene eseguita la propagazione degli ID, questa opzione non viene applicata e i trigger restano attivati. Ciò si verifica quando `KeepIdentity=False` ed è presente una relazione definita in cui il padre è un campo di identità e il valore viene assegnato al figlio non appena generato.  
  
 ForceTableLock  
 Specifica se le tabelle in cui vengono copiati i dati tramite il caricamento bulk XML devono essere bloccate per la durata del caricamento bulk stesso. Si tratta di una proprietà booleana. Quando questa proprietà è impostata su TRUE, il caricamento bulk XML acquisisce blocchi di tabella per la durata del caricamento bulk stesso. Quando la proprietà è impostata su FALSE, il caricamento bulk XML acquisisce un blocco di tabella ogni volta che inserisce un record in una tabella.  
  
 Il valore predefinito è FALSE.  
  
 IgnoreDuplicateKeys  
 Specifica l'operazione da effettuare se viene eseguito un tentativo di inserimento di valori duplicati in una colonna chiave. Se questa proprietà è impostata su TRUE e viene eseguito un tentativo di inserimento di un record con un valore duplicato in una colonna chiave, il record non viene inserito in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Viene invece inserito il record successivo. L'operazione di caricamento bulk, pertanto, non ha esito negativo. Se la proprietà è impostata su FALSE, il caricamento bulk non riesce quando viene eseguito un tentativo di inserimento di un valore duplicato in una colonna chiave.  
  
 Quando la proprietà IgnoreDuplicateKeys è impostata su TRUE, viene eseguita un'istruzione di COMMIT per ogni record inserito nella tabella. Questo comportamento provoca una riduzione delle prestazioni. La proprietà può essere impostata su TRUE solo quando la proprietà delle transazioni è impostata su FALSE, poiché il comportamento transazionale viene implementato tramite file.  
  
 Il valore predefinito è FALSE.  
  
 KeepIdentity  
 Specifica la modalità di gestione dei valori per una colonna di tipo Identity nel file di origine. Si tratta di una proprietà booleana. Quando la proprietà è impostata su TRUE, il caricamento bulk XML assegna i valori specificati nel file di origine alla colonna Identity. Quando la proprietà è impostata su FALSE, l'operazione di caricamento bulk ignora i valori di colonna di tipo Identity specificati nell'origine. In questo caso, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assegna un valore alla colonna Identity.  
  
 Se il caricamento bulk interessa una colonna che è una chiave esterna che fa riferimento a una colonna Identity in cui sono archiviati valori generati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], il caricamento bulk propaga in modo appropriato tali valori Identity nella colonna chiave esterna.  
  
 Il valore di questa proprietà si applica a tutte le colonne interessate dal caricamento bulk. Il valore predefinito è TRUE.  
  
> [!NOTE]  
>  Per lasciare questa proprietà è TRUE, è necessario disporre **ALTER TABLE** autorizzazioni sulle tabelle di destinazione. In caso contrario, la proprietà deve essere impostata sul valore FALSE. Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-table-transact-sql.md).  
  
 KeepNulls  
 Specifica il valore da utilizzare per una colonna in cui manca un attributo corrispondente o un elemento figlio nel documento XML. Si tratta di una proprietà booleana. Quando la proprietà è impostata su TRUE, il caricamento bulk XML assegna un valore Null alla colonna. Non viene assegnato il valore predefinito della colonna, se presente, in base all'impostazione nel server. Il valore di questa proprietà si applica a tutte le colonne interessate dal caricamento bulk.  
  
 Il valore predefinito è FALSE.  
  
 SchemaGen  
 Specifica se creare le tabelle necessarie prima di eseguire un'operazione di caricamento bulk. Si tratta di una proprietà booleana. Se questa proprietà è impostata su TRUE, vengono create le tabelle identificate nello schema di mapping (il database deve essere presente). Se esiste già uno o più delle tabelle nel database, sgdroptables-proprietà determina se tali tabelle preesistenti devono essere eliminati e ricreati.  
  
 Il valore predefinito per la proprietà SchemaGen è FALSE. SchemaGen non crea vincoli PRIMARY KEY nelle tabelle appena create. SchemaGen, tuttavia, crea vincoli FOREIGN KEY nel database se trova corrispondenza **SQL: Relationship** e **SQL: Key-campi** annotazioni nello schema di mapping e se il campo chiave è costituita una singola colonna.  
  
 Si noti che se si imposta la proprietà SchemaGen su TRUE, il caricamento Bulk XML esegue le operazioni seguenti:  
  
-   Vengono create le tabelle necessarie dai nomi di elemento e di attributo. È pertanto importante non utilizzare parole riservate di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per i nomi di elemento e di attributo nello schema.  
  
-   Restituisce dati di overflow per qualsiasi colonna definita utilizzando il [SQL: overflow-campo](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md) in [tipo di dati xml](../../../t-sql/xml/xml-transact-sql.md) formato.  
  
 SGDropTables  
 Specifica se le tabelle esistenti devono essere eliminate e ricreate. Utilizzare questa proprietà quando la proprietà SchemaGen è impostata su TRUE. Se SGDropTables è FALSE, le tabelle esistenti vengono mantenute. Quando questa proprietà è TRUE, le tabelle esistenti vengono eliminate e ricreate.  
  
 Il valore predefinito è FALSE.  
  
 SGUseID  
 Specifica se l'attributo nello schema di mapping che è identificato come **id** tipo può essere utilizzato per la creazione di un vincolo PRIMARY KEY quando viene creata la tabella. Utilizzare questa proprietà quando la proprietà SchemaGen è impostata su TRUE. Se SGUseID è TRUE, l'utilità SchemaGen utilizza un attributo per cui **dt: Type = "id"** viene specificata come colonna chiave primaria e aggiunge il vincolo PRIMARY KEY appropriato durante la creazione della tabella.  
  
 Il valore predefinito è FALSE.  
  
 File temporanei  
 Specifica il percorso del file in cui il caricamento bulk XML crea i file temporanei per un caricamento bulk in transazioni. Questa proprietà è utile solo quando la proprietà Transaction è impostata su TRUE. È necessario verificare che l'account di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzato per il caricamento bulk XML possa accedere a tale percorso. Se questa proprietà non è impostata, il caricamento bulk XML archivia i file temporanei nel percorso specificato nella variabile di ambiente TEMP.  
  
 Transazione  
 Specifica se il caricamento bulk deve essere eseguito come transazione. In questo caso, è garantito il rollback se il caricamento bulk ha esito negativo. Si tratta di una proprietà booleana. Se la proprietà è impostata su TRUE, il caricamento bulk viene eseguito in un contesto transazionale. La proprietà TempFilePath è utile solo quando transazione è impostata su TRUE.  
  
> [!NOTE]  
>  Se si siano caricando dati binari (ad esempio hex, tipi di dati XML bin. Base64 del file binario, immagine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tipi di dati), la proprietà di transazione deve essere impostata su FALSE.  
  
 Il valore predefinito è FALSE.  
  
 XMLFragment  
 Specifica se i dati di origine sono un frammento XML. Un frammento XML è un documento XML privo di singolo elemento di livello principale (radice). Si tratta di una proprietà booleana. Questa proprietà deve essere impostata su TRUE se il file di origine è costituito da un frammento XML.  
  
 Il valore predefinito è FALSE.  
  
  