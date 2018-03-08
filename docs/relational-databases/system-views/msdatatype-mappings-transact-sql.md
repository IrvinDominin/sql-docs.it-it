---
title: MSdatatype_mappings (Transact-SQL) | Microsoft Docs
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
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f0acbcbf2c70b08b44e0147989fb1f9dcd3e2301
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSdatatype_mappings** vista esegue il mapping di tipi di dati di SQL Server per i tipi di dati utilizzati dai sistemi di gestione di database non SQL Server (DBMS). Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|È il nome del DBMS. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> **MSSQLSERVER**: la destinazione è un database di SQL Server.<br />**ORACLE**: la destinazione è un database Oracle.<br />**DB2**: la destinazione è un database IBM DB2.<br />**SYBASE**: la destinazione è un database di Sybase.|  
|**sql_type**|**nvarchar(128)**|È il tipo di dati di SQL Server.|  
|**dest_type**|**nvarchar(128)**|È il nome del tipo di dati non SQL Server.|  
|**dest_prec**|**bigint**|È la precisione del tipo di dati non SQL Server.|  
|**dest_create_params**|**int**|Solo per uso interno.|  
|**dest_nullable**|**bit**|Indica se il tipo di dati non SQL Server supporta un valore NULL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Replica di database eterogenei](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Tabelle di replica &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
