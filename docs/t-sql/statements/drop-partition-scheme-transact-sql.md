---
title: ELIMINARE lo schema di partizione (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP PARTITION SCHEME
- DROP_PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP PARTITION SCHEME statement
- deleting partition schemes
- dropping partition schemes
- removing partition schemes
- partition schemes [SQL Server], removing
ms.assetid: 6efbc87c-1c92-4e43-96a7-e0f30f1db185
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c410a37aca0ad2b7c8ca662f76d9af8d9fc6d75a
ms.sourcegitcommit: 50e54dda407f362262b86941f68b7d80516db7fb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/06/2017
---
# <a name="drop-partition-scheme-transact-sql"></a>DROP PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove uno schema di partizione dal database corrente. Gli schemi di partizione vengono creati utilizzando [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) e modificati tramite [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP PARTITION SCHEME partition_scheme_name [ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *partition_scheme_name*  
 Nome dello schema di partizione che si desidera eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile eliminare uno schema di partizione solo se non esistono tabelle o indici che lo utilizzano. Se esistono tabelle o indici che utilizzano lo schema di partizione specifico, l'istruzione DROP PARTITION SCHEME restituisce un errore. L'esecuzione dell'istruzione DROP PARTITION SCHEME non comporta la rimozione dei filegroup.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire l'istruzione DROP PARTITION SCHEME, è necessario utilizzare le autorizzazioni seguenti:  
  
-   Autorizzazione ALTER ANY DATASPACE. Questa autorizzazione viene concessa per impostazione predefinita al ruolo predefinito del server **sysadmin** e ai ruoli predefiniti dei database **db_owner** e **db_ddladmin** .  
  
-   Autorizzazione CONTROL o ALTER per il database nel quale viene creato lo schema di partizione.  
  
-   Autorizzazione CONTROL SERVER o ALTER ANY DATABASE per il server del database nel quale è stato creato lo schema di partizione.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente lo schema di partizione `myRangePS1` viene eliminato dal database corrente:  
  
```  
DROP PARTITION SCHEME myRangePS1;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [Sys. partition_schemes &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [Sys.destination_data_spaces &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [Sys. Partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
