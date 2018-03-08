---
title: log_shipping_monitor_error_detail (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_error_detail_TSQL
- log_shipping_monitor_error_detail
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_error_detail system table
ms.assetid: 0c38a625-60d2-4ee2-bcf3-2ba367914220
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c3f30aafc0d201903fab4a5d42e55c38669b70c2
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="logshippingmonitorerrordetail-transact-sql"></a>log_shipping_monitor_error_detail (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Archivia i dettagli relativi agli errori per processi di log shipping. Questa tabella è archiviata nel **msdb** database.  
  
 Le tabelle correlate alla cronologia e al monitoraggio vengono utilizzate anche nel server primario e nei server secondari.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**uniqueidentifier**|ID primario per il backup o ID secondario per la copia o il ripristino.|  
|**agent_type**|**tinyint**|Tipo di processo di log shipping.<br /><br /> 0 = backup.<br /><br /> 1 = copia.<br /><br /> 2 = ripristino.|  
|**session_id**|**int**|ID della sessione per il processo di backup/copia/ripristino.|  
|**database_name**|**sysname**|Nome del database associato a questo record di errore. Database primario per il backup, database secondario per il ripristino, o vuoto per la copia.|  
|**sequence_number**|**int**|Numero incrementale che indica l'ordine corretto delle informazioni relative agli errori che interessano più record.|  
|**log_time**|**datetime**|Data e ora di creazione del record.|  
|**log_time_utc**|**datetime**|Data e ora UTC (Coordinated Universal Time o ora di Greenwich) di creazione del record.|  
|**message**|**nvarchar**|Testo del messaggio.|  
|**origine**|**nvarchar**|Origine del messaggio di errore o dell'evento.|  
|**help_url**|**nvarchar**|URL, se disponibile, in cui sono disponibili informazioni aggiuntive sull'errore.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa tabella include i dettagli degli errori relativi ai processi di log shipping. Ogni errore viene registrato come una sequenza di eccezioni. Per ogni sessione dell'agente possono essere disponibili più errori (sequenze).  
  
 Oltre a essere archiviate sul server di monitoraggio remoto, le informazioni relative al server primario vengono archiviate nel server primario nel relativo **log_shipping_monitor_error_detail** tabella e le informazioni relative a un server secondario viene inoltre archiviato nel server secondario nel relativo **log_shipping_monitor_error_detail** tabella.  
  
 Per identificare una sessione di agente, utilizzare colonne **agent_id**, **agent_type**, e **session_id**. Ordinamento **log_time** per visualizzare gli errori nell'ordine in cui sono stati registrati.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni sul Log Shipping &#40; SQL Server &#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [log_shipping_monitor_history_detail &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-monitor-history-detail-transact-sql.md)   
 [sp_cleanup_log_shipping_history &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cleanup-log-shipping-history-transact-sql.md)   
 [sp_delete_log_shipping_primary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-database-transact-sql.md)   
 [sp_delete_log_shipping_secondary_database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-secondary-database-transact-sql.md)   
 [sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql.md)   
 [System Tables &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
