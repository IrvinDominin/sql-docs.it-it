---
title: sys.sysperfinfo (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92d1cb29e339017f13c5b784f2b1459cf1a19432
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] rappresentazione dei contatori delle prestazioni interni che è possibile visualizzare tramite Monitor di sistema di Windows.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar(128)**|Nome dell'oggetto prestazione, ad esempio **SQLServer:LockManager** o **SQLServer:BufferManager**.|  
|**counter_name**|**nchar(128)**|Nome del contatore delle prestazioni all'interno dell'oggetto, ad esempio **richieste di pagine** o **richieste di blocco**.|  
|**nome_istanza**|**nchar(128)**|Istanza denominata del contatore. Ad esempio, sono disponibili contatori gestiti per ogni tipo di blocco, ad esempio **tabella**, **pagina**, **chiave**e così via. Il nome dell'istanza consente di contraddistinguere contatori simili.|  
|**cntr_value**|**bigint**|Valore effettivo del contatore. Spesso si tratta di un contatore a incremento progressivo costante che conta le occorrenze dell'evento dell'istanza.|  
|**cntr_type**|**int**|Tipo di contatore definito dall'architettura di controllo delle prestazioni di Windows.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
