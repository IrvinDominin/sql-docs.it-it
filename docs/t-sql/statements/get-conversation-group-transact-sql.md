---
title: GET CONVERSATION GROUP (Transact-SQL) | Documenti Microsoft
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
- GET
- CONVERSATION_GROUP_TSQL
- GET_TSQL
- GET_CONVERSATION_GROUP_TSQL
- GET CONVERSATION GROUP
- CONVERSATION GROUP
- GET CONVERSATION
- GET_CONVERSATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GET CONVERSATION GROUP statement
- conversations [Service Broker], groups
ms.assetid: 4da8a855-33c0-43b2-a49d-527487cb3b5c
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 04035a9ccbe406b9fa50b5003ab109c3f1ff997d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="get-conversation-group-transact-sql"></a>GET CONVERSATION GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'identificatore del gruppo di conversazioni per il messaggio successivo da ricevere e blocca il gruppo di conversazioni per la conversazione contenente il messaggio. L'identificatore del gruppo di conversazioni può essere utilizzato per recuperare le informazioni sullo stato della conversazione prima di recuperare il messaggio stesso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
[ WAITFOR ( ]  
   GET CONVERSATION GROUP @conversation_group_id  
      FROM <queue>  
[ ) ] [ , TIMEOUT timeout ]  
[ ; ]  
  
<queue> ::=  
{  
    [ database_name . [ schema_name ] . | schema_name . ] queue_name  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 WAITFOR  
 Specifica che l'istruzione GET CONVERSATION GROUP deve rimanere in attesa dell'arrivo di un messaggio nella coda, se non sono presenti messaggi.  
  
 *@conversation_group_id*  
 Variabile utilizzata per archiviare l'ID del gruppo di conversazioni restituito dall'istruzione GET CONVERSATION GROUP. La variabile deve essere di tipo **uniqueidentifier**. Se non sono disponibili gruppi di conversazione, la variabile viene impostata su NULL.  
  
 FROM  
 Specifica la coda da cui recuperare il gruppo di conversazioni.  
  
 *database_name*  
 Nome del database contenente la coda da cui recuperare il gruppo di messaggi. Se non si *database_name* viene omesso, viene utilizzato il database corrente.  
  
 *schema_name*  
 Nome dello schema proprietario della coda da cui recuperare il gruppo di messaggi. Se non si *schema_name* viene omesso, viene utilizzato lo schema predefinito per l'utente corrente.  
  
 *queue_name*  
 Nome della coda da cui recuperare il gruppo di conversazioni.  
  
 TIMEOUT *timeout*  
 Specifica la quantità di tempo, in millisecondi, che Service Broker attende l'arrivo di un messaggio nella coda. È possibile utilizzare questa clausola solo insieme alla clausola WAITFOR. Se un'istruzione che utilizza l'istruzione WAITFOR non include questa clausola o *timeout* è -1, il tempo di attesa è illimitato. Se il timeout scade, l'istruzione GET CONVERSATION GROUP imposta la  *@conversation_group_id*  variabile su NULL.  
  
## <a name="remarks"></a>Osservazioni  
  
> [!IMPORTANT]  
>  Se l'istruzione GET CONVERSATION GROUP non è la prima istruzione in un batch o stored procedure, l'istruzione precedente deve terminare con un punto e virgola (**;**), il [!INCLUDE[tsql](../../includes/tsql-md.md)] carattere di terminazione.  
  
 Se la coda specificata nell'istruzione GET CONVERSATION GROUP non è disponibile, l'istruzione viene interrotta con un errore [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Questa istruzione restituisce il gruppo di conversazioni successivo in cui tutte le condizioni seguenti sono vere:  
  
-   Il gruppo di conversazioni può essere correttamente bloccato.  
  
-   Nella coda del gruppo di conversazioni sono disponibili messaggi.  
  
-   Il gruppo di conversazioni ha il livello di priorità più elevato di tutti i gruppi di conversazioni che soddisfano i criteri elencati in precedenza. Il livello di priorità di un gruppo di conversazioni corrisponde a quello più elevato assegnato a qualsiasi conversazione membro del gruppo e per cui sono presenti messaggi nella coda.  
  
 Le chiamate all'istruzione GET CONVERSATION GROUP all'interno della stessa transazione potrebbero bloccare più di un gruppo di conversazioni. Se non è disponibile alcun gruppo di conversazioni, l'istruzione restituisce NULL come identificatore del gruppo di conversazioni.  
  
 Se si specifica la clausola WAITFOR, l'istruzione rimane in attesa per il periodo di timeout specificato oppure fino a quando non è disponibile un gruppo di conversazioni. Se la coda viene eliminata durante l'attesa dell'istruzione, viene restituito un errore.  
  
 GET CONVERSATION GROUP non è valida in una funzione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per recuperare un identificatore di un gruppo di conversazioni da una coda, l'utente corrente deve disporre dell'autorizzazione RECEIVE per la coda.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-getting-a-conversation-group-waiting-indefinitely"></a>A. Recupero di un gruppo di conversazioni e attesa illimitata  
 Nell'esempio seguente `@conversation_group_id` viene impostato sull'identificatore del gruppo di conversazioni per il successivo messaggio disponibile in `ExpenseQueue`. Il comando rimane in attesa finché non è disponibile un messaggio.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
WAITFOR (  
 GET CONVERSATION GROUP @conversation_group_id  
     FROM ExpenseQueue  
) ;  
```  
  
### <a name="b-getting-a-conversation-group-waiting-one-minute"></a>B. Recupero di un gruppo di conversazioni e attesa di un minuto  
 Nell'esempio seguente `@conversation_group_id` viene impostato sull'identificatore del gruppo di conversazioni per il successivo messaggio disponibile in `ExpenseQueue`. Se nessun messaggio diventa disponibile entro un minuto, GET CONVERSATION GROUP restituisce il valore di `@conversation_group_id` senza modificarlo.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER  
  
WAITFOR (  
    GET CONVERSATION GROUP @conversation_group_id   
    FROM ExpenseQueue ),  
TIMEOUT 60000 ;  
```  
  
### <a name="c-getting-a-conversation-group-returning-immediately"></a>C. Recupero di un gruppo di conversazioni e restituzione immediata del valore  
 Nell'esempio seguente `@conversation_group_id` viene impostato sull'identificatore del gruppo di conversazioni per il successivo messaggio disponibile in `ExpenseQueue`. Se non è disponibile alcun messaggio, `GET CONVERSATION GROUP` restituisce immediatamente il valore di `@conversation_group_id` senza modificarlo.  
  
```  
DECLARE @conversation_group_id UNIQUEIDENTIFIER ;  
  
GET CONVERSATION GROUP @conversation_group_id  
FROM AdventureWorks.dbo.ExpenseQueue ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DIALOG CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/begin-dialog-conversation-transact-sql.md)   
 [MOVE CONVERSATION &#40;Transact-SQL&#41;](../../t-sql/statements/move-conversation-transact-sql.md)  
  
  
