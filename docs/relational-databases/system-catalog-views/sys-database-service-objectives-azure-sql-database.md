---
title: Sys.database_service_objectives (Database SQL di Azure) | Documenti Microsoft
ms.custom: 
ms.date: 08/30/2016
ms.prod: 
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: 
ms.service: sql-database
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- Pool elastico
- pool elastico, gestione
f1_keywords:
- DATABASE_SERVICE_OBJECTIVES_TSQL
ms.assetid: cecd8c31-06c0-4aa7-85d3-ac590e6874fa
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 08c801fe0f7d917de2c520e788320ec3677d8a6e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatabaseserviceobjectives-azure-sql-database"></a>Sys.database_service_objectives (Database SQL di Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

Restituisce l'edizione (livello di servizio), l'obiettivo di servizio (livello di prezzo) e nome del pool elastico, se presente, per un database SQL di Azure o un Data Warehouse di SQL Azure. Se connessi al database master in un server di Database SQL di Azure, restituisce informazioni su tutti i database. Per Azure SQL Data Warehouse, è necessario essere connessi al database master.  
  
  
 Per informazioni sui prezzi, vedere [opzioni del Database SQL e le prestazioni: prezzi di Database SQL](https://azure.microsoft.com/en-us/pricing/details/sql-database/) e [SQL Data Warehouse prezzi](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).  
  
 Per modificare le impostazioni del servizio, vedere [ALTER DATABASE (Database SQL di Azure)](../../t-sql/statements/alter-database-azure-sql-database.md) e [ALTER DATABASE (Azure SQL Data Warehouse)](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md).  
  
 La vista sys.database_service_objectives contiene le colonne seguenti.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|database_id|int|L'ID del database, univoco all'interno di un'istanza del server di Database SQL di Azure. Attive con [Sys. Databases &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md).|  
|edition|sysname|Il livello di servizio per il database o data warehouse: **base**, **Standard**, **Premium** o **Data Warehouse**.|  
|service_objective|sysname|Il piano tariffario del database. Se il database è in un pool elastico, restituisce **ElasticPool**.<br /><br /> Nel **base** livello, restituisce **base**.<br /><br /> **Solo i database in un livello di servizio standard** restituisce uno dei seguenti: S0, S1, S2 o S3.<br /><br /> **Solo i database in un livello premium** restituisce delle operazioni seguenti: P1, P2, P4, P6/P3 o P11.<br /><br /> **SQL Data Warehouse** restituisce DW100 tramite DW2000.|  
|elastic_pool_name|sysname|Il nome del [pool elastico](https://azure.microsoft.com/documentation/articles/sql-database-elastic-pool/) al quale appartiene il database. Restituisce **NULL** se il database è un singolo database o un warehoue di dati.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiede **dbManager** autorizzazione per il database master.  A livello di database, l'utente deve essere l'autore o il proprietario.  
  
## <a name="examples"></a>Esempi  
 Questo esempio può essere eseguito nel database master o nei database utente. La query restituisce il nome del servizio e informazioni di livello delle prestazioni dei database.  
  
```sql  
SELECT  d.name,   
     slo.*    
FROM sys.databases d   
JOIN sys.database_service_objectives slo    
ON d.database_id = slo.database_id;  
  
```  
  
  
