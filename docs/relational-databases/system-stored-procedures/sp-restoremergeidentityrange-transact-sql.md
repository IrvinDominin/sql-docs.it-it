---
title: sp_restoremergeidentityrange (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_restoremergeidentityrange_TSQL
- sp_restoremergeidentityrange
helpviewer_keywords:
- sp_restoremergeidentityrange
ms.assetid: 7923e422-2748-40c0-b5a8-6410c48d5b70
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3c5e07b7dde01cc8e8a0c1289a25c8fd3de83aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792129"
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
 [ **@publication** =] **'***pubblicazione***'**  
 Nome della pubblicazione. *pubblicazione* viene **sysname**, con valore predefinito **tutti**. Se viene specificato questo parametro, vengono ripristinati solo gli intervalli di valori Identity per la pubblicazione specificata.  
  
 [ **@article** =] **'***articolo***'**  
 Nome dell'articolo. *articolo* viene **sysname**, con valore predefinito è **tutti**. Se specificato, vengono ripristinati solo gli intervalli di valori Identity per l'articolo specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_restoremergeidentityrange** viene usato con la replica di tipo merge.  
  
 **sp_restoremergeidentityrange** Ottiene le informazioni sull'allocazione di intervallo massimo di identità dal server di distribuzione e aggiorna i valori nel **max_used** colonna [MSmerge_identity_range_allocations &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-identity-range-allocations-transact-sql.md) per gli articoli che utilizzano la gestione automatica.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_restoremergeidentityrange**.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [Replicare colonne Identity](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  
