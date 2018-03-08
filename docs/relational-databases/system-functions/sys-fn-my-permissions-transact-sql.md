---
title: sys.fn_my_permissions (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.fn_my_permissions_TSQL
- fn_my_permissions_TSQL
- sys.fn_my_permissions
- fn_my_permissions
dev_langs:
- TSQL
helpviewer_keywords:
- fn_my_permissions function
- sys.fn_my_permissions function
ms.assetid: 30f97f00-03d8-443a-9de9-9ec420b7699b
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Active
ms.openlocfilehash: 3c83af3c3c59b52a4a7c9fb2e127ab3bd03fb87d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="sysfnmypermissions-transact-sql"></a>sys.fn_my_permissions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce un elenco delle autorizzazioni valide concesse all'entità per un'entità a protezione diretta. Una funzione correlata è [HAS_PERMS_BY_NAME](../../t-sql/functions/has-perms-by-name-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
fn_my_permissions ( securable , 'securable_class' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *securable*  
 Nome dell'entità a protezione diretta. Se l'entità a sicurezza diretta è il server o un database, questo valore deve essere impostato su NULL. *entità a protezione diretta* è un'espressione scalare di tipo **sysname**. *entità a protezione diretta* può essere un nome in più parti.  
  
 '*securable_class*'  
 Nome della classe dell'entità a sicurezza diretta per cui vengono elencate le autorizzazioni. *securable_class* è un **sysname**. *securable_class* deve essere uno dei seguenti: APPLICATION ROLE, ASSEMBLY, chiave asimmetrica, certificato, contratto, DATABASE, ENDPOINT, FULLTEXT CATALOG, account di accesso, tipo di messaggio, oggetto, REMOTE SERVICE BINDING, ruolo, ROUTE, SCHEMA, SERVER, servizio , CHIAVE SIMMETRICA, TIPO, L'UTENTE, RACCOLTA DI XML SCHEMA.  
  
## <a name="columns-returned"></a>Colonne restituite  
 Nella tabella seguente vengono elencate le colonne che **fn_my_permissions** restituisce. Ogni riga restituita descrive un'autorizzazione assegnata al contesto di sicurezza corrente per l'entità a protezione diretta. Restituisce NULL se la query non viene eseguita correttamente.  
  
|Nome colonna|Tipo|Description|  
|-----------------|----------|-----------------|  
|nome_entità|**sysname**|Nome dell'entità a sicurezza diretta per la quale sono state concesse le autorizzazioni valide elencate.|  
|subentity_name|**sysname**|Nome della colonna nel caso in cui l'entità a sicurezza diretta contenga colonne. In caso contrario, NULL.|  
|permission_name|**nvarchar**|Nome dell'autorizzazione.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione con valori di tabella restituisce un elenco delle autorizzazioni valide assegnate all'entità di protezione chiamante per un'entità a sicurezza diretta specificata. Per autorizzazione valida si intende una qualsiasi delle autorizzazioni seguenti:  
  
-   Autorizzazione concessa direttamente all'entità di protezione e non negata.  
  
-   Un'autorizzazione inclusa in un'autorizzazione di livello superiore assegnata all'entità di protezione e non negata.  
  
-   Un'autorizzazione concessa a un ruolo o a un gruppo cui appartiene l'entità di protezione e non negata.  
  
-   Un'autorizzazione di cui dispone un ruolo o un gruppo a cui appartiene l'entità di protezione e non negata.  
  
 La valutazione dell'autorizzazione viene sempre eseguita nel contesto di sicurezza del chiamante. Per determinare se è stata assegnata un'autorizzazione valida a un'altra entità di protezione, il chiamante deve disporre dell'autorizzazione IMPERSONATE per tale entità.  
  
 Per le entità a livello di schema, sono accettati i nomi non Null composti da una, due o tre parti. Per le entità a livello di database, viene accettato un nome di una sola parte, con un valore null indica "*database corrente*". Per il server stesso, è richiesto un valore Null, ad indicare il server corrente. **fn_my_permissions** non controlla le autorizzazioni in un server collegato.  
  
 La query seguente restituirà un elenco di classi di entità a protezione diretta predefinite:  
  
```  
SELECT DISTINCT class_desc FROM fn_builtin_permissions(default)  
    ORDER BY class_desc;  
GO  
```  
  
 Se l'impostazione predefinita viene fornito come valore di *entità a protezione diretta* o *securable_class*, il valore verrà interpretato come NULL.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-listing-effective-permissions-on-the-server"></a>A. Elenco delle autorizzazioni valide per il server  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui il chiamante dispone per il server.  
  
```  
SELECT * FROM fn_my_permissions(NULL, 'SERVER');  
GO  
```  
  
### <a name="b-listing-effective-permissions-on-the-database"></a>B. Elenco delle autorizzazioni valide per il database  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui il chiamante dispone per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions (NULL, 'DATABASE');  
GO  
```  
  
### <a name="c-listing-effective-permissions-on-a-view"></a>C. Elenco delle autorizzazioni valide per una vista  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui il chiamante dispone per la vista `vIndividualCustomer` nello schema `Sales` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('Sales.vIndividualCustomer', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;   
GO   
```  
  
### <a name="d-listing-effective-permissions-of-another-user"></a>D. Elenco delle autorizzazioni valide di un altro utente  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui l'utente del database `Wanida` dispone per la tabella `Employee` nello schema `HumanResources` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Il chiamante deve disporre dell'autorizzazione IMPERSONATE per l'utente `Wanida`.  
  
```  
EXECUTE AS USER = 'Wanida';  
SELECT * FROM fn_my_permissions('HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
### <a name="e-listing-effective-permissions-on-a-certificate"></a>E. Elenco delle autorizzazioni valide per un certificato  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui il chiamante dispone per un certificato denominato `Shipping47` nel database corrente.  
  
```  
SELECT * FROM fn_my_permissions('Shipping47', 'CERTIFICATE');  
GO  
```  
  
### <a name="f-listing-effective-permissions-on-an-xml-schema-collection"></a>F. Elenco delle autorizzazioni valide per una raccolta di XML Schema  
 L'esempio seguente restituisce un elenco delle autorizzazioni valide del chiamante in una raccolta di XML Schema denominato `ProductDescriptionSchemaCollection` nel [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.  
  
```  
USE AdventureWorks2012;  
SELECT * FROM fn_my_permissions('ProductDescriptionSchemaCollection',  
    'XML SCHEMA COLLECTION');  
GO  
```  
  
### <a name="g-listing-effective-permissions-on-a-database-user"></a>G. Elenco delle autorizzazioni valide per un utente del database  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui il chiamante dispone per un utente denominato `MalikAr` nel database corrente.  
  
```  
SELECT * FROM fn_my_permissions('MalikAr', 'USER');  
GO  
```  
  
### <a name="h-listing-effective-permissions-of-another-login"></a>H. Elenco delle autorizzazioni valide di un altro account di accesso  
 Nell'esempio seguente viene restituito un elenco delle autorizzazioni valide di cui l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `WanidaBenshoof` dispone per la tabella `Employee` nello schema `HumanResources` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Il chiamante deve disporre dell'autorizzazione IMPERSONATE per l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `WanidaBenshoof`.  
  
```  
EXECUTE AS LOGIN = 'WanidaBenshoof';  
SELECT * FROM fn_my_permissions('AdventureWorks2012.HumanResources.Employee', 'OBJECT')   
    ORDER BY subentity_name, permission_name ;    
REVERT;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [Gerarchia delle autorizzazioni &#40;Motore di database&#41;](../../relational-databases/security/permissions-hierarchy-database-engine.md)   
 [sys.fn_builtin_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [Viste del catalogo relative alla sicurezza &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [EXECUTE AS &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  
