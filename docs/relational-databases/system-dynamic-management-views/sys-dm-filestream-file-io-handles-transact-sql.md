---
title: sys.dm_filestream_file_io_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 34d72c21f66544cae05bd9fa6dba8cb70282862c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati gli handle di file conosciuti dal proprietario dello spazio dei nomi (NSO, Namespace Owner). Handle di FileStream che un client ottenuto tramite **OpenSqlFilestream** vengono visualizzati in questa vista.  
  
|Colonna|Tipo|Description|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Viene mostrato l'indirizzo della struttura NSO interna associata all'handle del client. Ammette i valori Null.|  
|**creation_request_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null.|  
|**creation_irp_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null|  
|**handle_id**|**int**|Viene mostrato l'ID univoco di questo handle assegnato dal driver. Non ammette i valori Null.|  
|**creation_client_thread_id**|**varbinary(8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**creation_client_process_id**|**varbinary(8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**filestream_transaction_id**|**varbinary(128)**|Viene mostrato l'ID della transazione associata all'handle specificato. Si tratta del valore restituito dal **get_filestream_transaction_context** (funzione). Utilizzare questo campo per creare un join al **Sys.dm filestream_file_io_requests** visualizzazione. Ammette i valori Null.|  
|**access_type**|**nvarchar(60)**|Non ammette i valori Null.|  
|**logical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso logico del file aperto da questo handle. Questo è lo stesso percorso restituito dal **. PathName** metodo **varbinary**(**max**) filestream. Ammette i valori Null.|  
|**physical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso NTFS effettivo del file. Questo è lo stesso percorso restituito dal **. PhysicalPathName** metodo il **varbinary**(**max**) filestream. Viene abilitato dal flag di traccia 5556. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [FileStream e FileTable DMV &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
