---
title: Sys.system_components_surface_area_configuration (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.system_components_surface_area_configuration_TSQL
- system_components_surface_area_configuration
- system_components_surface_area_configuration_TSQL
- sys.system_components_surface_area_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_components_surface_area_configuration catalog view
ms.assetid: d9920008-3387-4f9e-8f21-47473f2ba04f
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9612341074b70b688d7333c95ebce3acc0ea1706
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="syssystemcomponentssurfaceareaconfiguration-transact-sql"></a>sys.system_components_surface_area_configuration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni oggetto di sistema eseguibile che può essere attivato o disabilitato da un componente di Configurazione superficie di attacco. Per ulteriori informazioni, vedere [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**nome_componente**|**sysname**|Nome del componente, le cui regole di confronto sono Latin1_General_CI_AS_KS_WS. Non può essere NULL.|  
|**database_name**|**sysname**|Database contenente l'oggetto, le cui regole di confronto sono Latin1_General_CI_AS_KS_WS. I possibili valori sono i seguenti:<br /><br /> **master**<br /><br /> **msdb**<br /><br /> **MSSQLSYSTEMRESOURCE**|  
|**schema_name**|**sysname**|Schema contenente l'oggetto, le cui regole di confronto sono Latin1_General_CI_AS_KS_WS. Non può essere NULL.|  
|**object_name**|**sysname**|Nome dell'oggetto. le cui regole di confronto sono Latin1_General_CI_AS_KS_WS. Non può essere NULL.|  
|**state**|**tinyint**|0 = Disabilitato<br /><br /> 1 = Attivato|  
|**type**|**char(2)**|Tipo di oggetto. I possibili valori sono i seguenti:<br /><br /> P = SQL_STORED_PROCEDURE<br /><br /> PC = CLR_STORED_PROCEDURE<br /><br /> FN = SQL_SCALAR_FUNCTION<br /><br /> FS = CLR_SCALAR_FUNCTION<br /><br /> FT = CLR_TABLE_VALUED_FUNCTION<br /><br /> IF = SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> TF = SQL_TABLE_VALUED_FUNCTION<br /><br /> X = EXTENDED_STORED_PROCEDURE|  
|**type_desc**|**nvarchar(60)**|Descrizione del nome del tipo di oggetto.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
