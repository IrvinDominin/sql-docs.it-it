---
title: sys.dm_exec_query_optimizer_info (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_query_optimizer_info_TSQL
- dm_exec_query_optimizer_info
- sys.dm_exec_query_optimizer_info_TSQL
- sys.dm_exec_query_optimizer_info
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_optimizer_info dynamic management view
ms.assetid: 1d72cef1-22d8-4ae0-91db-6694fe918c9e
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c7b87cc0b34d33abd8f658a7ff20852200b93a2c
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecqueryoptimizerinfo-transact-sql"></a>sys.dm_exec_query_optimizer_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce statistiche dettagliate sul funzionamento di Query Optimizer di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare questa vista durante l'ottimizzazione di un carico di lavoro per individuare problemi o miglioramenti per l'ottimizzazione delle query. Ad esempio, è possibile utilizzare il numero totale di ottimizzazioni, il valore del tempo trascorso e il valore di costo finale per confrontare le ottimizzazioni della query per il carico di lavoro corrente con eventuali variazioni rilevate durante il processo di ottimizzazione. Alcuni contatori forniscono dati rilevanti solo per utilizzo diagnostico interno in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questi contatori sono contrassegnati come "Solo per uso interno".  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_exec_query_optimizer_info**.  
  
|Nome|Tipo di dati|Description|  
|----------|---------------|-----------------|  
|**counter**|**nvarchar(4000)**|Nome dell'evento statistiche di Query Optimizer.|  
|**occurrence**|**bigint**|Numero di occorrenze dell'evento di ottimizzazione per il contatore corrente.|  
|**Valore**|**float**|Valore medio della proprietà per occorrenza dell'evento.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è necessaria l'autorizzazione VIEW SERVER STATE nel server.  
  
 In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Premium richiede l'autorizzazione VIEW DATABASE STATE nel database. In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] livelli Standard e Basic richiede il [!INCLUDE[ssSDS](../../includes/sssds-md.md)] account amministratore.  
  
## <a name="remarks"></a>Osservazioni  
 **Sys.dm exec_query_optimizer_info** contiene le seguenti proprietà (contatori). Tutti i valori di occorrenza sono cumulativi e vengono impostati su 0 al riavvio del sistema. Tutti i valori dei campi valori vengono impostati su NULL al riavvio del sistema. Tutti i valori delle colonne valori che specificano una media utilizzano il valore di occorrenza della stessa riga del denominatore nel calcolo della media. Tutte le ottimizzazioni di query vengono misurate quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] determina le modifiche apportate a **dm_exec_query_optimizer_info**, tra cui entrambe le query generate dall'utente e sistema. L'esecuzione di un piano già memorizzato nella cache non modifica i valori in **dm_exec_query_optimizer_info**, solo le ottimizzazioni sono significative.  
  
