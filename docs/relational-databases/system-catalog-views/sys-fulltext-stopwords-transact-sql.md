---
title: Sys.fulltext_stopwords (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fulltext_stopwords_TSQL
- fulltext_stopwords
- sys.fulltext_stopwords
- sys.fulltext_stopwords_TSQL
dev_langs: TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stopwords
- sys.fulltext_stopwords catalog view
- stopwords [full-text search]
ms.assetid: 79787bb7-d729-448e-b56a-0a467bbb304f
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 90bc334c7b42c40e7b5d31e6cdd67458775e2f1a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysfulltextstopwords-transact-sql"></a>sys.fulltext_stopwords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Contiene una riga per ogni parola non significativa per tutti gli elenchi di parole non significative nel database.  
 
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**stoplist_id**|**int**|ID dell'elenco di parole non significative cui **stopword** appartiene. Tale ID è univoco all'interno del database.|  
|**parola non significativa**|**nvarchar (64)**|Termine da considerare per una corrispondenza della parola non significativa.|  
|**lingua**|**sysname**|È il valore dell'alias in [Sys. fulltext_languages](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)corrispondente al valore dell'identificatore delle impostazioni locali (**LCID**), o è la rappresentazione di stringa dell'identificatore LCID numerico.|  
|**ID_Lingua**|**int**|Identificatore LCID utilizzato per il word breaking.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Configurare e gestire parole non significative ed elenchi per la ricerca Full-Text](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_system_stopwords &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-system-stopwords-transact-sql.md)  
  
  