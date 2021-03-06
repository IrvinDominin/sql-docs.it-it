---
title: Sys.dm_db_page_info (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.dm_db_page_info
- sys.dm_db_page_info_TSQL
- dm_db_page_info
- dm_db_page_info_TSQL
- dbcc page
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_page_info dynamic management view
author: ''
ms.author: pamela
manager: amitban
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9f2e2d0b49f58eff2eac52103bddc6fda818aeb3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849279"
---
# <a name="sysdmdbpageinfo-transact-sql"></a>Sys.dm_db_page_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Restituisce informazioni su una pagina in un database.  La funzione restituisce una riga che contiene le informazioni di intestazione dalla pagina, inclusi i `object_id`, `index_id`, e `partition_id`.  Questa funzione sostituisce la necessità di usare `DBCC PAGE` nella maggior parte dei casi.

## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_db_page_info ( DatabaseId, FileId, PageId, Mode )  
``` 

## <a name="arguments"></a>Argomenti  
 *DatabaseId* | NULL | IMPOSTAZIONE PREDEFINITA  

 ID del database. *DatabaseId* viene **smallint**. Valori validi sono il numero di ID di un database. Il valore predefinito è NULL, tuttavia l'invio di che un valore NULL per questo parametro verrà generato un errore.
 
*FileId* | NULL | IMPOSTAZIONE PREDEFINITA

ID del file. *FileId* viene **int**.  Valori validi sono il numero di ID di un file nel database specificato da *DatabaseId*. Il valore predefinito è NULL, tuttavia l'invio di che un valore NULL per questo parametro verrà generato un errore.

*PageId* | NULL | IMPOSTAZIONE PREDEFINITA

È l'ID della pagina.  *PageId* viene **int**.  Valori validi sono il numero di ID di una pagina nel file specificato da *FileId*. Il valore predefinito è NULL, tuttavia l'invio di che un valore NULL per questo parametro verrà generato un errore.

*modalità* | NULL | IMPOSTAZIONE PREDEFINITA

Determina il livello di dettaglio nell'output della funzione. "Limitato" restituirà i valori NULL per tutte le colonne descrizione, 'Dettagliate' popolerà le colonne descrizione.  Il valore predefinito è "Limitato".

## <a name="table-returned"></a>Tabella restituita  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id |INT |ID database |
|file_id |INT |ID file |
|page_id |INT |ID pagina |
|page_type |INT |Tipo di pagina |
|page_type_desc |Nvarchar(64) |Descrizione del tipo di pagina |
|page_flag_bits |Nvarchar(64) |Flag di bit nell'intestazione di pagina |
|page_flag_bits_desc |nvarchar(256) |Descrizione del flag bit nell'intestazione di pagina |
|page_type_flag_bits |Nvarchar(64) |Bit di Flag di tipo nell'intestazione di pagina |
|page_type_flag_bits_desc |Nvarchar(64) |Descrizione del tipo flag bit nell'intestazione di pagina |
|object_id |INT |ID dell'oggetto proprietario della pagina |
|index_id |INT |ID dell'indice (0 per le pagine di dati di heap) |
|partition_id |BIGINT |ID della partizione |
|alloc_unit_id |BIGINT |ID di unità di allocazione |
|page_level |INT |A livello di pagina nell'indice (foglia = 0) |
|slot_count |SMALLINT |Numero totale di slot (utilizzato e inutilizzato) <br> Per una pagina di dati, questo numero è equivalente al numero di righe. |
|ghost_rec_count |SMALLINT |Numero di record contrassegnati come fantasma nella pagina <br> Un record fantasma è quello che è stato contrassegnato per l'eliminazione ma non sono ancora stati rimossi. |
|torn_bits |INT |bit 1 per ogni settore per il rilevamento di scritture errate. Utilizzato anche per archiviare checksum <br> Questo valore viene utilizzato per rilevare il danneggiamento dei dati |
|is_iam_pg |bit |Bit per indicare se la pagina è una pagina IAM  |
|is_mixed_ext |bit |Bit per indicare se allocata in un extent misto |
|pfs_file_id |SMALLINT |ID file della pagina PFS corrispondente |
|pfs_page_id |INT |ID della pagina PFS corrispondente |
|pfs_alloc_percent |INT |Percentuale di allocazione come indicato dal byte PFS |
|pfs_status |Nvarchar(64) |Byte PFS |
|pfs_status_desc |Nvarchar(64) |Descrizione del byte PFS |
|gam_file_id |SMALLINT |ID file della pagina GAM corrispondente |
|gam_page_id |INT |ID pagina della pagina GAM corrispondente |
|gam_status |bit |Bit per indicare se allocata nella mappa GAM |
|gam_status_desc |Nvarchar(64) |Descrizione per il bit di stato nella pagina GAM |
|sgam_file_id |SMALLINT |ID file della pagina SGAM corrispondente |
|sgam_page_id |INT |ID pagina della pagina SGAM corrispondente |
|sgam_status |bit |Bit per indicare se allocata nella mappa SGAM |
|sgam_status_desc |Nvarchar(64) |Descrizione per il bit di stato nella pagina SGAM |
|diff_map_file_id |SMALLINT |ID file della pagina mappa di bit differenziale corrispondente |
|diff_map_page_id |INT |ID pagina della pagina mappa di bit differenziale corrispondente |
|diff_status |bit |Bit per indicare se viene modificato lo stato delle differenze |
|diff_status_desc |Nvarchar(64) |Descrizione per il bit di stato diff |
|ml_file_id |SMALLINT |ID file della pagina corrispondente bitmap con registrazione minima |
|ml_page_id |INT |ID pagina della pagina corrispondente bitmap con registrazione minima |
|ml_status |bit |Bit per indicare se la pagina è a registrazione minima |
|ml_status_desc |Nvarchar(64) |Descrizione dello stato della registrazione minima di bit |
|free_bytes |SMALLINT |Numero di byte disponibili nella pagina |
|free_data_offset |INT |Offset di spazio disponibile alla fine dell'area dati |
|reserved_bytes |SMALLINT |Numero di byte disponibili riservati da tutte le transazioni (se heap) <br> Numero di righe fantasma (se foglia dell'indice) |
|reserved_xdes_id |SMALLINT |Spazio fornito dalle m_xdesID a m_reservedCnt <br> Solo a scopo di debug |
|xdes_id |Nvarchar(64) |Più recente delle transazioni fornite da m_reserved <br> Solo a scopo di debug |
|prev_page_file_id |SMALLINT |ID di file di pagina precedente |
|prev_page_page_id |INT |ID di pagina pagina precedente |
|next_page_file_id |SMALLINT |ID di file di pagina successiva |
|next_page_page_id |INT |ID di pagina pagina successiva |
|MIN_LEN |SMALLINT |Lunghezza delle righe di dimensioni fisse |
|lsn |Nvarchar(64) |Numero di sequenza di log / timestamp |
|header_version |INT |Versione dell'intestazione di pagina |

## <a name="remarks"></a>Note
Il `sys.dm_db_page_info` funzione a gestione dinamica restituisce informazioni sulla pagina, ad esempio `page_id`, `file_id`, `index_id`, `object_id` e così via, presenti in un'intestazione di pagina. Queste informazioni sono utili per la risoluzione dei problemi e debug di diversi problemi di prestazioni (contesa latch / blocco) e il danneggiamento.

`sys.dm_db_page_info` può essere usato al posto di `DBCC PAGE` istruzione in molti casi, ma restituisce solo le informazioni di intestazione pagina, non il corpo della pagina. `DBCC PAGE` saranno ancora necessarie per casi d'uso in cui è necessario l'intero contenuto della pagina.

## <a name="using-in-conjunction-with-other-dmvs"></a>Uso in combinazione con altre viste a gestione dinamica
Uno dei casi di utilizzo importante `sys.dm_db_page_info` consiste nel creare un join con altre viste a gestione dinamica che espongono le informazioni della pagina.  Per facilitare il caso d'uso, una nuova colonna denominata `page_resource` è stato aggiunto che espone informazioni sulla pagina in formato esadecimale a 8 byte. Questa colonna è stata aggiunta al `sys.dm_exec_processes` e `sys.sysprocesses` e verrà aggiunto a altre DMV in futuro in base alle esigenze.

Una nuova funzione `sys.fn_PageResCracker`, accetta il `page_resource` come input e restituisce una singola riga contenente `database_id`, `file_id` e `page_id`.  Questa funzione può quindi essere utilizzata per facilitare i join tra `sys.dm_exec_requests` oppure `sys.sysprocesses` e `sys.dm_db_page_info`.

## <a name="permissions"></a>Permissions  
Richiede il `VIEW DATABASE STATE` autorizzazione nel database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-all-the-properties-of-a-page"></a>A. Visualizzazione di tutte le proprietà di una pagina
La query seguente restituisce una riga con tutte le informazioni della pagina per un determinato `database_id`, `file_id`, `page_id` combinazione con la modalità predefinita ('limitazioni')

```sql
SELECT *  
FROM sys.dm_db_page_info (5, 1, 15, DEFAULT)
```

### <a name="b-using-sysdmdbpageinfo-with-other-dmvs"></a>B. Uso di sys.dm_db_page_info con altre viste a gestione dinamica 

La query seguente restituisce una riga per ogni `wait_resource` esposti dal `sys.dm_exec_requests` quando la riga contiene un valore non null `page_resource`

```sql
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```

## <a name="see-also"></a>Vedere anche  
[Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
[Viste a gestione dinamica relative ai database &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
[sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   


