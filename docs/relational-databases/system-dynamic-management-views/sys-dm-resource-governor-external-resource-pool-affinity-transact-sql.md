---
title: Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/13/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- sys.dm_resource_governor_external_resource_pool_affinity_TSQL
- dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_resource_governor_external_resource_pool_affinity
- dm_resource_governor_external_resource_pool_affinity
ms.assetid: e32fac49-5161-47c0-8540-af3fe730c00c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66c22994acf1784f888ebd245429f24c12afa7cb
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43026539"
---
# <a name="sysdmresourcegovernorexternalresourcepoolaffinity-transact-sql"></a>Sys.dm_resource_governor_external_resource_pool_affinity (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Si applica a:**  [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)] [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Restituisce informazioni di affinità della CPU relative alla configurazione di pool di risorse esterne corrente.
  
|Nome colonna|Tipo di dati|Description|
|----------------|---------------|-----------------|
|pool_id|**int**|ID del pool di risorse esterno. Non ammette i valori Null.|
|processor_group|**smallint**|ID del gruppo di processori logici Windows. Non ammette i valori Null.|
|cpu_mask|**bigint**|Maschera binaria che rappresenta la CPU associate a questo pool. Non ammette i valori Null.|
  
## <a name="remarks"></a>Note

I pool creati con affinità `AUTO` non vengono visualizzati in questa vista perché non presentano affinità. Per altre informazioni, vedere la [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) e [ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md) istruzioni.

## <a name="permissions"></a>Permissions

È richiesta l'autorizzazione `VIEW SERVER STATE`.

## <a name="see-also"></a>Vedere anche

[Governance delle risorse per Machine Learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[sys.dm_resource_governor_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pool-affinity-transact-sql.md)

[Opzione di configurazione del server external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[ALTER EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)
