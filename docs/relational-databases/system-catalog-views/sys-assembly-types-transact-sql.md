---
title: sys.assembly_types (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- assembly_types
- sys.assembly_types
- sys.assembly_types_TSQL
- assembly_types_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.assembly_types catalog view
ms.assetid: 35f0384f-7a6d-41b1-9461-f1406d68f317
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f4411b518085338e18b01697fd445ca1d18e7ce1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysassemblytypes-transact-sql"></a>sys.assembly_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni tipo definito dall'utente che viene definito da un assembly CLR. Nell'esempio **sys.assembly_types** vengono visualizzati nell'elenco delle colonne ereditate (vedere [Sys. Types &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)) dopo **rule_object_id**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|ID dell'assembly da cui è stato creato questo tipo.|  
|**assembly_class**|**sysname**|Nome della classe all'interno dell'assembly che definisce questo tipo.|  
|**is_binary_ordered**|**bit**|L'ordinamento dei byte di questo tipo equivale all'ordinamento tramite gli operatori di confronto sul tipo.|  
|**is_fixed_length**|**bit**|La lunghezza del tipo corrisponde sempre a max_length.|  
|**prog_id**|**nvarchar(40)**|ProgID del tipo esposto a COM.|  
|**assembly_qualified_name**|**nvarchar(4000)**|Nome di tipo completo dell'assembly. Il nome è in un formato appropriato per essere passato a Type.GetType().|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Tipi scalari, viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)  
  
  
