---
title: MOVE CONVERSATION (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
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
- MOVE_CONVERSATION_TSQL
- MOVE CONVERSATION
- MOVE_TSQL
- MOVE
dev_langs:
- TSQL
helpviewer_keywords:
- moving conversations
- MOVE CONVERSATION statement
- relocating conversations
- conversations [Service Broker], groups
- conversations [Service Broker], moving
ms.assetid: 1da4d2c9-e767-434e-b49b-615711a7f626
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd8c5e548bf45fe4a2fc6bf0638ebb5282981263
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="move-conversation-transact-sql"></a>MOVE CONVERSATION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Sposta una conversazione in un gruppo di conversazioni diverso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
MOVE CONVERSATION conversation_handle  
   TO conversation_group_id  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *conversation_handle*  
 Variabile o costante contenente l'handle di conversazione della conversazione da spostare. *conversation_handle* deve essere di tipo **uniqueidentifier**.  
  
 TO *conversation_group_id*  
 Variabile o costante contenente l'identificatore del gruppo di conversazioni in cui si trova la conversazione da spostare. *conversation_group_id* deve essere di tipo **uniqueidentifier**.  
  
## <a name="remarks"></a>Osservazioni  
 L'istruzione MOVE CONVERSATION Sposta la conversazione specificata da *conversation_handle* per il gruppo di conversazioni identificato da *conversation_group_id*. I dialoghi possono essere reindirizzati solo tra gruppi di conversazioni associati alla stessa coda.  
  
> [!IMPORTANT]  
>  Se l'istruzione MOVE CONVERSATION non è la prima istruzione in un batch o stored procedure, l'istruzione precedente deve terminare con un punto e virgola (**;**), il [!INCLUDE[tsql](../../includes/tsql-md.md)] carattere di terminazione.  
  
 L'istruzione MOVE CONVERSATION blocca il gruppo di conversazioni associato *conversation_handle* e il gruppo di conversazioni specificato da *conversation_group_id* fino a quando la transazione contenente l'istruzione commit o rollback.  
  
 MOVE CONVERSATION non è un'istruzione valida in una funzione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per spostare una conversazione, l'utente corrente deve essere il proprietario della conversazione e del gruppo di conversazioni, un membro del ruolo predefinito del server sysadmin o un membro del ruolo predefinito del database db_owner.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente una conversazione viene spostata in un gruppo di conversazioni diverso.  
  
```  
DECLARE @conversation_handle UNIQUEIDENTIFIER,  
        @conversation_group_id UNIQUEIDENTIFIER ;  
  
SET @conversation_handle =  
    <retrieve conversation handle from database> ;  
SET @conversation_group_id =  
    <retrieve conversation group ID from database> ;  
  
MOVE CONVERSATION @conversation_handle TO @conversation_group_id ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [GET CONVERSATION GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/get-conversation-group-transact-sql.md)   
 [END CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/end-conversation-transact-sql.md)   
 [sys.conversation_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-groups-transact-sql.md)   
 [sys.conversation_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-endpoints-transact-sql.md)  
  
  
