---
title: sys.availability_group_listeners (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 48b54435e7737198bd3fd6084ad67ed253d29809
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysavailabilitygrouplisteners-transact-sql"></a>sys.availability_group_listeners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Per ogni sempre nel gruppo di disponibilità, restituisce zero righe, che indica che nessun nome di rete è associato al gruppo di disponibilità o restituisce una riga per ogni configurazione del listener del gruppo di disponibilità in Windows Server Failover Clustering (WSFC) cluster. In questa vista viene visualizzata la configurazione in tempo reale raccolta dal cluster.  
  
> [!NOTE]  
>  Questa vista del catalogo non descrive i dettagli di una configurazione IP, definita nel cluster WSFC.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|ID gruppo di disponibilità (**group_id**) da [availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md).|  
|**listener_id**|**nvarchar(36)**|GUID dall'ID della risorsa del cluster.|  
|**dns_name**|**nvarchar(63)**|Nome di rete configurato (nome host) del listener del gruppo di disponibilità.|  
|**port**|**int**|Numero di porta TCP configurato per il listener del gruppo di disponibilità.<br /><br /> Null = Il listener è stato configurato all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il numero di porta non è stato aggiunto al gruppo di disponibilità. Per aggiungere la porta, utilizzare l'opzione MODIFY LISTENER del [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione.|  
|**is_conformant**|**bit**|Se questa configurazione IP è conforme, uno di:<br /><br /> 1 = Il listener è conforme. Tra gli indirizzi IP (Internet Protocol) esistono sono relazioni "OR". *Conforme a* comprende ogni una configurazione IP che è stata creata con il [CREATE AVAILABILITY GROUP](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione. Inoltre, se una configurazione IP creata all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio tramite Gestione cluster di failover WSFC, ma modificabile tramite l'istruzione Tsql ALTER AVAILABILITY GROUP, la configurazione IP viene qualificata come conforme.<br /><br /> 0 = Il listener non è conforme. In genere, indica un indirizzo IP che non può essere configurato tramite i comandi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che è stato definito direttamente nel cluster WSFC.|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|Eventuali stringhe di configurazione IP del cluster per questo listener. Null = Il listener non dispone di indirizzi IP virtuali. Esempio:<br /><br /> Indirizzo IPv4: `65.55.39.10`.<br /><br /> Indirizzo IPv6: `2001::4898:23:1002:20f:1fff:feff:b3a3`.|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e DMV di Gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Viste del catalogo dei gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Monitorare gruppi di disponibilità &#40; Transact-SQL &#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Gruppi di disponibilità AlwaysOn di &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
