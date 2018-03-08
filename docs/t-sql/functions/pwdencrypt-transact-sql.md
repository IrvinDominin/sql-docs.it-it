---
title: PWDENCRYPT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 06b080d784d9a8737c1fe524e6634517ca0c97f5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce l'hash della password di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per il valore di input che utilizza la versione corrente dell'algoritmo di hashing delle password.  
  
 PWDENCRYPT è una funzione precedente e potrebbe non essere supportata in una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzare [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) invece. HASHBYTES rende disponibili ulteriori algoritmi di hashing.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>Argomenti  
 *password*  
 Password da crittografare. *password* è **sysname**.  
  
## <a name="return-types"></a>Tipi restituiti  
 **varbinary(128)**  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT è disponibile per il ruolo public.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di sicurezza &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40; Transact-SQL &#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  
