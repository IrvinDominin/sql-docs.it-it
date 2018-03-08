---
title: sys.sysfiles (Transact-SQL) | Microsoft Docs
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
- sysfiles
- sys.sysfiles_TSQL
- sys.sysfiles
- sysfiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysfiles system table
- sys.sysfiles compatibility view
ms.assetid: 3b47f38d-1cff-404d-89d3-9342c451c802
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46f241ec9402dc275f265419344bc2e3ccf4d007
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="syssysfiles-transact-sql"></a>sys.sysfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni file di un database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numero di identificazione del file, univoco per ogni database.|  
|**groupid**|**smallint**|Numero di identificazione del filegroup.|  
|**size**|**int**|Dimensioni del file in pagine da 8 KB.|  
|**maxsize**|**int**|Dimensioni massime del file espresse in pagine da 8 KB.<br /><br /> 0 = Nessun aumento.<br /><br /> -1 = La dimensione del file aumenterà finché il disco è pieno.<br /><br /> 268435456 = La dimensione del file di log aumenterà fino al valore massimo di 2 TB.<br /><br /> Nota: I database che vengono aggiornati con una dimensione del file di log senza limiti restituirà -1 per la dimensione massima del file di log.|  
|**growth**|**int**|Aumento delle dimensioni del database. Può essere il numero di pagine o la percentuale delle dimensioni del file, a seconda del valore di **stato**.<br /><br /> 0 = Nessun aumento.|  
|**status**|**int**|Bit di stato per il **crescita** valore in megabyte (MB) o kilobyte (KB).<br /><br /> 0x2 = File del disco.<br /><br /> 0x40 = File di log.<br /><br /> 0x100000 = Aumento. Questo valore indica una percentuale e non il numero di pagine.|  
|**perf**|**int**|Riservato.|  
|**name**|**sysname**|Nome logico del file.|  
|**filename**|**nvarchar(260)**|Nome del dispositivo fisico, incluso il percorso completo del file.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
