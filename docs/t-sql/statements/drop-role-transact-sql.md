---
title: DROP ROLE (Transact-SQL) | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 05/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP ROLE
- DROP_ROLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting roles
- database roles [SQL Server], removing
- removing roles
- DROP ROLE statement
- roles [SQL Server], removing
- dropping roles
ms.assetid: 1f6f13ae-56a2-4ef1-93f5-8e6151b83e1d
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d8262eae6ed14104da08cf182326f49c3221876a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="drop-role-transact-sql"></a>DROP ROLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Rimuove un ruolo dal database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server  
  
DROP ROLE [ IF EXISTS ] role_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP ROLE role_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale il ruolo solo se esiste già.  
  
 *role_name*  
 Specifica il ruolo da rimuovere dal database.  
  
## <a name="remarks"></a>Osservazioni  
 I ruoli proprietari di entità a sicurezza diretta non possono essere rimossi dal database. Per rimuovere un ruolo di database proprietario di entità a sicurezza diretta, è innanzitutto necessario trasferire la proprietà di tali entità oppure rimuovere le entità dal database. I ruoli che includono membri non possono essere rimossi dal database. Per rimuovere un ruolo che include membri, è innanzitutto necessario rimuovere i membri del ruolo.  
  
 Per rimuovere membri da un ruolo del database, utilizzare [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md).  
  
 Non è possibile utilizzare l'istruzione DROP ROLE per rimuovere un ruolo predefinito del database.  
  
 Le informazioni sull'appartenenza ai ruoli sono visibili nella vista del catalogo sys.database_role_members.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
 Per rimuovere un ruolo del server, utilizzare [DROP SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/drop-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Richiede **ALTER ANY ROLE** autorizzazione per il database, o **controllo** l'autorizzazione per il ruolo o l'appartenenza di **db_securityadmin**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eliminato il ruolo del database `purchasing` dal `AdventureWorks2012` database.  
  
```  
DROP ROLE purchasing;  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [CREAZIONE di ruolo &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sys.database_role_members &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-role-members-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  


