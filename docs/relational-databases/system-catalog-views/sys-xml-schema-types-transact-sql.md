---
title: sys.xml_schema_types (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_types_TSQL
- xml_schema_types_TSQL
- sys.xml_schema_types
- xml_schema_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_types catalog view
ms.assetid: 441ba49d-f778-4fa1-98c4-ced375a01a34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea20d8e326d006e1a405adffcf73fae6ca1e4473
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715956"
---
# <a name="sysxmlschematypes-transact-sql"></a>sys.xml_schema_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni componente di XML schema che è un tipo **symbol_space** dei **T**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate >**||Eredita le colonne da [xml_schema_components](../../relational-databases/system-catalog-views/sys-xml-schema-components-transact-sql.md).|  
|**is_abstract**|**bit**|1 = Il tipo è un tipo abstract. Tutte le istanze di un elemento di questo tipo è necessario utilizzare **xsi: Type** per indicare un tipo derivato non abstract.<br /><br /> 0 = Il tipo non è abstract (predefinito)|  
|**allows_mixed_content**|**bit**|1 = Il contenuto misto è consentito.<br /><br /> 0 = Il contenuto misto non è consentito (predefinito)|  
|**is_extension_blocked**|**bit**|1 = sostituzione con un'estensione del tipo è bloccata nell'istanza quando l'attributo block nella **complexType** definizione o il **blockDefault** attributo del predecessore \<schema > informazioni sugli elementi è impostata su "extension" o "#all".<br /><br /> 0 = La sostituzione con l'estensione non è bloccata.|  
|**is_restriction_blocked**|**bit**|1 = sostituzione con una restrizione del tipo è bloccata nell'istanza quando l'attributo block nella **complexType** definizione o il **blockDefault** attributo del predecessore \<schema > informazioni sugli elementi è impostata su "restriction" o "#all".<br /><br /> 0 = La sostituzione con la restrizione non è bloccata (predefinito)|  
|**is_final_extension**|**bit**|1 = la derivazione dall'estensione del tipo è bloccata quando l'attributo final nella **complexType** definizione o il **finalDefault** attributo del predecessore \<schema > informazioni sull'elemento elemento viene impostato su "extension" o "#all".<br /><br /> 0 = L'estensione è consentita (predefinito)|  
|**is_final_restriction**|**bit**|1 = la derivazione per restrizione del tipo è bloccata quando l'attributo final nel semplice o **complexType** definizione o il **finalDefault** attributo del predecessore \<schema > elemento elemento informazione è impostato su "restriction" o "#all".<br /><br /> 0 = La restrizione è consentita (predefinito)|  
|**is_final_list_member**|**bit**|1 = Questo tipo semplice non può essere utilizzato come tipo di elemento in un elenco.<br /><br /> 0 = Questo è un tipo complesso oppure il tipo può essere utilizzato come tipo di elemento (predefinito)|  
|**is_final_union_member**|**bit**|1 = Questo tipo semplice non può essere utilizzato come tipo di membro di Tipo unione.<br /><br /> 0 = Questo è un tipo complesso oppure il tipo può essere utilizzato come tipo di membro unione. (predefinito)|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML schema &#40;sistema di tipi XML&#41; viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
