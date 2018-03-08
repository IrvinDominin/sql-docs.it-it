---
title: sysmail_delete_principalprofile_sp (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_delete_principalprofile_sp_TSQL
- sysmail_delete_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_principalprofile_sp
ms.assetid: 8fc14700-e17a-4073-9a96-7fc23e775c69
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 204daab0d90b050237d864c23729cf2544d68fe4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sysmaildeleteprincipalprofilesp-transact-sql"></a>sysmail_delete_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove l'autorizzazione per un utente o ruolo del database per l'utilizzo di un profilo di Posta elettronica database pubblico o privato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_delete_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@principal_id** = ] *principal_id*  
 È l'ID dell'utente del database o del ruolo nel **msdb** database per l'associazione da eliminare. *principal_id* è **int**, con un valore predefinito è NULL. Per rendere un profilo pubblico in profilo privato, fornire l'ID dell'entità **0** o il nome dell'entità **'public'**. Entrambi *principal_id* o *principal_name* deve essere specificato.  
  
 [  **@principal_name**  =] **'***principal_name***'**  
 È il nome dell'utente del database o del ruolo nel **msdb** database per l'associazione da eliminare. *principal_name* è **sysname**, con un valore predefinito è NULL. Per rendere un profilo pubblico in profilo privato, fornire l'ID dell'entità **0** o il nome dell'entità **'public'**. Entrambi *principal_id* o *principal_name* deve essere specificato.  
  
 [ **@profile_id** = ] *profile_id*  
 ID del profilo per l'associazione da eliminare. *profile_id* è **int**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
 [ **@profile_name** = ] **'***profile_name***'**  
 Nome del profilo per l'associazione da eliminare. *profile_name* è **sysname**, con un valore predefinito è NULL. Entrambi *profile_id* o *profile_name* deve essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Per trasformare un profilo pubblico in profilo privato, immettere **'public'** per il nome dell'entità o **0** per l'id dell'entità.  
  
 Prestare attenzione quando si rimuovono le autorizzazioni per il profilo privato predefinito di un utente o per il profilo pubblico predefinito. Quando non è disponibile alcun profilo predefinito **sp_send_dbmail** richiede il nome di un profilo come argomento. Rimozione di un profilo predefinito potrebbe pertanto provocare chiamate a **sp_send_dbmail** esito negativo. Per ulteriori informazioni, vedere [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).  
  
 La stored procedure **sysmail_delete_principalprofile_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata l'eliminazione dell'associazione tra il profilo **AdventureWorks Administrator** e l'account di accesso **ApplicationUser** nel **msdb** database.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Posta elettronica database Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
