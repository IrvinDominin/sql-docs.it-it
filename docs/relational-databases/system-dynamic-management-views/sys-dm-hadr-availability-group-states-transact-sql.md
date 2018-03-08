---
title: sys.dm_hadr_availability_group_states (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b4d6dbddbf0fb211335789eefeff5f2a392f2d59
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmhadravailabilitygroupstates-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni sempre nel gruppo di disponibilità che dispone di una replica di disponibilità nell'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ogni riga visualizza gli stati che definiscono l'integrità di un determinato gruppo di disponibilità.  
  
> [!NOTE]  
>  Per ottenere l'elenco completo dei, eseguire una query di [availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) vista del catalogo.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|Identificatore univoco del gruppo di disponibilità.|  
|**primary_replica**|**varchar(128)**|Nome dell'istanza del server che ospita la replica primaria corrente.<br /><br /> Null = Non la replica primaria o impossibile comunicare con il cluster di failover WSFC.|  
|**primary_recovery_health**|**tinyint**|Indica l'integrità di recupero della replica primaria, uno di:<br /><br /> 0 = in corso<br /><br /> 1 = Online<br /><br /> NULL<br /><br /> Nelle repliche secondarie di **primary_recovery_health** colonna è NULL.|  
|**primary_recovery_health_desc**|**nvarchar(60)**|Descrizione di **primary_replica_health**, uno di:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|Indica lo stato di ripristino di una replica secondaria, uno di:<br /><br /> 0 = in corso<br /><br /> 1 = Online<br /><br /> NULL<br /><br /> Nella replica primaria, il **secondary_recovery_health** colonna è NULL.|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|Descrizione di **secondary_recovery_health**, uno di:<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|Riflette un rollup del **synchronization_health** di tutte le repliche di disponibilità nel gruppo di disponibilità. Di seguito sono i valori possibili e le relative descrizioni.<br /><br /> 0: non integro. Nessuna delle repliche di disponibilità è associato un **synchronization_health** (2 = HEALTHY).<br /><br /> 1: parzialmente integro. Il valore relativo all'integrità di sincronizzazione di alcune repliche di disponibilità, ma non di tutte, è integro.<br /><br /> 2: integro. Il valore relativo all'integrità di sincronizzazione di ogni replica di disponibilità è integro.<br /><br /> Per informazioni sullo stato di sincronizzazione di replica, vedere il **synchronization_health** colonna [hadr_availability_replica_states &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md).|  
|**synchronization_health_desc**|**nvarchar(60)**|Descrizione di **synchronization_health**, uno di:<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare gruppi di disponibilità &#40; Transact-SQL &#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Gruppi di disponibilità Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Funzioni e viste a gestione dinamica &#40; gruppi di disponibilità AlwaysOn Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
