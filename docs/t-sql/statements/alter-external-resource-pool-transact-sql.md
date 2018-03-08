---
title: MODIFICARE il POOL di risorse esterne (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 11/13/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL RESOURCE POOL statement
ms.assetid: 634c327d-971b-49ba-b8a2-e243a04040db
caps.latest.revision: 
author: jeannt
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb4073a8114e953dc9df87614a63e074ab8c9683
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-external-resource-pool-transact-sql"></a>MODIFICARE il POOL di risorse esterne (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
**Si applica a:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] e [!INCLUDE[sssql17-md](../../includes/sssql17-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

Modifica di un pool di Resource Governor esterna che specifica le risorse che possono essere utilizzate da processi esterni. 

+ Per [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)] in [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)], determina il pool esterno `rterm.exe`, `BxlServer.exe`e altri processi derivati.

+ Per [!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] in SQL Server 2017, il pool esterno determina i processi R elencati per la versione precedente, nonché `python.exe`, `BxlServer.exe`e altri processi derivati.

 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).

## <a name="syntax"></a>Sintassi

```sql
ALTER EXTERNAL RESOURCE POOL { pool_name | "default" }
[ WITH (
    [ MAX_CPU_PERCENT = value ]
    [ [ , ] AFFINITY CPU =
            {
                AUTO
              | ( <cpu_range_spec> )
              | NUMANODE = (( <NUMA_node_id> )
            } ]   
    [ [ , ] MAX_MEMORY_PERCENT = value ]
    [ [ , ] MAX_PROCESSES = value ]
    )
]
[ ; ]
  
<CPU_range_spec> ::=
{ CPU_ID | CPU_ID  TO CPU_ID } [ ,...n ]
```  
  
## <a name="arguments"></a>Argomenti

{ *pool_name* | "default"}  
È il nome di un pool di risorse esterne definite dall'utente esistente o il pool di risorse esterno predefinito che viene creato quando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è installato.
"default" deve essere racchiuso tra virgolette ("") o parentesi quadre ([]), se utilizzata con `ALTER EXTERNAL RESOURCE POOL` per evitare conflitti con `DEFAULT`, che è un sistema parola riservata.


MAX_CPU_PERCENT =*valore*  
Specifica la media della CPU larghezza di banda massima che possono ricevere tutte le richieste nel pool di risorse esterne quando è presente una contesa di CPU. *valore* è un intero con valore predefinito è pari a 100. L'intervallo consentito per *valore* è compreso tra 1 e 100.


AFFINITÀ {CPU = AUTO | ( \<CPU_range_spec >) | NUMANODE = (\<NUMA_node_range_spec >)}  
Collegare il pool di risorse esterne alla CPU specifiche. Il valore predefinito è AUTO.

AFFINITÀ di CPU = **(** \<CPU_range_spec > **)** pool di risorse esterno viene eseguito il mapping di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU identificate il CPU_IDs specificato. Quando si utilizza AFFINITY NUMANODE = **(** \<NUMA_node_range_spec > **)**, il pool di risorse esterne viene creata un'affinità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU fisiche corrispondenti per il dato NUMA nodo o all'intervallo di nodi.


MAX_MEMORY_PERCENT =*valore*  
Specifica la memoria totale del server utilizzabile dalle richieste nel pool di risorse esterne. *valore* è un intero con valore predefinito è pari a 100. L'intervallo consentito per *valore* è compreso tra 1 e 100.


MAX_PROCESSES =*valore*  
Specifica il numero massimo di processi consentiti per il pool di risorse esterne. Specificare 0 per impostare una soglia illimitata per il pool, che successivamente è associato solo dalle risorse di computer. Il valore predefinito è 0.

## <a name="remarks"></a>Osservazioni

Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] implementa il pool di risorse quando si esegue il [ALTER RESOURCE GOVERNOR RECONFIGURE](../../t-sql/statements/alter-resource-governor-transact-sql.md) istruzione.

Per informazioni generali sui pool di risorse, vedere [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md), [Sys. resource_governor_external_resource_pools &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md), e [Sys.dm resource_governor_external_resource_pool_affinity &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md).  

Per informazioni specifiche per l'utilizzo del pool di risorse esterno per definire i processi di machine learning, vedere [governance delle risorse per machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)...
## <a name="permissions"></a>Permissions

È richiesta l'autorizzazione `CONTROL SERVER`.

## <a name="examples"></a>Esempi

L'istruzione seguente modifica un pool esterno, limitare l'utilizzo della CPU del 50% e la memoria massima sul 25% della memoria disponibile nel computer.
  
```sql
ALTER EXTERNAL RESOURCE POOL ep_1
WITH (
    MAX_CPU_PERCENT = 50
    , AFFINITY CPU = AUTO
    , MAX_MEMORY_PERCENT = 25
);
GO
ALTER RESOURCE GOVERNOR RECONFIGURE;
GO
```

## <a name="see-also"></a>Vedere anche

[Governance delle risorse per machine learning in SQL Server](../../advanced-analytics/r/resource-governance-for-r-services.md)

[Opzione di configurazione del server external scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)

[CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)

[DROP EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-external-resource-pool-transact-sql.md)

[ALTER RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-resource-pool-transact-sql.md)

[CREATE WORKLOAD GROUP &#40; Transact-SQL &#41;](../../t-sql/statements/create-workload-group-transact-sql.md)

[Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)

[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-resource-governor-transact-sql.md) 
