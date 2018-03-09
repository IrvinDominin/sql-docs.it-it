---
title: sp_grantdbaccess (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
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
- sp_grantdbaccess
- sp_grantdbaccess_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grantdbaccess
ms.assetid: 3eb09513-03f1-42f8-9917-3a1f3a579bec
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e8e67cc8f4672a650f7909fc71a759c3a856fcf
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="spgrantdbaccess-transact-sql"></a>sp_grantdbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiunge un utente del database al database corrente.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare [CREATE USER](../../t-sql/statements/create-user-transact-sql.md) invece.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_grantdbaccess [ @loginame = ] 'login'  
    [ , [ @name_in_db = ] 'name_in_db' [ OUTPUT ] ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@loginame =** ] **'***accesso* **'**  
 Nome del gruppo di Windows, dell'account di accesso di Windows oppure dell'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale eseguire il mapping al nuovo utente del database. Nomi dei gruppi di Windows e gli account di accesso di Windows devono essere qualificati con un nome di dominio di Windows nel formato *dominio*\\*accesso*, ad esempio **LONDON\Joeb**. Sull'account di accesso non può essere già stato eseguito il mapping a un utente nel database. *account di accesso* è un **sysname**, non prevede alcun valore predefinito.  
  
 [  **@name_in_db=**] **'***name_in_db***'** [ **OUTPUT**]  
 Nome del nuovo utente del database. *name_in_db* è una variabile OUTPUT con un tipo di dati **sysname**e un valore predefinito è NULL. Se non specificato, *accesso* viene utilizzato. Se specificato come variabile OUTPUT con valore NULL,  **@name_in_db**  è impostato su *accesso*. *name_in_db* non deve essere già presente nel database corrente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_grantdbaccess** chiama CREATE USER, che supporta opzioni aggiuntive. Per informazioni sulla creazione di utenti del database, vedere [CREATE USER &#40; Transact-SQL &#41; ](../../t-sql/statements/create-user-transact-sql.md). Per rimuovere un utente del database da un database, utilizzare [DROP USER](../../t-sql/statements/drop-user-transact-sql.md).  
  
 **sp_grantdbaccess** non può essere eseguita all'interno di una transazione definita dall'utente.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza di **db_owner** ruolo predefinito del database o **db_accessadmin** ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata l'istruzione `CREATE USER` per aggiungere un utente del database per l'account di accesso di Windows `Edmonds\LolanSo` al database corrente. Il nuovo utente è denominato `Lolan`. Si tratta del metodo ottimale per la creazione di un utente del database.  
  
```  
CREATE USER Lolan FOR LOGIN [Edmonds\LolanSo];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [DROP USER &#40; Transact-SQL &#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
