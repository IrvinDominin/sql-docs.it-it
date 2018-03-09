---
title: sp_helptracertokenhistory (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helptracertokenhistory_TSQL
- sp_helptracertokenhistory
helpviewer_keywords:
- sp_helptracertokenhistory
ms.assetid: 96910d1c-be76-43eb-9c93-4477e6761749
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ad9a67f66222ff87753056ea1b27b2ad83e6e8d
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelptracertokenhistory-transact-sql"></a>sp_helptracertokenhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni dettagliate sulla latenza per i token di traccia specificati. Per ogni Sottoscrittore, viene restituita una riga. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione o nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helptracertokenhistory [ @publication = ] 'publication'   
        , [ @tracer_id = ] tracer_id  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication=** ] **'***pubblicazione***'**  
 Nome della pubblicazione in cui è stato inserito il token di traccia. *pubblicazione* è **sysname**, non prevede alcun valore predefinito.  
  
 [  **@tracer_id=** ] *tracer_id*  
 È l'ID del token di traccia nel [MStracer_tokens &#40; Transact-SQL &#41; ](../../relational-databases/system-tables/mstracer-tokens-transact-sql.md) tabella per cui cronologia vengono restituite informazioni. *tracer_id* è **int**, non prevede alcun valore predefinito.  
  
 [  **@publisher=** ] **'***publisher***'**  
 Nome del server di pubblicazione. *server di pubblicazione* è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro deve essere specificato solo per non[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i server di pubblicazione.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nome del database di pubblicazione. *publisher_db* è **sysname**, con un valore predefinito null. Questo parametro viene ignorato se la stored procedure viene eseguita nel server di pubblicazione.  
  
## <a name="result-set"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**distributor_latency**|**bigint**|Numero di secondi che intercorrono tra il commit del record del token di traccia nel server di pubblicazione e il commit nel server di distribuzione.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore che ha ricevuto il token di traccia.|  
|**subscriber_db**|**sysname**|Nome del database di sottoscrizione in cui è stato inserito il record del token di traccia.|  
|**subscriber_latency**|**bigint**|Numero di secondi che intercorrono tra il commit del record del token di traccia nel server di distribuzione e il commit nel Sottoscrittore.|  
|**overall_latency**|**bigint**|Numero di secondi che intercorrono tra il commit del record del token di traccia nel server di pubblicazione e il commit nel Sottoscrittore.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_helptracertokenhistory** viene utilizzata nella replica transazionale.  
  
 Eseguire [sp_helptracertokens &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md) per ottenere un elenco dei token di traccia per la pubblicazione.  
  
 Un valore NULL nel set di risultati indica che non è stato possibile calcolare le statistiche relative alla latenza, perché il token di traccia non è stato ricevuto nel server di distribuzione o in uno dei Sottoscrittori.  
  
## <a name="example"></a>Esempio  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-helptracertokenhistor_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server, il **db_owner** ruolo predefinito del database nel database di pubblicazione o **db_owner** predefiniti del database o  **replmonitor** ruoli nel database di distribuzione possono eseguire **sp_helptracertokenhistory**.  
  
## <a name="see-also"></a>Vedere anche  
 [Misurare la latenza e convalidare le connessioni per la replica transazionale](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)   
 [sp_deletetracertokenhistory &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md)  
  
  
