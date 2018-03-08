---
title: ELIMINARE il POOL di risorse esterne (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2016
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
- DROP EXTERNAL RESOURCE POOL
- DROP_EXTERNAL_RESOURCE_POOL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL RESOURCE POOL statement
ms.assetid: e2fa01bd-96ff-4ea9-bb08-6cb6b6adf68c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: edd6e956bc9453317c928a099469e65ddf5e0e0f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drop-external-resource-pool-transact-sql"></a>ELIMINARE il POOL di risorse esterne (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Elimina un pool di risorse esterne di Resource Governor consentono di definire le risorse per i processi esterni. Per R Services determina il pool esterno `rterm.exe`, `BxlServer.exe`e altri processi derivati. Vengono creati pool di risorse esterne utilizzando [CREATE EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-resource-pool-transact-sql.md) e modificati tramite [ALTER EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-external-resource-pool-transact-sql.md).  
  
 ![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
DROP EXTERNAL RESOURCE POOL pool_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *pool_name*  
 Il nome del pool di risorse esterni da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 Se contiene gruppi di carico di lavoro non è possibile eliminare un pool di risorse esterne.  
  
 Non è possibile eliminare pool predefiniti o interni di Resource Governor.  
  
 La riconfigurazione n  
  
 Per l'esecuzione di istruzioni DDL, è consigliabile avere familiarità con gli stati di Resource Governor. Per ulteriori informazioni, vedere [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione `CONTROL SERVER`.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il pool di risorse esterno denominato `ex_pool`.  
  
```  
DROP EXTERNAL RESOURCE POOL ex_pool;  
GO  
ALTER RESOURCE GOVERNOR RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Opzione di configurazione Server External scripts enabled](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [Servizi R per SQL Server](../../advanced-analytics/r-services/sql-server-r-services.md)   
 [Problemi noti per SQL Server R Services](../../advanced-analytics/r-services/known-issues-for-sql-server-r-services.md)   
 [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)   
 [ALTER EXTERNAL RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/alter-external-resource-pool-transact-sql.md)   
 [DROP WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/drop-workload-group-transact-sql.md)   
 [DROP RESOURCE POOL &#40; Transact-SQL &#41;](../../t-sql/statements/drop-resource-pool-transact-sql.md)  
  
  
