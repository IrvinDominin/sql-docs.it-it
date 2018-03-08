---
title: MODIFICARE il ruolo di SERVER (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-non-specified
ms.prod_service: pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_SERVER_ROLE_TSQL
- ALTER SERVER ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- SERVER ROLE, ALTER
- ALTER SERVER ROLE statement
ms.assetid: 7a4db7bb-c442-4e12-9a8a-114da5bc7710
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 7ce5b5223f5c755c89cb3e105ceb6517087d699f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="alter-server-role-transact-sql"></a>ALTER SERVER ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-pdw-md.md)]

Modifica l'appartenenza di un ruolo del server o il nome di un ruolo del server definito dall'utente. Impossibile rinominare i ruoli predefiniti del server.  
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
ALTER SERVER ROLE server_role_name   
{  
    [ ADD MEMBER server_principal ]  
  | [ DROP MEMBER server_principal ]  
  | [ WITH NAME = new_server_role_name ]  
} [ ; ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
ALTER SERVER ROLE  server_role_name  ADD MEMBER login;  
  
ALTER SERVER ROLE  server_role_name  DROP MEMBER login;  
```  
  
## <a name="arguments"></a>Argomenti  
*nome_ruolo_server*  
Nome del ruolo del server da modificare.  
  
Aggiungi membro *server_principal*  
Aggiunge l'entità server specificata al ruolo del server. *server_principal* può essere un account di accesso o un ruolo del server definito dall'utente. *server_principal* non può essere un ruolo predefinito del server, un ruolo del database o dell'amministratore di sistema.  
  
DROP MEMBER *server_principal*  
Rimuove l'entità server specificata dal ruolo del server. *server_principal* può essere un account di accesso o un ruolo del server definito dall'utente. *server_principal* non può essere un ruolo predefinito del server, un ruolo del database o dell'amministratore di sistema.  
  
CON nome  **=**  *new_server_role_name*  
Specifica il nuovo nome del ruolo del server definito dall'utente. Il nome non deve essere già esistente nel server.  
  
## <a name="remarks"></a>Osservazioni  
La modifica del nome di un ruolo del server definito dall'utente non comporta la modifica del numero di ID, del proprietario o delle autorizzazioni del ruolo.  
  
Per modificare l'appartenenza al ruolo, `ALTER SERVER ROLE` sostituisce sp_addsrvrolemember e sp_dropsrvrolemember. Queste stored procedure sono deprecate.  
  
È possibile visualizzare i ruoli del server eseguendo una query sulle viste del catalogo `sys.server_role_members` e `sys.server_principals`.  
  
Per modificare il proprietario di un ruolo del server definito dall'utente, utilizzare [ALTER AUTHORIZATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
Richiede `ALTER ANY SERVER ROLE` autorizzazione per il server per modificare il nome di un ruolo del server definito dall'utente.  
  
**Ruoli predefiniti del server**  
  
Per aggiungere un membro a un ruolo predefinito del server, è necessario essere membri di tale ruolo o del ruolo predefinito del server `sysadmin`.  
  
> [!NOTE]  
>  Il `CONTROL SERVER` e `ALTER ANY SERVER ROLE` autorizzazioni non sono sufficienti per eseguire `ALTER SERVER ROLE` per un ruolo predefinito del server, e `ALTER` Impossibile concedere l'autorizzazione in un ruolo predefinito del server.  
  
**Ruoli server definiti dall'utente**  
  
Per aggiungere un membro a un ruolo del server definito dall'utente, è necessario essere un membro del `sysadmin` ruolo predefinito del server o avere `CONTROL SERVER` o `ALTER ANY SERVER ROLE` autorizzazione. Oppure è necessario disporre `ALTER` l'autorizzazione per tale ruolo.  
  
> [!NOTE]  
>  A differenza dei ruoli predefiniti del server, i membri di un ruolo del server definito dall'utente non dispongono implicitamente dell'autorizzazione per aggiungere membri a quello stesso ruolo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-changing-the-name-of-a-server-role"></a>A. Modifica del nome di un ruolo del server  
Nell'esempio seguente viene creato un ruolo del server denominato `Product`, viene quindi modificato il nome del ruolo del server in `Production`.  
  
```  
CREATE SERVER ROLE Product ;  
ALTER SERVER ROLE Product WITH NAME = Production ;  
GO  
```  
  
### <a name="b-adding-a-domain-account-to-a-server-role"></a>B. Aggiunta di un account di dominio a un ruolo del server  
Nell'esempio seguente viene aggiunto un account di dominio denominato `adventure-works\roberto0` al ruolo del server definito dall'utente denominato `Production`.  
  
```  
ALTER SERVER ROLE Production ADD MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="c-adding-a-sql-server-login-to-a-server-role"></a>C. Aggiunta di un account di accesso di SQL Server a un ruolo del server  
L'esempio seguente aggiunge un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso denominato `Ted` per il `diskadmin` ruolo predefinito del server.  
  
```  
ALTER SERVER ROLE diskadmin ADD MEMBER Ted ;  
GO  
```  
  
### <a name="d-removing-a-domain-account-from-a-server-role"></a>D. Rimozione di un account di dominio da un ruolo del server  
Nell'esempio seguente viene rimosso un account di dominio denominato `adventure-works\roberto0` dal ruolo del server definito dall'utente denominato `Production`.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER [adventure-works\roberto0] ;  
```  
  
### <a name="e-removing-a-sql-server-login-from-a-server-role"></a>E. Rimozione di un account di accesso di SQL Server da un ruolo del server  
L'esempio seguente rimuove il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] accesso `Ted` dal `diskadmin` ruolo predefinito del server.  
  
```  
ALTER SERVER ROLE Production DROP MEMBER Ted ;  
GO  
```  
  
### <a name="f-granting-a-login-the-permission-to-add-logins-to-a-user-defined-server-role"></a>F. Concessione di un account di accesso all'autorizzazione per aggiungere account di accesso a un ruolo del server definito dall'utente  
Nell'esempio seguente viene consentito a `Ted` di aggiungere altri account di accesso al ruolo del server definito dall'utente denominato `Production`.  
  
```  
GRANT ALTER ON SERVER ROLE::Production TO Ted ;  
GO  
```  
  
### <a name="g-to-view-role-membership"></a>G. Per visualizzare l'appartenenza ai ruoli  
Per visualizzare l'appartenenza al ruolo, utilizzare il **ruolo del Server (membri)** pagina [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o eseguire la query seguente:  
  
```  
SELECT SRM.role_principal_id, SP.name AS Role_Name,   
SRM.member_principal_id, SP2.name  AS Member_Name  
FROM sys.server_role_members AS SRM  
JOIN sys.server_principals AS SP  
    ON SRM.Role_principal_id = SP.principal_id  
JOIN sys.server_principals AS SP2   
    ON SRM.member_principal_id = SP2.principal_id  
ORDER BY  SP.name,  SP2.name  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Esempi:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="h-basic-syntax"></a>H. Sintassi di base  
L'esempio seguente aggiunge l'account di accesso `Anna` per il `LargeRC` ruolo del server.  
  
```  
ALTER SERVER ROLE LargeRC ADD MEMBER Anna;  
```  
  
### <a name="i-remove-a-login-from-a-resource-class"></a>I. Rimuovere un account di accesso da una classe di risorse.  
Nell'esempio seguente elimina l'appartenenza di Anna il `LargeRC` ruolo del server.  
  
```  
ALTER SERVER ROLE LargeRC DROP MEMBER Anna;  
```  
  
## <a name="see-also"></a>Vedere anche  
[CREATE SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
[DROP SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
[CREAZIONE di ruolo &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
[ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
[DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
[Sicurezza Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
[Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
[Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
[Sys. server_role_members &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-server-role-members-transact-sql.md)   
[sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
