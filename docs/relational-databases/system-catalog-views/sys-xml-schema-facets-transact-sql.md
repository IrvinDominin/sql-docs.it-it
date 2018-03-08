---
title: sys.xml_schema_facets (Transact-SQL) | Microsoft Docs
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
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4faca09a59029aeb2f2499b4236e24ea946823e3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysxmlschemafacets-transact-sql"></a>sys.xml_schema_facets (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per facet (restrizione) di una definizione di tipo xml (corrisponde a **xml_types**).  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|ID del componente XML (tipo) a cui appartiene il facet corrente.|  
|**facet_id**|**int**|ID (ordinale in base 1) del facet, univoco all'interno dell'ID del componente.|  
|**kind**|**char(2)**|Tipo di facet:<br /><br /> LG = Lunghezza (Length)<br /><br /> LN = Lunghezza minima (Minimum Length)<br /><br /> LX = Lunghezza massima (Maximum Length)<br /><br /> PT = Pattern (espressione regolare)<br /><br /> EU = Enumerazione (Enumeration)<br /><br /> IN = Valore inclusivo minimo (Minimum Inclusive value)<br /><br /> IX = Valore inclusivo massimo (Maximum Inclusive value)<br /><br /> EN = Valore esclusivo minimo (Minimum Exclusive value)<br /><br /> EX = Valore esclusivo massimo (Maximum Exclusive value)<br /><br /> DT = Totale cifre (Total Digits)<br /><br /> DF = Cifre frazionarie (Fraction Digits)<br /><br /> WS = Normalizzazione di spazi vuoti (White Space normalization)|  
|**kind_desc**|**nvarchar (60)**|Descrizione del tipo di facet:<br /><br /> LENGTH<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = Il facet include un valore fisso predefinito.<br /><br /> 0 = Nessun valore fisso (predefinito)|  
|**Valore**|**nvarchar (4000)**|Valore fisso predefinito del facet.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML Schema &#40; Sistema di tipi XML &#41; Viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
