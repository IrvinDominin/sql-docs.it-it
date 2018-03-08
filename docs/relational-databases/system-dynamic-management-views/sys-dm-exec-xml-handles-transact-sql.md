---
title: sys.dm_exec_xml_handles (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_exec_xml_handles
- dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_xml_handles dynamic management function
ms.assetid: a873ce0f-6955-417a-96a1-b2ef11a83633
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8d9b94690a487911414fdceeb9cd173116ea9c0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmexecxmlhandles-transact-sql"></a>sys.dm_exec_xml_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Restituisce informazioni sugli handle attivi aperti da **sp_xml_preparedocument**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dm_exec_xml_handles (session_id | 0 )  
```  
  
## <a name="arguments"></a>Argomenti  
 *session_id* | 0,  
 ID della sessione. Se *session_id* è specificato, questa funzione restituisce informazioni sugli handle XML nella sessione specificata.  
  
 Se si specifica 0, la funzione restituisce informazioni su tutti gli handle XML di tutte le sessioni.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID della sessione che contiene l'handle del documento XML.|  
|**document_id**|**int**|ID dell'handle di documento XML restituito da **sp_xml_preparedocument**.|  
|**namespace_document_id**|**int**|ID dell'handle interno utilizzato per il documento di spazio dei nomi associato che è stato passato come terzo parametro **sp_xml_preparedocument**. È NULL se non esiste un documento dello spazio dei nomi.|  
|**sql_handle**|**varbinary(64)**|Handle per il testo del codice SQL in cui l'handle è stato definito.|  
|**statement_start_offset**|**int**|Numero di caratteri in attualmente in esecuzione batch o stored procedure in cui il **sp_xml_preparedocument** chiamata viene eseguita. Può essere utilizzato con il **sql_handle**, **statement_end_offset**e **Sys.dm exec_sql_text** funzione a gestione dinamica per recuperare l'attualmente esecuzione istruzione per la richiesta.|  
|**statement_end_offset**|**int**|Numero di caratteri in attualmente in esecuzione batch o stored procedure in cui il **sp_xml_preparedocument** chiamata viene eseguita. Può essere utilizzato con il **sql_handle**, **statement_start_offset**e **Sys.dm exec_sql_text** funzione a gestione dinamica per recuperare l'attualmente esecuzione istruzione per la richiesta.|  
|**creation_time**|**datetime**|Timestamp quando **sp_xml_preparedocument** è stato chiamato.|  
|**original_document_size_bytes**|**bigint**|Dimensioni in byte del documento XML non analizzato.|  
|**original_namespace_document_size_bytes**|**bigint**|Dimensioni in byte del documento dello spazio dei nomi XML non analizzato. È NULL se non esiste un documento dello spazio dei nomi.|  
|**num_openxml_calls**|**bigint**|Numero di chiamate a OPENXML con questo handle di documento.|  
|**row_count**|**bigint**|Numero di righe restituite da tutte le chiamate a OPENXML precedenti per questo handle di documento.|  
|**dormant_duration_ms**|**bigint**|Millisecondi trascorsi dall'ultima chiamata a OPENXML. Se non è stato chiamato, OPENXML restituisce i millisecondi di **sp_xml_preparedocument**chiamata t.|  
  
## <a name="remarks"></a>Osservazioni  
 La durata di **sql_handles** utilizzato per recuperare il testo SQL eseguito una chiamata a **sp_xml_preparedocument** sia maggiore di quella il piano memorizzato nella cache usato per eseguire la query. Se il testo della query non è disponibile nella cache, non sarà possibile recuperare i dati utilizzando le informazioni incluse nel risultato della funzione. Questa situazione può verificarsi in caso di esecuzione di numerosi batch di grandi dimensioni.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE sul server per visualizzare tutte le sessioni o gli ID di sessione che non appartengono al chiamante. Un chiamante può sempre visualizzare i dati del proprio ID della sessione corrente.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono selezionati tutti gli handle attivi.  
  
```  
SELECT * FROM sys.dm_exec_xml_handles(0);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Funzioni e viste a gestione dinamica &#40; relative all'esecuzione Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
