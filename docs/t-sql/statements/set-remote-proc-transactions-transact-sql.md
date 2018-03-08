---
title: SET REMOTE_PROC_TRANSACTIONS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- REMOTE_PROC_TRANSACTIONS_TSQL
- SET REMOTE_PROC_TRANSACTIONS
- REMOTE_PROC_TRANSACTIONS
- SET_REMOTE_PROC_TRANSACTIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- remote stored procedures [SQL Server]
- SET REMOTE_PROC_TRANSACTIONS statement
- distributed transactions [SQL Server], starting
- REMOTE_PROC_TRANSACTIONS option
- active transactions
ms.assetid: 4d284ae9-3f5f-465a-b0dd-1328a4832a03
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97d4599c98e68a3cf4bd8682ec2b4601aec19568
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="set-remoteproctransactions-transact-sql"></a>SET REMOTE_PROC_TRANSACTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Specifica che, quando una transazione locale è attiva, l'esecuzione di una stored procedure remota comporta l'avvio di una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)] gestita da [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Questa opzione è disponibile per la compatibilità con le versioni precedenti per le applicazioni che utilizzano stored procedure remote. Anziché pubblicare chiamate della stored procedure remota, utilizzare query distribuite che fanno riferimento a server collegati che Questi vengono definiti utilizzando [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SET REMOTE_PROC_TRANSACTIONS { ON | OFF }   
```  
  
## <a name="arguments"></a>Argomenti  
 ON | OFF  
 Quando è impostata su ON, viene avviata una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)] quando in una transazione locale viene eseguita una stored procedure remota. Quando è impostata su OFF, la chiamata di una stored procedure remota in una transazione locale non avvia una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="remarks"></a>Osservazioni  
 Quando l'opzione REMOTE_PROC_TRANSACTIONS è impostata su ON, la chiamata di una stored procedure remota comporta l'avvio di una transazione distribuita e l'integrazione della transazione in MS DTC. L'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in cui viene chiamata la stored procedure remota corrisponde all'origine della transazione e ne controlla il completamento. Quando per la connessione viene successivamente eseguita un'istruzione COMMIT TRANSACTION o ROLLBACK TRANSACTION, l'istanza di controllo richiede che il completamento della transazione distribuita nei computer interessati venga gestito da MS DTC.  
  
 Dopo l'avvio di una transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)], è possibile chiamare stored procedure remote in altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che sono state definite come server remoti. Tutti i server remoti sono integrati nella transazione distribuita [!INCLUDE[tsql](../../includes/tsql-md.md)]. MS DTC assicura inoltre che la transazione venga completata in ogni server remoto.  
  
 L'opzione REMOTE_PROC_TRANSACTIONS è un'impostazione a livello di connessione che può essere utilizzata per eseguire l'override a livello di istanza **sp_configure remote proc trans** opzione.  
  
 Quando l'opzione REMOTE_PROC_TRANSACTIONS viene impostata su OFF, le chiamate di stored procedure remote non diventano parte di una transazione locale. Al completamento della stored procedure remota viene eseguito il commit o il rollback delle modifiche apportate dalla stored procedure. Le successive istruzioni COMMIT TRANSACTION o ROLLBACK TRANSACTION eseguite dalla connessione che ha chiamato la stored procedure remota non hanno alcun effetto sull'elaborazione eseguita dalla procedura.  
  
 L'opzione REMOTE_PROC_TRANSACTIONS è un'opzione di compatibilità che influisce sulle chiamate di stored procedure remota solo a istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definito come server remoti tramite **sp_addserver**. L'opzione non si applica alle query distribuite che eseguono una stored procedure in un'istanza definita come server collegato utilizzando **sp_addlinkedserver**.  
  
 L'opzione SET REMOTE_PROC_TRANSACTIONS viene impostata in fase di esecuzione, non in fase di analisi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="see-also"></a>Vedere anche  
 [BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
