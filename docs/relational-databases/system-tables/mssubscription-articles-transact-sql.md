---
title: MSsubscription_articles (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSsubscription_articles
- MSsubscription_articles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_articles system table
ms.assetid: dbc1737f-261e-4017-b9cd-703b9fc4ac78
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a5f1530091601cb241da7f1e4b1d48e02f699497
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="mssubscriptionarticles-transact-sql"></a>MSsubscription_articles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSsubscription_articles** tabella contiene informazioni relative agli articoli di una sottoscrizione in coda. Questa tabella viene popolata solo per i tipi di replica ad aggiornamento in coda e ad aggiornamento immediato sostituito dall'aggiornamento in coda in caso di errore.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**agent_id**|**int**|ID dell'agente che gestisce l'articolo.|  
|**artid**|**int**|L'ID dell'articolo di **sysarticles** tabella.|  
|**article**|**sysname**|Il nome dell'articolo di **sysarticles** tabella.|  
|**dest_table**|**sysname**|Il nome della tabella di destinazione dal **sysarticles** tabella.|  
|**proprietario**|**sysname**|Proprietario della sottoscrizione.|  
|**cft_table**|**sysname**|Nome della tabella dei conflitti dell'articolo per il tipo di replica ad aggiornamento in coda.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
