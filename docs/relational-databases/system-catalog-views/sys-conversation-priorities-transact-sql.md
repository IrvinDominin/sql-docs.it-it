---
title: Sys. conversation_priorities (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- conversation_priorities_TSQL
- conversation_priorities
- sys.conversation_priorities_TSQL
- sys.conversation_priorities
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], priorities
- Service Broker, conversations
- sys.conversation_priorities catalog view
ms.assetid: 7cbb9171-3310-4aae-8458-755c882d6462
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cf94358d5d4f06f787546ab98a8cbfcab2693bcb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846289"
---
# <a name="sysconversationpriorities-transact-sql"></a>sys.conversation_priorities (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni priorità di conversazione creata nel database corrente, come illustrato nella tabella seguente: 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|Priority_id|**int**|Numero che identifica in modo univoco la priorità di conversazione. Non ammette i valori Null.|  
|NAME|**sysname**|Nome della priorità di conversazione. Non ammette i valori Null.|  
|service_contract_id|**int**|Identificatore del contratto specificato per la priorità di conversazione. Questa colonna può essere unita alla colonna service_contract_id in sys.service_contracts. Ammette valori Null.|  
|local_service_id|**int**|Identificatore del servizio specificato come servizio locale per la priorità di conversazione. Questa colonna può essere unita alla colonna service_id in sys.services. Ammette valori Null.|  
|remote_service_name|**nvarchar(256)**|Nome del servizio specificato come servizio remoto per la priorità di conversazione. Ammette valori Null.|  
|priority|**tinyint**|Livello di priorità specificato nella priorità di conversazione. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono elencate le priorità di conversazione utilizzando join per mostrare i nomi del contratto e del servizio locale.  
  
```  
SELECT scp.name AS priority_name,  
       ssc.name AS contract_name,  
       ssvc.name AS local_service_name,  
       scp.remote_service_name,  
       scp.priority AS priority_level  
FROM sys.conversation_priorities AS scp  
    INNER JOIN sys.service_contracts AS ssc  
       ON scp.service_contract_id = ssc.service_contract_id  
    INNER JOIN sys.services AS ssvc  
       ON scp.local_service_id = ssvc.service_id  
ORDER BY priority_name, contract_name,  
         local_service_name, remote_service_name;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [sys.services &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)   
 [sys.service_contracts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-service-contracts-transact-sql.md)  
  
  
