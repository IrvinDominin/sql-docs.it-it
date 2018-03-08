---
title: sysdatatypemappings (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysdatatypemappings
- sysdatatypemappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdatatypemappings view
ms.assetid: 5dfafb70-3e3d-4465-b293-1acff1f855b6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00c57554fbf2cc60a91d1b0a3ae13377630fe099
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdatatypemappings-transact-sql"></a>sysdatatypemappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysdatatypemappings** vista viene utilizzata per indicare il mapping tra tipi di dati di SQL Server e i tipi di dati di un sistema di gestione di database (DBMS) non SQL Server. Questa vista è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**mapping_id**|**int**|ID del mapping dei tipi di dati.|  
|**source_dbms**|**sysname**|Indica il nome del sistema DBMS per il quale viene eseguito il mapping dei tipi di dati. I possibili valori sono i seguenti.<br /><br /> **MSSQLSERVER** = l'origine è un database di SQL Server.<br /><br /> **ORACLE** = l'origine è un database Oracle.|  
|**source_version**|**sysname**|Indica la versione del prodotto del sistema DBMS di origine.|  
|**source_type**|**sysname**|Indica il tipo di dati elencato nel sistema DBMS di origine.|  
|**source_length_min**|**bigint**|Lunghezza minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la lunghezza non viene utilizzata.|  
|**source_length_max**|**bigint**|Lunghezza massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la lunghezza non viene utilizzata.|  
|**source_precision_min**|**bigint**|Precisione minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la precisione non viene utilizzata.|  
|**source_precision_max**|**bigint**|Precisione massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la precisione non viene utilizzata.|  
|**source_scale_min**|**int**|Scala minima del tipo di dati nel DBMS di origine. Il valore NULL indica che la scala non viene utilizzata.|  
|**source_scale_max**|**int**|Scala massima del tipo di dati nel DBMS di origine. Il valore NULL indica che la scala non viene utilizzata.|  
|**source_nullable**|**bit**|Indica se il tipo di dati di destinazione supporta i valori Null.|  
|**source_createparams**|**int**|Solo per uso interno.|  
|**destination_dbms**|**sysname**|Indica il nome del sistema DBMS di destinazione. I possibili valori sono i seguenti.<br /><br /> **MSSQLSERVER** = la destinazione è un database di SQL Server.<br /><br /> **ORACLE** = la destinazione è un database Oracle.<br /><br /> **DB2** = la destinazione è un database IBM DB2.<br /><br /> **SYBASE** = la destinazione è un database di Sybase.|  
|**destination_version**|**sysname**|Versione del prodotto del sistema DBMS di destinazione.|  
|**destination_type**|**sysname**|Tipo di dati nel sistema DBMS di destinazione.|  
|**destination_length**|**bigint**|Lunghezza del tipo di dati nel sistema DBMS di destinazione.|  
|**destination_precision**|**bigint**|Precisione del tipo di dati nel sistema DBMS di destinazione.|  
|**destination_scale**|**int**|Scala del tipo di dati nel sistema DBMS di destinazione.|  
|**destination_nullable**|**bit**|Indica se il tipo di dati nel sistema DBMS di destinazione supporta valori Null.|  
|**destination_createparams**|**int**|Solo per uso interno.|  
|**dataloss**|**bit**|Indica se si verifica perdita dei dati durante l'esecuzione del mapping del tipo di dati tra il sistema DBMS di origine e quello di destinazione.|  
|**is_default**|**bit**|Indica se il mapping dei tipi di dati viene utilizzato per impostazione predefinita.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40; Transact-SQL &#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpdatatypemap &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
