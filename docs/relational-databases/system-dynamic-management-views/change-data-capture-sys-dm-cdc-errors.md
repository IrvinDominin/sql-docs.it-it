---
title: sys.dm_cdc_errors (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_cdc_errors_TSQL
- dm_cdc_errors
- sys.dm_cdc_errors
- sys.dm_cdc_errors_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cdc_errors dynamic management view
- change data capture [SQL Server], error reporting
ms.assetid: 898f2d76-9e63-45ef-94da-8034e86004ab
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 03e39dee1e8a04aa1222be9d5e477c7dd76895ad
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="change-data-capture---sysdmcdcerrors"></a>Change Data Capture - Sys.dm cdc_errors
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni errore rilevato durante la sessione di analisi dei log di acquisizione dei dati delle modifiche.  
 
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID della sessione.<br /><br /> 0 = l'errore non si è verificato all'interno di una sessione di analisi dei log.|  
|**phase_number**|**int**|Numero che indica la fase in cui si trovava la sessione quando si è verificato l'errore. Per una descrizione di ogni fase, vedere [Sys.dm cdc_log_scan_sessions &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md).|  
|**entry_time**|**datetime**|Data e ora di registrazione dell'errore. Questo valore corrisponde al timestamp nel log degli errori di SQL.|  
|**error_number**|**int**|ID del messaggio di errore.|  
|**error_severity**|**int**|Livello di gravità del messaggio, compreso tra 1 e 25.|  
|**error_state**|**int**|Numero di contesto dell'errore.|  
|**error_message**|**nvarchar(1024)**|Testo del messaggio di errore.|  
|**start_lsn**|**nvarchar(23)**|Valore LSN iniziale delle righe in elaborazione quando si è verificato l'errore.<br /><br /> 0 = l'errore non si è verificato all'interno di una sessione di analisi dei log.|  
|**begin_lsn**|**nvarchar(23)**|Valore LSN iniziale della transazione in elaborazione quando si è verificato l'errore.<br /><br /> 0 = l'errore non si è verificato all'interno di una sessione di analisi dei log.|  
|**sequence_value**|**nvarchar(23)**|Valore LSN delle righe in elaborazione quando si è verificato l'errore.<br /><br /> 0 = l'errore non si è verificato all'interno di una sessione di analisi dei log.|  
  
## <a name="remarks"></a>Osservazioni  
 **Sys.dm cdc_errors** contiene informazioni sull'errore per le sessioni di 32 precedente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW DATABASE STATE per eseguire query di **Sys.dm cdc_errors** vista a gestione dinamica. Per ulteriori informazioni sulle autorizzazioni per le viste a gestione dinamica, vedere [funzioni e viste a gestione dinamica &#40; Transact-SQL &#41; ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.dm_cdc_log_scan_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/change-data-capture-sys-dm-cdc-log-scan-sessions.md)   
 [sys.dm_repl_traninfo &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-repl-traninfo-transact-sql.md)  
  
  

