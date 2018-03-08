---
title: sp_migrate_user_to_contained (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_migrate_user_to_contained
- sp_migrate_user_to_contained_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_migrate_user_to_contained
ms.assetid: b3a49ff6-46ad-4ee7-b6fe-7e54213dc33e
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 366d2347118fa55a8541e7f84a268b173ae5b2e3
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="spmigrateusertocontained-transact-sql"></a>sp_migrate_user_to_contained (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Converte un utente del database di cui è stato eseguito il mapping a un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in un utente del database indipendente con password. In un database indipendente, utilizzare questa procedura per rimuovere le dipendenze nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui viene installato il database. **sp_migrate_user_to_contained** separa l'utente dall'originale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] account di accesso, in modo che sia possibile amministrare separatamente impostazioni quali password e lingua predefinita per il database indipendente. **sp_migrate_user_to_contained** può essere usata prima di spostare il database indipendente in un'istanza diversa del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] per eliminare le dipendenze corrente [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gli account di accesso dell'istanza.  
  
 **Nota** questa procedura viene utilizzata solo in un database indipendente. Per altre informazioni, vedere [Database indipendenti](../../relational-databases/databases/contained-databases.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_migrate_user_to_contained [ @username = ] N'user' ,   
    [ @rename = ] { N'copy_login_name' | N'keep_name' } ,   
    [ @disablelogin = ] { N'disable_login' | N'do_not_disable_login' }   
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@username =** ] **N'***utente***'**  
 Nome di un utente nel database indipendente corrente di cui è stato eseguito il mapping a un account di accesso con autenticazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il valore è **sysname**, il valore predefinito è **NULL**.  
  
 [ **@rename =** ] **N'***copy_login_name***'** | **N'** *keep_name***'**  
 Quando un utente del database in base a un account di accesso è un nome utente diverso rispetto al nome di account di accesso, utilizzare *keep_name* per mantenere il nome utente del database durante la migrazione. Utilizzare *copy_login_name* per creare il nuovo utente del database indipendente con il nome dell'account di accesso, invece che all'utente. Quando il nome utente di un utente del database basato su un account di accesso è uguale al nome dell'account di accesso, entrambe le opzioni consentono di creare l'utente del database indipendente senza la modifica del nome.  
  
 [ **@disablelogin =** ] **N'***disable_login***'** | **N'** *do_not_disable_login***'**  
 *disable_login* disabilita l'account di accesso nel database master. Per connettersi quando l'account di accesso è disabilitato, la connessione deve fornire il nome del database indipendente come il **catalogo iniziale** come parte della stringa di connessione.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_migrate_user_to_contained** Crea utente del database indipendente con password, indipendentemente dalla proprietà o le autorizzazioni dell'account di accesso. Ad esempio, la procedura può avere esito positivo se l'account di accesso è disabilitato o se all'utente viene negato il **CONNETTI** autorizzazioni per il database.  
  
 **sp_migrate_user_to_contained** presenta le restrizioni seguenti.  
  
-   Il nome utente non può essere già esistente nel database.  
  
-   Impossibile convertire gli utenti predefiniti, ad esempio dbo e guest.  
  
-   L'utente non può essere specificato nella **EXECUTE AS** clausola di una stored procedure firmata.  
  
-   L'utente non può disporre di una stored procedure che include il **EXECUTE AS OWNER** clausola.  
  
-   **sp_migrate_user_to_contained** non può essere utilizzato in un database di sistema.  
  
## <a name="security"></a>Security  
 Quando si esegue la migrazione di utenti, fare attenzione a non disabilitare o eliminare tutti gli account di accesso di amministratore dall'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se vengono eliminati tutti gli account di accesso, vedere [connettersi a SQL Server quando System Administrators sono bloccati](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md).  
  
 Se il **BUILTIN\Administrators** account di accesso è presente, gli amministratori possono connettersi avviando l'applicazione mediante il **Esegui come amministratore** opzione.  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione **CONTROL SERVER** .  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-migrating-a-single-user"></a>A. Migrazione di un solo utente  
 Nell'esempio seguente viene eseguita la migrazione di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] denominato `Barry` a un database indipendente con password. Nell'esempio il nome utente non viene modificato e l'account di accesso rimane abilitato.  
  
```sql  
sp_migrate_user_to_contained   
@username = N'Barry',  
@rename = N'keep_name',  
@disablelogin = N'do_not_disable_login' ;  
  
```  
  
### <a name="b-migrating-all-database-users-with-logins-to-contained-database-users-without-logins"></a>B. Migrazione di tutti gli utenti del database con account di accesso a utenti del database indipendente senza account di accesso  
 Nell'esempio seguente viene eseguita la migrazione di tutti gli utenti basati sugli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a utenti del database indipendente con password. Nell'esempio sono inclusi account di accesso non abilitati. L'esempio deve essere eseguito nel database indipendente.  
  
```sql  
DECLARE @username sysname ;  
DECLARE user_cursor CURSOR  
    FOR   
        SELECT dp.name   
        FROM sys.database_principals AS dp  
        JOIN sys.server_principals AS sp   
        ON dp.sid = sp.sid  
        WHERE dp.authentication_type = 1 AND sp.is_disabled = 0;  
OPEN user_cursor  
FETCH NEXT FROM user_cursor INTO @username  
    WHILE @@FETCH_STATUS = 0  
    BEGIN  
        EXECUTE sp_migrate_user_to_contained   
        @username = @username,  
        @rename = N'keep_name',  
        @disablelogin = N'disable_login';  
    FETCH NEXT FROM user_cursor INTO @username  
    END  
CLOSE user_cursor ;  
DEALLOCATE user_cursor ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Migrate to a Partially Contained Database](../../relational-databases/databases/migrate-to-a-partially-contained-database.md)   
 [Database indipendenti](../../relational-databases/databases/contained-databases.md)  
  
  
