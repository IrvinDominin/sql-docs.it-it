---
title: CLOSE SYMMETRIC KEY (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b2e65502932c646f539e923fe905854234534eac
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Chiude una chiave simmetrica oppure tutte le chiavi simmetriche aperte nella sessione corrente.  
  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>Argomenti  
 *Key_name*  
 Nome della chiave simmetrica da chiudere.  
  
## <a name="remarks"></a>Osservazioni  
 Le chiavi simmetriche aperte sono associate alla sessione, non al contesto di sicurezza. Una chiave aperta resterà disponibile finché non viene chiusa in modo esplicito o la sessione non viene terminata. CLOSE ALL SYMMETRIC KEYS chiuderà qualsiasi chiave master del database che è stato aperto nella sessione corrente tramite il [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) istruzione.  Informazioni sulle chiavi aperte sono visibili nella [sys.openkeys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) vista del catalogo.  
  
## <a name="permissions"></a>Permissions  
 Non sono richieste autorizzazioni esplicite per chiudere una chiave simmetrica.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-closing-a-symmetric-key"></a>A. Chiusura di una chiave simmetrica  
 Nell'esempio seguente viene chiusa la chiave simmetrica `ShippingSymKey04`.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>B. Chiusura di tutte le chiavi simmetriche  
 Nell'esempio seguente vengono chiuse tutte le chiavi simmetriche aperte nella sessione corrente insieme alla chiave master del database aperta in modo esplicito.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  
