---
title: Esecuzione di operazioni di copia Bulk | Microsoft Docs
description: Esecuzione di operazioni di copia bulk utilizzando i Driver OLE DB per SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- bulk copy [OLE DB Driver for SQL Server]
- data access [OLE DB Driver for SQL Server], bulk copy operations
- OLE DB Driver for SQL Server, bulk copy operations
- MSOLEDBSQL, bulk copy operations
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 9d8d32213afb7ad070d3a59897c8b0d5db853860
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804679"
---
# <a name="performing-bulk-copy-operations"></a>Esecuzione di operazioni di copia bulk
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  La funzionalità di copia bulk di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporta il trasferimento di grandi quantità di dati in o da una tabella o una vista di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il trasferimento dei dati può essere eseguito anche specificando un'istruzione SELECT. È possibile spostare i dati tra [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e un file di dati del sistema operativo, ad esempio un file ASCII. Il file di dati può avere formati diversi. Per eseguire una copia bulk in un file di formato, è necessario definire il formato. I dati possono essere caricati in variabili di programma e trasferiti a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] mediante metodi e funzioni di copia bulk.  
  
 Per un'applicazione di esempio che illustri questa caratteristica, vedere [Bulk copia i dati usando IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-how-to/bulk-copy-data-using-irowsetfastload-ole-db.md).  
  
 In un'applicazione la copia bulk viene generalmente utilizzata in una delle modalità seguenti:  
  
-   Copia bulk da una tabella, da una vista o dal set di risultati di un'istruzione Transact-SQL in un file di dati in cui i dati vengono archiviati nello stesso formato della tabella o della vista.  
  
     Tale file viene definito file di dati in modalità nativa.  
  
-   Copia bulk da una tabella, da una vista o dal set di risultati di un'istruzione Transact-SQL in un file di dati in cui i dati vengono archiviati in un formato diverso da quello della tabella o della vista.  
  
     In questo caso viene creato un file di formato separato che definisce le caratteristiche (tipo di dati, posizione, lunghezza, carattere di terminazione e così via) di ogni colonna che viene archiviata nel file di dati. Se tutte le colonne vengono convertite in formato carattere, il file risultante viene definito file di dati in modalità carattere.  
  
-   Copia bulk da un file di dati in una tabella o una vista.  
  
     Se necessario, viene utilizzato un file di formato per determinare il layout del file di dati.  
  
-   Caricare i dati in variabili di programma, quindi importarli in una tabella o in una vista utilizzando le funzioni di copia bulk per eseguire una copia bulk in una riga per volta.  
  
 Non è necessario che i file di dati utilizzati dalle funzioni di copia bulk vengano creati da un altro programma per la copia bulk. È possibile generare un file di dati e il file di formato in base alle definizioni della copia bulk in qualsiasi altro modo. Tali file possono essere quindi utilizzati con un programma per la copia bulk di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per importare i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. È ad esempio possibile esportare dati da un foglio di calcolo in un file delimitato da tabulazione, compilare un file di formato che descrive il file delimitato da tabulazione, quindi utilizzare un programma per la copia bulk per importare rapidamente i dati in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. I file di dati generati dalla copia bulk possono essere importati anche in altre applicazioni. È ad esempio possibile utilizzare le funzioni di copia bulk per esportare i dati da una tabella o da una vista in un file con valori delimitati da tabulazioni, che è quindi possibile caricare in un foglio di calcolo.  
  
 I programmatori che eseguono la codifica di applicazioni per l'utilizzo delle funzioni di copia bulk devono seguire le regole generali per garantire un buon livello di prestazioni per la copia bulk. Per altre informazioni sul supporto per le operazioni di copia bulk in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [l'importazione ed esportazione dei dati &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Un tipo CLR definito dall'utente deve essere associato come dati binari. Anche se un file di formato specifica SQLCHAR come tipo di dati per una colonna con tipo definito dall'utente (UDT) di destinazione, l'utilità BCP tratterà i dati come binari.  
  
 Non utilizzare SET FMTONLY OFF con le operazioni di copia bulk. SET FMTONLY OFF può compromettere la riuscita dell'operazione di copia bulk o determinare risultati imprevisti.  
  
