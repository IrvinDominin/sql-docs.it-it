---
title: sys.database_automatic_tuning_options (Transact-SQL) | Microsoft Docs
description: Informazioni su come visualizzare le opzioni di ottimizzazione automatica su un Database SQL
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: jovanpop-msft
ms.author: jovanpop
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8655e529f2a254daab46431b4d7b3e44768f33f5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47841239"
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>sys.database\_automatic\_tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Restituisce le opzioni di ottimizzazione automatica per questo database.  

|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Il nome dell'opzione ottimizzazione automatica. Fare riferimento a [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) per le opzioni disponibili.|  
|**desired_state**|**smallint**|Indica la modalità operativa desiderata per l'opzione ottimizzazione automatica, impostata in modo esplicito dall'utente.<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità operativa desiderata dell'opzione ottimizzazione automatica.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Indica la modalità di funzionamento dell'opzione ottimizzazione automatica.<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar(60)**|Descrizione testuale della modalità operativa effettiva dell'opzione ottimizzazione automatica.<br />OFF<br />ON|  
|**reason**|**smallint**|Indica il motivo per cui gli stati desiderati ed effettivi sono diversi.<br />2 = DISABLED<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Descrizione testuale del motivo perché sono diversi stati effettivi e desiderati.<br />DISABILITATO = opzione viene disabilitata dal sistema<br />QUERY_STORE_OFF = Query Store è stata disattivata<br />QUERY_STORE_READ_ONLY = Query Store è in modalità di sola lettura<br />NOT_SUPPORTED = disponibile solo in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition| 
  
## <a name="permissions"></a>Permissions  
 È necessaria l'autorizzazione `VIEW DATABASE STATE`.  
  
## <a name="see-also"></a>Vedere anche  
 [L'ottimizzazione automatica](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
