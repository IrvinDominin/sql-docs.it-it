---
title: dbo.sysproxies (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.sysproxies_TSQL
- sysproxies_TSQL
- dbo.sysproxies
- sysproxies
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxies system table
ms.assetid: a73da875-be22-45fc-b5e2-ea7ebd48e2d6
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9a1e16809177b6bec502493d03527343fecf6923
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="dbosysproxies-transact-sql"></a>dbo.sysproxies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Definisce gli attributi di un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID dell'account proxy.|  
|**name**|**sysname**|ID dell'account proxy.|  
|**credential_id**|**int**|ID delle credenziali utilizzate dall'account proxy.|  
|**enabled**|**tinyint**|Stato dell'account proxy.<br /><br /> **0** = Disabled. **1** = abilitato.|  
|**description**|**nvarchar(512)**|Descrizione immessa dall'utente al momento della creazione dell'account proxy.|  
|**user_sid**|**varbinary(85)**|Microsoft Windows *identificatore di protezione* dell'utente o gruppo associato alle credenziali proxy.|  
|**credential_date_created**|**datetime**|Data e ora di creazione delle credenziali.|  
  
## <a name="remarks"></a>Osservazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server può accedere il **sysproxies** tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [dbo.sysproxylogin &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxylogin-transact-sql.md)   
 [dbo.sysproxysubsystem &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxysubsystem-transact-sql.md)   
 [dbo.syssubsystems &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-syssubsystems-transact-sql.md)  
  
  
