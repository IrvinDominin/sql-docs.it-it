---
title: Sys. elastic_pool_resource_stats (Database SQL di Azure) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: reference
f1_keywords:
- sys.elastic_pool_resource_stats catalog view
helpviewer_keywords:
- sys.elastic_pool_resource_stats_TSQL
- sys.elastic_pool_resource_stats
- elastic_pool_resource_stats_TSQL
- elastic_pool_resource_stats
ms.assetid: f242c1bd-3cc8-4c8b-8aaf-c79b6a8a0329
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 210e051088539920ad9c26e8036c7d9a911a2e4c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653129"
---
# <a name="syselasticpoolresourcestats-azure-sql-database"></a>Sys. elastic_pool_resource_stats (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Restituisce le statistiche di utilizzo di risorse per tutti i pool di database elastici in un server logico. Per ogni pool di database elastici, è disponibile una riga per ogni 15 secondi (quattro righe per ogni minuto) finestra di report. Inclusi CPU, IO, Log, il consumo di archiviazione e l'utilizzo di richieste/sessioni simultanee da tutti i database nel pool. Questi dati vengono conservati per 14 giorni. 
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12.|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**start_time**|**datetime2**|Ora UTC che indica l'inizio dei periodo di 15 secondi.|  
|**end_time**|**datetime2**|Ora UTC che indica la fine del secondo intervallo di reporting 15.|  
|**nome_pool_elastico**|**nvarchar(128)**|Nome del pool di database elastici.|  
|**avg_cpu_percent**|**decimal(5,2)**|Utilizzo di calcolo medio in percentuale del limite del pool.|  
|**avg_data_io_percent**|**decimal(5,2)**|Utilizzo dei / o medio espresso in percentuale sulla base del limite del pool.|  
|**avg_log_write_percent**|**decimal(5,2)**|Medio scrittura utilizzo delle risorse in percentuale del limite del pool.|  
|**avg_storage_percent**|**decimal(5,2)**|Utilizzo di spazio di archiviazione medio espresso in percentuale del limite di archiviazione del pool.|  
|**max_worker_percent**|**decimal(5,2)**|Massimi ruoli di lavoro simultanei (richieste) espresso in percentuale sulla base del limite del pool.|  
|**max_session_percent**|**decimal(5,2)**|Numero massimo di sessioni simultaneo espresso in percentuale sulla base del limite del pool.|  
|**elastic_pool_dtu_limit**|**int**|Pool elastico max DTU impostazione corrente per questo pool elastico durante questo intervallo.|  
|**elastic_pool_storage_limit_mb**|**bigint**|Limite di archiviazione massima del pool elastico corrente l'impostazione per questo pool elastico in megabyte durante questo intervallo.|
|**avg_allocated_storage_percent**|**decimal(5,2)**|La percentuale di dati spazio allocato per tutti i database nel pool elastico.  Questa è la percentuale di spazio per i dati allocato alla dimensione massima dei dati per il pool elastico.  Per altre informazioni vedere: [gestione dello spazio del File nel database SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management)|  
  
## <a name="remarks"></a>Note  
 In questa vista esiste nel database master del server logico. È necessario essere connessi al database master per eseguire query **Sys. elastic_pool_resource_stats**.  
  
## <a name="permissions"></a>Permissions  
 Richiede l'appartenenza al **dbmanager** ruolo.  
  
## <a name="examples"></a>Esempi  
 L'esempio seguente restituisce i dati di utilizzo delle risorse ordinati in base l'ora più recente per tutti i pool di database elastici nel server logico corrente.  
  
```  
SELECT * FROM sys.elastic_pool_resource_stats   
ORDER BY end_time DESC;  
```  
  
 L'esempio seguente calcola il consumo percentuale medio di DTU per un pool specifico.  
  
```  
SELECT start_time, end_time,      
  (SELECT Max(v)      
FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS value(v)) AS [avg_DTU_percent]    
FROM sys.elastic_pool_resource_stats   
WHERE elastic_pool_name = '<your pool name>'   
ORDER BY end_time DESC;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestire una crescita straordinaria con database elastici](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/)   
 [Creare e gestire un pool di database elastici di Database SQL (anteprima)](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool-portal/)   
 [Sys. resource_stats &#40;Database SQL di Azure&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [DM db_resource_stats &#40;Database SQL di Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md)  
  
  
