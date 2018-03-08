---
title: sys.sysprotects (Transact-SQL) | Microsoft Docs
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
- sysprotects
- sys.sysprotects_TSQL
- sys.sysprotects
- sysprotects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysprotects compatibility view
- sysprotects system table
ms.assetid: 49c9658d-fb51-4c77-94a0-fba699b0102d
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: abde43e1d699c32b2a9cd21459d823692952e059
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="syssysprotects-transact-sql"></a>sys.sysprotects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Include informazioni sulle autorizzazioni associate agli account di sicurezza nel database tramite le istruzioni GRANT e DENY.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID dell'oggetto a cui sono applicate le autorizzazioni.|  
|**uid**|**smallint**|ID dell'utente o gruppo a cui sono applicate le autorizzazioni. Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
|**action**|**tinyint**|Le possibili autorizzazioni sono le seguenti:<br /><br /> 26 = REFERENCES<br /><br /> 178 = CREATE FUNCTION<br /><br /> 193 = SELECT<br /><br /> 195 = INSERIMENTO<br /><br /> 196 = DELETE<br /><br /> 197 = UPDATE<br /><br /> 198 = CREATE TABLE<br /><br /> 203 = CREATE DATABASE<br /><br /> 207 = CREATE VIEW<br /><br /> 222 = CREATE PROCEDURE<br /><br /> 224 = EXECUTE<br /><br /> 228 = BACKUP DATABASE<br /><br /> 233 = CREATE DEFAULT<br /><br /> 235 = BACKUP LOG<br /><br /> 236 = CREATE RULE|  
|**protecttype**|**tinyint**|I possibili valori sono i seguenti:<br /><br /> 204 = GRANT_W_GRANT<br /><br /> 205 = GRANT<br /><br /> 206 = DENY|  
|**colonne**|**varbinary(8000)**|Mappa di bit delle colonne a cui sono applicate le istruzioni SELECT e UPDATE.<br /><br /> Bit 0 = tutte le colonne.<br /><br /> Bit 1 = le autorizzazioni vengono applicate alla colonna specifica.<br /><br /> NULL = nessuna informazione.|  
|**GRANTOR**|**smallint**|ID dell'utente che ha eseguito le autorizzazioni GRANT o DENY. Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema di viste di sistema &#40; Transact-SQL &#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
