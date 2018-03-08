---
title: sys.trusted_assemblies (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan;rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 827e0d356114bf2254ebd265ca7ee29e0a00f595
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Contiene una riga per ogni assembly attendibile per il server.

 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Nome colonna |Tipo di dati |Description |
|--- |--- |--- |
|hash |varbinary(8000) |SHA2_512 l'hash del contenuto dell'assembly. |
|description |nvarchar(4000) |Descrizione definita dall'utente facoltativa dell'assembly. Si consiglia di utilizzare il nome canonico che consente di codificare il nome semplice, numero di versione, impostazioni cultura, chiave pubblica e l'architettura dell'assembly da considerare attendibile. Questo valore in modo univoco identifica l'assembly relativamente alla common language runtime (CLR) e corrisponde al valore clr_name nella Assemblies. |
|create_date |datetime2 |Data che l'assembly è stato aggiunto all'elenco degli assembly attendibili. |
|created_by |nvarchar (128) |Nome di account di accesso dell'entità che ha aggiunto l'assembly all'elenco. |
| | | |


## <a name="remarks"></a>Osservazioni  

Utilizzare **necessario aggiungere sp_add_trusted_assembly** e **necessario aggiungere sys.trusted_assemblies** aggiungere o rimuovere gli assembly da `sys.trusted_assemblies`.

## <a name="see-also"></a>Vedere anche  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  

