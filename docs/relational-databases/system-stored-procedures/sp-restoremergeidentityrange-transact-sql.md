---
title: sp_restoremergeidentityrange (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a42807009ffd42b16fe08fde76b7f91e34d62742
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sprestoremergeidentityrange-transact-sql"></a>sp_restoremergeidentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Questa stored procedure viene utilizzata per aggiornare le assegnazioni degli intervalli di valori Identity. Garantisce inoltre che la gestione automatica degli intervalli di valori Identity funzioni correttamente dopo il ripristino di un server di pubblicazione da un backup. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_restoremergeidentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publication**  =] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* è **sysname**, con valore predefinito di **tutti**. Se viene specificato questo parametro, vengono ripristinati solo gli intervalli di valori Identity per la pubblicazione specificata.  
  
 [  **@article**  =] **'***articolo***'**  
 Nome dell'articolo. *articolo* è **sysname**, con un valore predefinito di **tutti**. Se specificato, vengono ripristinati solo gli intervalli di valori Identity per l'articolo specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_restoremergeidentityrange** viene utilizzato con la replica di tipo merge.  
  
 **sp_restoremergeidentityrange** Ottiene informazioni di allocazione di intervalli di valori identity massimo dal server di distribuzione e aggiorna i valori di **max_used** colonna di [MSmerge_identity_range_allocations & # 40; Transact-SQL &#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) per gli articoli che utilizzano Gestione intervalli di valori identity automatici.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server o **db_owner** ruolo predefinito del database possono eseguire **sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergearticle &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Replicare colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
