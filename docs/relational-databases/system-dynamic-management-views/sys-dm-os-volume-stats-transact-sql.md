---
title: sys.dm_os_volume_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_volume_stats_TSQL
- dm_os_volume_stats
- sys.dm_os_volume_stats
- sys.dm_os_volume_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_volume_stats dynamic management function
ms.assetid: fa1c58ad-8487-42ad-956c-983f2229025f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f599084d70903ae3d74c04795ddb60d473b6002
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670489"
---
# <a name="sysdmosvolumestats-transact-sql"></a>sys.dm_os_volume_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sul volume del sistema operativo (directory) in cui sono archiviati i database e i file specificati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzare questa funzione a gestione dinamica per verificare gli attributi dell'unità disco fisica o restituire informazioni sullo spazio libero disponibile relative alla directory.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sys.dm_os_volume_stats (database_id, file_id)  
```  
  
##  <a name="Arguments"></a> Argomenti  
 *database_id*  
 ID del database. *database_id* è di tipo **int** e non prevede alcun valore predefinito. Non può essere NULL.  
  
 *file_id*  
 ID del file. *file_id* viene **int**, non prevede alcun valore predefinito. Non può essere NULL.  
  
## <a name="table-returned"></a>Tabella restituita  
  
||||  
|-|-|-|  
|**Colonna**|**Data type**|**Descrizione**|  
|**database_id**|**int**|ID del database. Non può essere null.|  
|**file_id**|**int**|ID del file. Non può essere null.|  
|**volume_mount_point**|**nvarchar(512)**|Punto di montaggio in corrispondenza del quale si trova la radice del volume. Può restituire una stringa vuota.|  
|**volume_id**|**nvarchar(512)**|ID di volume del sistema operativo. Può restituire una stringa vuota.|  
|**logical_volume_name**|**nvarchar(512)**|Nome del volume logico. Può restituire una stringa vuota.|  
|**file_system_type**|**nvarchar(512)**|Tipo di volume del file system (ad esempio, NTFS, FAT, RAW). Può restituire una stringa vuota.|  
|**total_bytes**|**bigint**|Dimensioni totali del volume, espresse in byte. Non può essere null.|  
|**available_bytes**|**bigint**|Spazio libero disponibile nel volume. Non può essere null.|  
|**supports_compression**|**bit**|Indica se il volume supporta la compressione eseguita dal sistema operativo. Non può essere null.|  
|**supports_alternate_streams**|**bit**|Indica se il volume supporta flussi alternativi. Non può essere null.|  
|**supports_sparse_files**|**bit**|Indica se il volume supporta i file sparse.  Non può essere null.|  
|**is_read_only**|**bit**|Indica se il volume è attualmente contrassegnato come di sola lettura. Non può essere null.|  
|**is_compressed**|**bit**|Indica se il volume è attualmente compresso. Non può essere null.|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-return-total-space-and-available-space-for-all-database-files"></a>A. Restituzione dello spazio totale e dello spazio disponibile per tutti i file di database  
 Nell'esempio seguente vengono restituiti lo spazio totale e lo spazio disponibile (in byte) per tutti i file di database nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT f.database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.master_files AS f  
CROSS APPLY sys.dm_os_volume_stats(f.database_id, f.file_id);  
```  
  
### <a name="b-return-total-space-and-available-space-for-the-current-database"></a>B. Restituzione dello spazio totale e dello spazio disponibile per il database corrente  
 Nell'esempio seguente vengono restituiti lo spazio totale e lo spazio disponibile (in byte) per i file nel database corrente.  
  
```  
SELECT database_id, f.file_id, volume_mount_point, total_bytes, available_bytes  
FROM sys.database_files AS f  
CROSS APPLY sys.dm_os_volume_stats(DB_ID(f.name), f.file_id);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
  
  
