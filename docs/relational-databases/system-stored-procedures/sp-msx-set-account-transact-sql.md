---
title: sp_msx_set_account (Transact-SQL) | Microsoft Docs
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
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7d463863e71a0ba2899a987fdb425d08c8f5245a
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta il nome account e la password del server master di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nel server di destinazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@credential_name=** ] **'***credential_name***'**  
 Nome delle credenziali da utilizzare per accedere al server master. Il nome specificato deve corrispondere al nome di una credenziale esistente. Entrambi *credential_name* o *credential_id* deve essere specificato.  
  
 [ **@credential_id=** ] *credential_id*  
 Identificatore delle credenziali da utilizzare per accedere al server master. L'identificatore deve corrispondere a un identificatore di credenziali già esistenti. Entrambi *credential_name* o *credential_id* deve essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] credenziali utilizzate per archiviare le informazioni di nome e una password utente che utilizza un server di destinazione per l'accesso a un server master. Questa procedura imposta le credenziali utilizzate da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per questo server di destinazione per accedere al server master.  
  
 Le credenziali specificate devono corrispondere a delle credenziali esistenti. Per ulteriori informazioni sulla creazione di una credenziale, vedere [CREATE CREDENTIAL &#40; Transact-SQL &#41; ](../../t-sql/statements/create-credential-transact-sql.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione **sp_msx_set_account** per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene impostato il server per utilizzare le credenziali `MsxAccount` per accedere al server master.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
