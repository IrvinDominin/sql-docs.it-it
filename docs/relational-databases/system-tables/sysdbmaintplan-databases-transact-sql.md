---
title: sysdbmaintplan_databases (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_databases
- sysdbmaintplan_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_databases system table
ms.assetid: f8413a44-8fcc-4899-84f2-b4afe0f8ec08
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcca0cf0b8653edfab9cec993c04e36987d0e010
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765489"
---
# <a name="sysdbmaintplandatabases-transact-sql"></a>sysdbmaintplan_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa tabella è inclusa per mantenere le informazioni esistenti per le istanze aggiornate da una versione precedente di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive non modificano il contenuto della tabella. Questa tabella è archiviata nel **msdb** database.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID del piano di manutenzione.|  
|**database_name**|**sysname**|Nome del database associato al piano di manutenzione del database.|  
  
  
