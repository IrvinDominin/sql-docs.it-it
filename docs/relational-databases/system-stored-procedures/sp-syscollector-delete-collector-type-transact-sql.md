---
title: sp_syscollector_delete_collector_type (Transact-SQL) | Microsoft Docs
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
- sp_syscollector_delete_collector_type
- sp_syscollector_delete_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collector_type
ms.assetid: 3f32905e-0005-42cb-aef1-7bd04c51fbac
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 14bfab3376da20b677414106e293ad21103e52dc
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spsyscollectordeletecollectortype-transact-sql"></a>sp_syscollector_delete_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina la definizione di un tipo di agente di raccolta.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_syscollector_delete_collector_type [[ @collector_type_uid = ] 'collector_type_uid' ]  
          , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@collector_type_uid =** ] **'***collector_type_uid***'**  
 GUID del tipo di agente di raccolta. *collector_type_uid* è **uniqueidentifier** e deve avere un valore se *nome* è NULL.  
  
 [  **@name =** ] **'***nome***'**  
 Nome del tipo di agente di raccolta. *nome* è **sysname** e deve avere un valore se *collector_type_uid* è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Entrambi *collector_type_uid* o *nome* deve avere un valore, non possono essere entrambi NULL.  
  
 Questa procedura genererà un errore se esistono gli elementi della raccolta di questo tipo di raccolta.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **dc_admin** (con autorizzazione EXECUTE) ruolo predefinito del database per eseguire questa procedura.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene eliminato il tipo di agente di raccolta query T-SQL generico.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collector_type @collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
