---
title: sys.database_query_store_options (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/25/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_QUERY_STORE_OPTIONS_TSQL
- DATABASE_QUERY_STORE_OPTIONS
- SYS.DATABASE_QUERY_STORE_OPTIONS_TSQL
- SYS.DATABASE_QUERY_STORE_OPTIONS
dev_langs:
- TSQL
helpviewer_keywords:
- database_query_store_options catalog view
- sys.database_query_store_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46710eb543ae038d22052cd55b356df9458201e3
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="sysdatabasequerystoreoptions-transact-sql"></a>sys.database_query_store_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Restituisce le opzioni di archivio Query per il database.  
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**desired_state**|**smallint**|Indica la modalità operativa desiderata dell'archivio Query, impostare in modo esplicito dall'utente.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE|  
|**desired_state_desc**|**nvarchar(64)**|Descrizione della modalità operativa desiderata dell'archivio Query:<br />OFF<br />READ_ONLY<br />READ_WRITE|  
|**actual_state**|**smallint**|Indica la modalità operativa dell'archivio Query. Oltre l'elenco degli stati desiderati necessarie per l'utente, lo stato effettivo può essere uno stato di errore.<br /> 0 = OFF <br /> 1 = READ_ONLY<br /> 2 = READ_WRITE<br /> 3 = ERRORE|  
|**actual_state_desc**|**nvarchar(64)**|Descrizione testuale della modalità operativa effettiva dell'archivio Query.<br />OFF<br />READ_ONLY<br />READ_WRITE<br />ERROR<br /><br /> Quando lo stato effettivo è diverso da quello desiderato, esistono situazioni:<br /><br /> Archivio query potrebbe funzionare in modalità di sola lettura, anche se in lettura / scrittura è stato specificato dall'utente. Questa situazione potrebbe verificarsi, ad esempio, se il database è in modalità di sola lettura o se le dimensioni di archivio Query superano la quota.<br /><br /> Molto raramente, archivio Query può finire in stato di errore a causa di errori interni. In questo caso, archivio Query può essere recuperato tramite l'esecuzione di **sp_query_store_consistency_check** stored procedure nel database interessato.|  
|**readonly_reason**|**int**|Quando il **desired_state_desc** è READ_WRITE e **actual_state_desc** viene impostato come READ_ONLY, **readonly_reason** restituisce mappare un bit per indicare i motivi per cui l'archivio Query è modalità di sola lettura.<br /><br /> 1 – database è in modalità di sola lettura<br /><br /> 2 – database è in modalità utente singolo<br /><br /> 4-database è in modalità di emergenza<br /><br /> 8: è di database replica secondaria (si applica a Always On e Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)] replica geografica). Questo valore può essere analizzato in modo efficace solo nei **leggibile** repliche secondarie<br /><br /> 65536: l'archivio Query ha raggiunto il limite impostato dall'opzione di MAX_STORAGE_SIZE_MB.<br /><br /> 131072 - il numero di istruzioni diverse nell'archivio Query ha raggiunto il limite di memoria interna. Provare a rimuovere le query che non è necessaria o l'aggiornamento a un maggiore livello di servizio per abilitare il trasferimento di archivio Query in modalità lettura-scrittura.<br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> 262144: dimensione di elementi in memoria in attesa di essere resi persistenti su disco ha raggiunto il limite di memoria interna. Archivio query sarà in modalità di sola lettura temporaneamente fino a quando gli elementi in memoria vengono mantenuti su disco. <br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br />524288 – database ha raggiunto il limite di dimensioni del disco. Archivio query è parte del database utente, pertanto se lo spazio non sono più disponibile per un database, il che significa che l'archivio Query non aumenti ulteriormente.<br />Si applica solo a [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. <br /> <br /> Per passare le operazioni di archivio Query back modalità lettura-scrittura, vedere **archivio Query di verifica è la raccolta di Query dei dati in modo continuativo** sezione [procedure consigliate per l'archivio Query](../../relational-databases/performance/best-practice-with-the-query-store.md).|  
|**current_storage_size_mb**|**bigint**|Dimensioni dell'archivio di Query su disco in megabyte.|  
|**flush_interval_seconds**|**bigint**|Definisce periodo per regolare lo scaricamento dei dati dell'archivio di Query su disco. Valore predefinito è 900 (15 min).<br /><br /> Modifica utilizzando il `ALTER DATABASE <database> SET QUERY_STORE (DATA_FLUSH_INTERVAL_SECONDS  = <interval>)` istruzione.|  
|**interval_length_minutes**|**bigint**|Intervallo di aggregazione delle statistiche. Non sono consentiti valori arbitrari. Utilizzare uno dei seguenti: 1, 5, 10, 15, 30, 60 e 1440 minuti. Il valore predefinito è 60 minuti.|  
|**max_storage_size_mb**|**bigint**|Dimensione massima del disco per l'archivio Query. Valore predefinito è 100 MB.<br />Per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Premium Edition il valore predefinito è 1Gb, mentre per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic Edition il valore predefinito è 10Mb.<br /><br /> Modifica utilizzando il `ALTER DATABASE <database> SET QUERY_STORE (MAX_STORAGE_SIZE_MB = <size>)` istruzione.|  
|**stale_query_threshold_days**|**bigint**|Numero di giorni che esegue una query con le impostazioni di criteri non viene mantenuta nell'archivio Query. Valore predefinito è 30. Impostare su 0 per disabilitare i criteri di conservazione.<br />Per l'edizione [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] Basic, l'impostazione predefinita è 7 giorni.<br /><br /> Modifica utilizzando il `ALTER DATABASE <database> SET QUERY_STORE ( CLEANUP_POLICY = ( STALE_QUERY_THRESHOLD_DAYS = <value> ) )` istruzione.|  
|**max_plans_per_query**|**bigint**|Limita il numero massimo di piani stored. Valore predefinito è 200. Se viene raggiunto il valore massimo, archivio Query smette di acquisire nuovi piani per tale query. Impostazione su 0 consente di rimuovere la limitazione per quanto riguarda il numero di piani acquisiti.<br /><br /> Modifica utilizzando il `ALTER DATABASE<database> SET QUERY_STORE (MAX_PLANS_PER_QUERY = <n>)` istruzione.|  
|**query_capture_mode**|**smallint**|La modalità di acquisizione query attualmente attiva:<br /><br /> 1 = ALL - vengono acquisite tutte le query. Questo è il valore di configurazione predefinito per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).<br /><br /> 2 = AUTO - acquisizione le query pertinenti in base al consumo di conteggio e risorse di esecuzione. Questo è il valore di configurazione predefinito per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].<br /><br /> 3 = Nessuna: arrestare l'acquisizione di nuove query. Archivio query continuerà a raccogliere le statistiche di compilazione e runtime per le query che già acquisite. Utilizzare questa configurazione con cautela, poiché potrebbe non essere implementato per acquisire le query importante.|  
|**query_capture_mode_desc**|**nvarchar(60)**|Descrizione della modalità di acquisizione effettivi dell'archivio Query:<br /><br /> TUTTI (impostazione predefinita per [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)])<br /><br /> AUTO (impostazione predefinita per [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)])<br /><br /> Nessuno|  
|**size_based_cleanup_mode**|**smallint**|Controlla se i pulizia verrà attivata automaticamente quando la quantità totale di dati sta per raggiungere le dimensioni massime:<br /><br /> 1 = OFF, non verrà attivata automaticamente la pulizia basata su dimensione.<br /><br /> 2 = AUTO - pulizia in base verrà attivata automaticamente quando la dimensione su disco raggiunge il 90% delle dimensioni **max_storage_size_mb**. Questo è il valore di configurazione predefinito.<br /><br />Pulizia basati sulle dimensioni consente di rimuovere innanzitutto le query meno recenti e meno costose. Si ferma in corrispondenza di circa l'80% di max_storage_size_mb.|  
|**size_based_cleanup_mode_desc**|**smallint**|Descrizione della modalità di pulizia basati sulle dimensioni effettive dell'archivio Query:<br /><br /> OFF <br /><br /> AUTO (impostazione predefinita)|  
|**wait_stats_capture_mode**|**smallint**|Controlla se archivio Query esegue l'acquisizione delle statistiche di attesa: <br /><br /> 0 = OFF <br /><br /> 1 = ON<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].|
|**wait_stats_mode_capture_desc**|**nvarchar(60)**|Descrizione della modalità di acquisizione di statistiche di attesa effettivo: <br /><br /> OFF <br /><br /> (Impostazione predefinita)<br /> **Si applica a**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].| 
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede il **VIEW DATABASE STATE** autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)   
 [Archivio query Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)  
  
  
