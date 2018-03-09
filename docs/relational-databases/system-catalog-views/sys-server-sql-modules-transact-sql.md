---
title: Sys.server_sql_modules (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.server_sql_modules
- sys.server_sql_modules_TSQL
- server_sql_modules_TSQL
- server_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_sql_modules catalog view
ms.assetid: 9ef9a8b9-c470-4a61-b0c4-ee24ad871d63
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2056568390fc8fa7ca7e03ee7df8ace39627ca5f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysserversqlmodules-transact-sql"></a>sys.server_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene il set di moduli SQL per i trigger a livello di server di tipo TR. È possibile unire in join questa relazione a sys.server_triggers. La tupla (object_id) è la chiave della relazione.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|È un riferimento FOREIGN KEY al trigger di livello server in cui il modulo è definito.|  
|**definizione**|**nvarchar(max)**|Testo SQL che definisce il modulo.<br /><br /> NULL = Crittografato.|  
|**uses_ansi_nulls**|**bit**|Il modulo è stato creato con l'opzione ANSI NULLS impostata su ON.|  
|**uses_quoted_identifier**|**bit**|Il modulo è stato creato con l'opzione QUOTED IDENTIFIER impostata su ON.|  
|**execute_as_principal_id**|**int**|ID dell'entità server EXECUTE AS.<br /><br /> NULL per impostazione predefinita o se EXECUTE AS CALLER<br /><br /> ID dell'entità specificata se eseguire AS SELF EXECUTE AS entità-2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
