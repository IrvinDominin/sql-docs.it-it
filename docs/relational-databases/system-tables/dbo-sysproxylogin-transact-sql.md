---
title: dbo.sysproxylogin (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysproxylogin_TSQL
- sysproxylogin_TSQL
- dbo.sysproxylogin
- sysproxylogin
dev_langs:
- TSQL
helpviewer_keywords:
- sysproxylogin system table
ms.assetid: 433d33cb-bdf2-47bb-af78-2a40b7c8dfce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00a3b3b53bcede7f43aad556465358b957331f45
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47770249"
---
# <a name="dbosysproxylogin-transact-sql"></a>dbo.sysproxylogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registra quali account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono associati ad ogni account proxy di SQL Server Agent. Questa tabella è archiviata nel **msdb** database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|ID dell'account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Questo valore corrisponde al **proxy_id** colonna il **sysproxies** tabella.|  
|**sid**|**varbinary(85)**|Microsoft Windows *identificatore di protezione* per l'account di accesso di SQL Server.|  
|**principal_id**|**int**|ID dell'utente o del gruppo che dispone dell'autorizzazione per utilizzare l'account proxy per un processo del sottosistema specificato.|  
|**flags**|**int**|Tipo di account di accesso:<br /><br /> **0** = utente di Windows o un gruppo e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso.<br /><br /> **1**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruolo predefinito del sistema<br /><br /> **2** = **msdb** ruolo predefinito del database|  
  
## <a name="remarks"></a>Note  
 Solo i membri del **sysadmin** ruolo predefinito del server può accedere a questa tabella.  
  
## <a name="see-also"></a>Vedere anche  
 [dbo.sysproxies &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysproxies-transact-sql.md)  
  
  
