---
title: sp_syspolicy_add_policy_category_subscription (Transact-SQL) | Microsoft Docs
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
- sp_syspolicy_add_policy_category_subscription
- sp_syspolicy_add_policy_category_subscription_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_add_policy_category_subscription
ms.assetid: 4284f550-9a3f-4726-8181-15e407fbf08f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf76a1f42289d52919605c85733304ba58024ca1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spsyspolicyaddpolicycategorysubscription-transact-sql"></a>sp_syspolicy_add_policy_category_subscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge una sottoscrizione di categoria di criteri al database specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@target_type=** ] **'***target_type***'**  
 Tipo di destinazione della sottoscrizione di categoria. *target_type* è **sysname**, è necessario e deve essere impostato su 'DATABASE'.  
  
 [ **@target_object=** ] **'***target_object***'**  
 È il nome del database in cui viene eseguita la sottoscrizione alla categoria. *target_object* è **sysname**ed è obbligatorio.  
  
 [ **@policy_category=** ] **'***policy_category***'**  
 È il nome della categoria di criteri per la sottoscrizione. *policy_category* è **sysname**ed è obbligatorio.  
  
 Per ottenere valori per *policy_category*, eseguire una query sulla vista di sistema syspolicy_policy_categories.  
  
 [ **@policy_category_subscription_id=** ] *policy_category_subscription_id*  
 Identificatore della sottoscrizione di categoria. *policy_category_subscription_id* è **int**e viene restituito come OUTPUT.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 È necessario eseguire sp_syspolicy_add_policy_category_subscription nel contesto del database di sistema msdb.  
  
 Se si specifica una categoria di criteri non esistente, verrà creata una nuova categoria di criteri e la sottoscrizione sarà obbligatoria per tutti i database all'esecuzione della stored procedure. Se la sottoscrizione obbligatoria per la nuova categoria viene successivamente cancellata, la sottoscrizione sarà valida solo per il database specificato come *target_object*. Per altre informazioni sulla modifica dell'impostazione di una sottoscrizione obbligatoria, vedere [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Questa stored procedure viene eseguita nel contesto del proprietario corrente della stessa.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene configurata la sottoscrizione di una categoria di criteri denominata 'Table Naming Policies' da parte del database specificato.  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione basata su criteri di Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  
