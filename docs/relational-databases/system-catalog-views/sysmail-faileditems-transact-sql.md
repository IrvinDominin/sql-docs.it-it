---
title: sysmail_faileditems (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_faileditems
- sysmail_faileditems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_faileditems database mail view
ms.assetid: a31562c5-358e-4cfc-a72d-b3faccc53851
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3147c846a4a69f199e5b3ae8c0cea931429254fc
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysmailfaileditems-transact-sql"></a>sysmail_faileditems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni messaggio di posta elettronica Database il **Impossibile** stato. Utilizzare questa vista per controllare quali messaggi non sono stati inviati correttamente.  
  
 Per visualizzare tutti i messaggi elaborati da posta elettronica Database, utilizzare [sysmail_allitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md). Per visualizzare solo i messaggi non inviati, utilizzare [sysmail_unsentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Per visualizzare solo i messaggi che sono stati inviati, utilizzare [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md). Per visualizzare allegati di posta elettronica, utilizzare [sysmail_attachments &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Identificatore dell'elemento di posta nella coda della posta.|  
|**profile_id**|**int**|Identificatore del profilo utilizzato per l'invio del messaggio.|  
|**destinatari**|**ntext**|Indirizzi di posta elettronica dei destinatari del messaggio.|  
|**copy_recipients**|**ntext**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio.|  
|**blind_copy_recipients**|**ntext**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio, ma i cui nomi non sono indicati nell'intestazione del messaggio.|  
|**subject**|**nvarchar(510)**|Oggetto del messaggio.|  
|**body**|**ntext**|Corpo del messaggio.|  
|**body_format**|**varchar(20)**|Formato del corpo del messaggio. I possibili valori sono TEXT e HTML.|  
|**importanza**|**varchar(6)**|Il **importanza** parametro del messaggio.|  
|**sensitivity**|**varchar(12)**|Il **sensibilità** parametro del messaggio.|  
|**file_attachments**|**ntext**|Elenco delimitato da punti e virgola dei nomi dei file allegati al messaggio di posta elettronica.|  
|**Attachment_encoding**|**varchar(20)**|Tipo di allegato del messaggio di posta elettronica.|  
|**Query**|**ntext**|Query eseguita dal programma di posta elettronica.|  
|**execute_query_database**|**sysname**|Contesto di database all'interno del quale il programma di posta elettronica ha eseguito la query.|  
|**attach_query_result_as_file**|**bit**|Quando il valore è 0, i risultati della query sono inclusi nel corpo del messaggio di posta elettronica, dopo il contenuto del corpo. Quando il valore è 1, i risultati sono restituiti come file allegato.|  
|**query_result_header**|**bit**|Quando il valore è 1, i risultati della query includono le intestazioni di colonna. Quando il valore è 0, i risultati della query non includono le intestazioni di colonna.|  
|**query_result_width**|**int**|Il **query_result_width** parametro del messaggio.|  
|**query_result_separator**|**char(1)**|Carattere utilizzato per separare le colonne nell'output della query.|  
|**exclude_query_output**|**bit**|Il **exclude_query_output** parametro del messaggio. Per ulteriori informazioni, vedere [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Il **append_query_error** parametro del messaggio. 0 indica che Posta elettronica database non deve inviare il messaggio di posta elettronica se la query contiene un errore.|  
|**send_request_date**|**datetime**|Data e ora di inserimento del messaggio nella coda della posta.|  
|**send_request_user**|**sysname**|Utente che ha inviato il messaggio. Corrisponde al contesto utente della procedura di Posta elettronica database e non al campo Da del messaggio.|  
|**sent_account_id**|**int**|Identificatore dell'account di Posta elettronica database utilizzato per l'invio del messaggio. Per questa vista è sempre NULL.|  
|**sent_status**|**varchar(8)**|Stato del messaggio. Sempre **Impossibile** per la visualizzazione.|  
|**sent_date**|**datetime**|Data e ora di rimozione del messaggio dalla coda della posta.|  
|**last_mod_date**|**datetime**|Data e ora dell'ultima modifica della riga.|  
|**last_mod_user**|**sysname**|Autore dell'ultima modifica della riga.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **sysmail_faileditems** visualizzazione per visualizzare i messaggi non inviati da posta elettronica Database. Quando si risolvono i problemi relativi a Posta elettronica database, questa vista può consentire di identificare la natura del problema in quanto indica gli attributi dei messaggi che non sono stati inviati. Per visualizzare il motivo dell'errore, vedere la voce per il messaggio non riuscito nel [sysmail_event_log &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md) visualizzazione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Concesso a **sysadmin** ruolo predefinito del server e **databasemailuserrole** ruolo del database. Quando viene utilizzata da un membro del **sysadmin** ruolo predefinito del server, questa vista mostra i messaggi non riusciti. Tutti gli altri utenti vedono semplicemente i messaggi non recapitati che hanno cercato di inviare personalmente.  
  
  
