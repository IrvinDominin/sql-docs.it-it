---
title: dbo.sysnotifications (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysnotifications_TSQL
- sysnotifications
- sysnotifications_TSQL
- dbo.sysnotifications
dev_langs:
- TSQL
helpviewer_keywords:
- sysnotifications system table
ms.assetid: c5150d18-e8b7-48a7-ada7-77c583af6e41
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2622328b29141e145a9877952b9d2a97c0994ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735759"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni notifica.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID dell'avviso.|  
|**operator_id**|**int**|ID dell'operatore a cui deve essere inviata la notifica.|  
|**notification_method**|**tinyint**|Metodo di notifica:<br /><br /> **1** = posta elettronica<br /><br /> **2** = cercapersone<br /><br /> **4** = **netsend**<br /><br /> **7** = all|  
  
  