## <a name="ole-db-driver-for-sql-server"></a>Driver OLE DB per SQL Server 
 Il Driver OLE DB per SQL Server implementa due metodi per l'esecuzione di operazioni di copia bulk con un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database. Il primo metodo prevede l'uso dell'interfaccia [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) per le operazioni di copia bulk basate sulla memoria, mentre il secondo prevede l'uso dell'interfaccia [IBCPSession](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md) per le operazioni di copia bulk basate su file.  
  
### <a name="using-memory-based-bulk-copy-operations"></a>Utilizzo di operazioni di copia bulk basate sulla memoria  
 Il driver OLE DB per SQL Server implementa l'interfaccia **IRowsetFastLoad** per esporre il supporto per le operazioni di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basate sulla memoria. L'interfaccia **IRowsetFastLoad** implementa i metodi [IRowsetFastLoad::Commit](../../oledb/ole-db-interfaces/irowsetfastload-commit-ole-db.md) e [IRowsetFastLoad::InsertRow](../../oledb/ole-db-interfaces/irowsetfastload-insertrow-ole-db.md).  
  
#### <a name="enabling-a-session-for-irowsetfastload"></a>Abilitazione di una sessione per IRowsetFastLoad  
 Il consumer notifica il Driver OLE DB per SQL Server della necessità di copia bulk impostando il Driver OLE DB per la proprietà SSPROP_ENABLEFASTLOAD dell'origine dati specifici di SQL Server su VARIANT_TRUE. Con la proprietà è impostata sull'origine dati, il consumer crea un Driver OLE DB per la sessione di SQL Server. La nuova sessione consente al consumer di accedere all'interfaccia **IRowsetFastLoad**.  
  
> [!NOTE]  
>  Se l'interfaccia **IDataInitialize** viene usata per l'inizializzazione dell'origine dati, è necessario impostare la proprietà SSPROP_IRowsetFastLoad nel parametro *rgPropertySets* del metodo **IOpenRowset::OpenRowset**. In caso contrario, la chiamata al metodo **OpenRowset** restituirà E_NOINTERFACE.  
  
 Abilitazione di una sessione per la copia bulk vincola il Driver OLE DB per il supporto di SQL Server per le interfacce nella sessione. Una sessione abilitata per la copia bulk espone solo le interfacce seguenti:  
  
-   **IDBSchemaRowset**  
  
-   **IGetDataSource**  
  
-   **IOpenRowset**  
  
-   **ISupportErrorInfo**  
  
-   **ITransactionJoin**  
  
 Per disabilitare la creazione di set di righe abilitati per la copia bulk e fare in modo che la sessione del driver OLE DB per SQL Server ripristini l'elaborazione standard, reimpostare SSPROP_ENABLEFASTLOAD su VARIANT_FALSE.  
  
#### <a name="irowsetfastload-rowsets"></a>Set di righe IRowsetFastLoad  
 I set di righe della copia bulk del driver OLE DB per SQL Server sono di sola scrittura ma espongono interfacce che consentono al consumer di determinare la struttura di una tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le interfacce seguenti sono esposte in un blocco abilitata per la copia il Driver OLE DB per il set di righe di SQL Server:  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
-   **IColumnsRowset**  
  
-   **IConvertType**  
  
-   **IRowsetFastLoad**  
  
-   **IRowsetInfo**  
  
-   **ISupportErrorInfo**  
  
 Le proprietà SSPROP_FASTLOADOPTIONS, SSPROP_FASTLOADKEEPNULLS e SSPROP_FASTLOADKEEPIDENTITY specifiche del provider controllano i comportamenti di un set di righe della copia bulk del driver OLE DB per SQL Server. Le proprietà vengono specificate nel membro *rgProperties* di un membro del parametro *rgPropertySets* **IOpenRowset**.  
  