|Contatore|Occorrenza|Valore|  
|-------------|----------------|-----------|  
|optimizations|Numero totale di ottimizzazioni.|Non applicabile|  
|elapsed time|Numero totale di ottimizzazioni.|Tempo medio trascorso per ottimizzazione in una singola istruzione (query), espresso in secondi.|  
|final cost|Numero totale di ottimizzazioni.|Costo medio stimato per piano ottimizzato espresso nelle unità di costo interne.|  
|trivial plan|Solo per uso interno|Solo per uso interno|  
|attività|Solo per uso interno|Solo per uso interno|  
|no plan|Solo per uso interno|Solo per uso interno|  
|search 0|Solo per uso interno|Solo per uso interno|  
|search 0 time|Solo per uso interno|Solo per uso interno|  
|search 0 tasks|Solo per uso interno|Solo per uso interno|  
|search 1|Solo per uso interno|Solo per uso interno|  
|search 1 time|Solo per uso interno|Solo per uso interno|  
|search 1 tasks|Solo per uso interno|Solo per uso interno|  
|search 2|Solo per uso interno|Solo per uso interno|  
|search 2 time|Solo per uso interno|Solo per uso interno|  
|search 2 tasks|Solo per uso interno|Solo per uso interno|  
|gain stage 0 to stage 1|Solo per uso interno|Solo per uso interno|  
|gain stage 1 to stage 2|Solo per uso interno|Solo per uso interno|  
|timeout|Solo per uso interno|Solo per uso interno|  
|memory limit exceeded|Solo per uso interno|Solo per uso interno|  
|insert stmt|Numero di ottimizzazioni per istruzioni INSERT.|Non applicabile|  
|delete stmt|Numero di ottimizzazioni per istruzioni DELETE.|Non applicabile|  
|update stmt|Numero di ottimizzazioni per istruzioni UPDATE.|Non applicabile|  
|contains subquery|Numero di ottimizzazioni per una query contenente almeno una sottoquery.|Non applicabile|  
|unnest failed|Solo per uso interno|Solo per uso interno|  
|tables|Numero totale di ottimizzazioni.|Numero medio di tabelle a cui viene fatto riferimento per query ottimizzata.|  
|hint|Numero di volte in cui un hint specifico è stato specificato. Gli hint conteggiati includono gli hint per la query JOIN, GROUP, UNION e FORCE ORDER, l'opzione SET FORCE PLAN e gli hint di join.|Non applicabile|  
|order hint|Numero di volte in cui un hint per la query FORCE ORDER è stato specificato.|Non applicabile|  
|join hint|Numero di volte in cui l'algoritmo JOIN è stato applicato a un hint di join.|Non applicabile|  
|view reference|Numero di volte in cui è stato fatto riferimento a una vista in una query.|Non applicabile|  
|remote query|Numero di ottimizzazioni in cui la query ha fatto riferimento ad almeno un'origine dei dati remota, ad esempio una tabella con un nome in quattro parti o un risultato OPENROWSET.|Non applicabile|  
|maximum DOP|Numero totale di ottimizzazioni.|Valore MAXDOP effettivo medio per un piano ottimizzato. Per impostazione predefinita, MAXDOP effettivo è determinato dal **massimo grado di parallelismo** configurazione del server, l'opzione e può essere sottoposto a override per una specifica query tramite il valore dell'hint per la query MAXDOP.|  
|maximum recursion level|Numero di ottimizzazioni in cui è stato specificato un livello MAXRECURSION maggiore di 0 con l'hint per la query.|Livello MAXRECURSION medio nelle ottimizzazioni in cui è stato specificato un livello di ricorsione massimo con l'hint per la query.|  
|indexed views loaded|Solo per uso interno|Solo per uso interno|  
|indexed views matched|Numero di ottimizzazioni in cui è stata trovata la corrispondenza per una o più viste indicizzate.|Numero medio di viste corrispondenti.|  
|indexed views used|Numero di ottimizzazioni in cui una o più viste indicizzate vengono utilizzate nel piano di output dopo aver individuato la corrispondenza.|Numero medio di viste utilizzate.|  
|indexed views updated|Numero di ottimizzazioni di un'istruzione DML che generano un piano che gestisce una o più viste indicizzate.|Numero medio di viste gestite.|  
|dynamic cursor request|Numero di ottimizzazioni in cui è stata specificata una richiesta di cursore dinamico.|Non applicabile|  
|fast forward cursor request|Numero di ottimizzazioni in cui è stata specificata una richiesta di cursore fast forward-only.|Non applicabile|  
|merge stmt|Numero di ottimizzazioni per le istruzioni MERGE.|Non applicabile|  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-viewing-statistics-on-optimizer-execution"></a>A. Visualizzazione delle statistiche durante l'esecuzione di Query Optimizer  
 Nell'esempio seguente vengono visualizzate le statistiche di esecuzione di Query Optimizer per l'istanza corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT * FROM sys.dm_exec_query_optimizer_info;  
```  
  
### <a name="b-viewing-the-total-number-of-optimizations"></a>B. Visualizzazione del numero totale di ottimizzazioni  
 Nell'esempio seguente viene visualizzato il numero di ottimizzazioni eseguite.  
  
```  
SELECT occurrence AS Optimizations FROM sys.dm_exec_query_optimizer_info  
WHERE counter = 'optimizations';  
```  
  
### <a name="c-average-elapsed-time-per-optimization"></a>C. Tempo medio trascorso per ottimizzazione  
 Nell'esempio seguente viene visualizzato il tempo medio trascorso per ogni ottimizzazione.  
  
```  
SELECT ISNULL(value,0.0) AS ElapsedTimePerOptimization  
FROM sys.dm_exec_query_optimizer_info WHERE counter = 'elapsed time';  
```  
  
### <a name="d-fraction-of-optimizations-that-involve-subqueries"></a>D. Frazione di ottimizzazioni che interessano sottoquery  
 Nell'esempio seguente viene individuata la frazione di query ottimizzate contenente una sottoquery.  
  
```  
SELECT (SELECT CAST (occurrence AS float) FROM sys.dm_exec_query_optimizer_info WHERE counter = 'contains subquery') /  
       (SELECT CAST (occurrence AS float)   
        FROM sys.dm_exec_query_optimizer_info WHERE counter = 'optimizations')  
        AS ContainsSubqueryFraction;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica &#40; relative all'esecuzione Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


