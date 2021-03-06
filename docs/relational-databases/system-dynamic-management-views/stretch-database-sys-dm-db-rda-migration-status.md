---
title: sys.dm_db_rda_migration_status (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3027978ca57b5ea94c69dc2410b0d25d73ce3823
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740979"
---
# <a name="stretch-database---sysdmdbrdamigrationstatus"></a>Stretch Database - DM db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni batch di dati migrati da ogni tabella abilitata per l'estensione nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Batch vengono identificati dalle rispettive ora di inizio e ora di fine.  
  
 **DM db_rda_migration_status** ha come ambito il contesto del database corrente. Assicurarsi di che essere nel contesto del database delle tabelle di abilitare Stretch per la quale si desidera visualizzare lo stato di migrazione.  
  
 Nelle [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], l'output di **DM db_rda_migration_status** è limitata a 200 righe.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|L'ID della tabella da cui è sono eseguita la migrazione di righe.|  
|**database_id**|**int**|L'ID del database da cui è sono eseguita la migrazione di righe.|  
|**migrated_rows**|**bigint**|Il numero di righe migrate nel batch.|  
|**start_time_utc**|**datetime**|L'ora UTC in cui è iniziata il batch.|  
|**end_time_utc**|**datetime**|L'ora UTC in cui il batch è stata completata.|  
|**error_number**|**int**|Se il batch non riesce, il numero di errore dell'errore che si sono verificati. in caso contrario, null.|  
|**error_severity**|**int**|Se il batch non riesce, la gravità dell'errore che si sono verificati. in caso contrario, null.|  
|**error_state**|**int**|Se il batch non riesce, lo stato dell'errore che si sono verificati. in caso contrario, null.<br /><br /> Il **error_state** indica la condizione o un percorso in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
