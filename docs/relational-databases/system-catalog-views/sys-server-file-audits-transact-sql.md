---
title: Sys. server_file_audits (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_file_audits_TSQL
- sys.server_file_audits_TSQL
- sys.server_file_audits
- server_file_audits
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_file_audits catalog view
ms.assetid: 553288a0-be57-4d79-ae53-b7cbd065e127
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85ba57ba9e3559a790ae983025356510987c1eae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845129"
---
# <a name="sysserverfileaudits-transact-sql"></a>sys.server_file_audits (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene informazioni estese sul tipo di controllo dei file in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] audit in un'istanza del server. Per altre informazioni, vedere [SQL Server Audit &#40;Motore di database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|audit_id|**int**|ID del controllo.|  
|NAME|**sysname**|Nome del controllo.|  
|audit_guid|**uniqueidentifier**|GUID del controllo.|  
|create_date|**datetime**|Data UTC di creazione del controllo dei file.|  
|modify_date|**DataTime**|Data UTC dell'ultima modifica del controllo dei file.|  
|principal_id|**int**|ID del proprietario del controllo come registrato nel server.|  
|Tipo|**char(2)**|Tipo di controllo:<br /><br /> 0 = Registro eventi di sicurezza NT<br /><br /> 1 = Registro eventi applicazioni NT<br /><br /> 2 = File nel file system|  
|type_desc|**nvarchar(60)**|Descrizione del tipo di controllo.|  
|on_failure|**tinyint**|In condizione di errore:<br /><br /> 0 = Continua<br /><br /> 1 = Arresta l'istanza del server<br /><br /> 2= Errore operazione|  
|on_failure_desc|**nvarchar(60)**|Voce in condizione di errore:<br /><br /> CONTINUE<br /><br /> SHUTDOWN SERVER INSTANCE<br /><br /> FAIL OPERATION|  
|is_state_enabled|**tinyint**|0 = Disabilitato<br /><br /> 1 = Attivato|  
|queue_delay|**int**|Tempo massimo di attesa suggerito, in millisecondi, prima di scrivere su disco. Se il valore è 0, il controllo garantirà una scrittura prima che l'evento possa continuare.|  
|predicate|**nvarchar(8000)**|Espressione del predicato applicata all'evento.|  
|max_file_size|**bigint**|Dimensione massima, in megabyte, del controllo:<br /><br /> 0 = Dimensione illimitata/non applicabile per il tipo di controllo selezionato.|  
|max_rollover_files|**int**|Numero massimo di file da utilizzare con l'opzione di rollover.|  
|max_files|**int**|Numero massimo di file da utilizzare senza l'opzione di rollover.|  
|reserved_disk_space|**int**|Quantità di spazio su disco da riservare per ogni file.|  
|log_file_path|**nvarchar(260)**|Percorso in cui si trova il controllo. Il percorso è un percorso di file o del registro applicazioni a seconda del tipo di controllo.|  
|log_file_name|**nvarchar(260)**|Nome di base per il file di log specificato in CREATE AUDIT DDL. Al file base_log_name viene aggiunto un numero incrementale come suffisso per creare il nome del file di log.|  
  
## <a name="permissions"></a>Permissions  
 Le entità con la **ALTER ANY SERVER AUDIT** oppure **VIEW ANY DEFINITION** autorizzazione ha accesso a questa vista del catalogo. Inoltre, l'entità non deve essere negata **VIEW ANY DEFINITION** l'autorizzazione.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [Sys. server_file_audits (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