|ID proprietà|Descrizione|  
|-----------------|-----------------|  
|SSPROP_FASTLOADKEEPIDENTITY|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BOOL<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: gestisce i valori Identity forniti dal consumer.<br /><br /> VARIANT_FALSE: i valori per una colonna Identity nella tabella [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono generati da [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Qualsiasi valore associato per la colonna viene ignorata dal Driver OLE DB per SQL Server.<br /><br /> VARIANT_TRUE: il consumer associa una funzione di accesso che fornisce un valore per una colonna Identity [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La proprietà Identity non è disponibile in colonne che supportano valori NULL, pertanto il consumer specifica un valore univoco per ogni chiamata a **IRowsetFastLoad::Insert**.|  
|SSPROP_FASTLOADKEEPNULLS|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BOOL<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: gestisce valori NULL per le colonne con un vincolo DEFAULT. Ha effetto solo su colonne di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] che supportano valori NULL e alle quali è applicato un vincolo DEFAULT.<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inserisce il valore predefinito per la colonna quando il consumer del driver OLE DB per SQL Server inserisce una riga che contiene NULL per la colonna.<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inserisce NULL per il valore della colonna quando il consumer del driver OLE DB per SQL Server inserisce una riga che contiene NULL per la colonna.|  
|SSPROP_FASTLOADOPTIONS|Colonna: nessuna<br /><br /> L/S: Lettura/Scrittura<br /><br /> Tipo: VT_BSTR<br /><br /> Impostazione predefinita: nessuna<br /><br /> Descrizione: questa proprietà corrisponde all'opzione **-h** "*hint*[,...*n*]" dell'utilità **bcp**. Di seguito sono indicate le stringhe che è possibile utilizzare come opzioni per l'esecuzione della copia bulk di dati in una tabella.<br /><br /> **ORDER**(*column*[**ASC** &#124; **DESC**][,...*n*]): ordinamento dei dati nel file di dati. Le prestazioni della copia bulk vengono migliorate se il file di dati da caricare viene ordinato in base all'indice cluster della tabella.<br /><br /> **ROWS_PER_BATCH** = *bb*: numero di righe di dati per batch (come *bb*). Il server ottimizza il caricamento bulk in base al valore *bb*. Per impostazione predefinita, il valore **ROWS_PER_BATCH** è sconosciuto.<br /><br /> **KILOBYTES_PER_BATCH** = *cc*: numero di kilobyte (KB) di dati per batch (come cc). Per impostazione predefinita, il valore **KILOBYTES_PER_BATCH** è sconosciuto.<br /><br /> **TABLOCK**: un blocco a livello di tabella viene acquisito per la durata dell'operazione di copia bulk. Questa opzione migliora in modo significativo le prestazioni, in quanto mantenere attivo un blocco solo per la durata dell'operazione di copia bulk riduce la contesa dei blocchi per la tabella. Una tabella può essere caricata contemporaneamente da più client se non include indici e si specifica **TABLOCK**. Per impostazione predefinita, il comportamento del blocco è determinato dall'opzione di tabella **table lock on bulk load**.<br /><br /> **CHECK_CONSTRAINTS**: eventuali vincoli per *table_name* vengono controllati durante l'operazione di copia bulk. Per impostazione predefinita, i vincoli vengono ignorati.<br /><br /> **FIRE_TRIGGER**: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] usa il controllo delle versioni delle righe per i trigger e memorizza le versioni delle righe nell'archivio delle versioni in **tempdb**. Le ottimizzazioni della registrazione bulk sono, pertanto, disponibili anche quando i trigger sono abilitati. Prima di eseguire l'importazione bulk di un batch con un numero elevato di righe con i trigger abilitati, può essere necessario aumentare le dimensioni di **tempdb**.|  
  
### <a name="using-file-based-bulk-copy-operations"></a>Utilizzo di operazioni di copia bulk basate su file  
 Il driver OLE DB per SQL Server implementa l'interfaccia **IBCPSession** per esporre il supporto per le operazioni di copia bulk [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] basate su file. L'interfaccia **IBCPSession** implementa i metodi [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md), [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md), [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md), [IBCPSession::BCPDone](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md), [IBCPSession::BCPExec](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md), [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md), [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) e [IBCPSession::BCPWriteFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md).  
  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per funzionalità di SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [Proprietà delle origini dati &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)   
 [Informazioni sull'importazione ed esportazione in blocco di dati &#40;SQL Server&#41;](../../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)   
 [IRowsetFastLoad &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md)   
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [Ottimizzazione delle prestazioni dell'importazione bulk](http://msdn.microsoft.com/library/ms190421\(SQL.105\).aspx)  

