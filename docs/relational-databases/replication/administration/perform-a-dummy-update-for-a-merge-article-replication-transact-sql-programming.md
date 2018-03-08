---
title: Eseguire un aggiornamento fittizio per un articolo di merge (programmazione Transact-SQL della replica) | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- sp_mergedummyupdate
- dummy updates [SQL Server replication]
ms.assetid: 2f339210-4d85-4843-bd94-e86f7100d3ef
caps.latest.revision: "31"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c52d1445609cc3b99e473433349828d1ebe0fad
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming"></a>Esecuzione di un aggiornamento fittizio per un articolo di merge (programmazione Transact-SQL della replica)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La replica di tipo merge usa i trigger come parte del processo di replica; in caso di aggiornamento di una tabella pubblicata, viene attivato un trigger di aggiornamento. In alcuni casi, i dati possono essere aggiornati senza l'attivazione del trigger, ad esempio durante le operazioni WRITETEXT e UPDATETEXT. In questi casi, è necessario aggiungere in modo esplicito un'istruzione UPDATE fittizia per replicare la modifica. È possibile aggiungere un'istruzione UPDATE fittizia utilizzando le stored procedure di replica.  
  
### <a name="to-add-a-dummy-update-statement"></a>Per aggiungere un'istruzione UPDATE fittizia  
  
1.  Eseguire l'operazione, ad esempio UPDATETEXT, su una riga in una tabella pubblicata di merge che richiede un aggiornamento fittizio.  
  
2.  Nel database del server di pubblicazione o del Sottoscrittore nel quale è stata apportata la modifica, eseguire [sp_mergedummyupdate &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergedummyupdate-transact-sql.md). Specificare la tabella nella quale è stata apportata la modifica per **@source_object**e l'identificatore univoco della riga modificata per **@rowguid**.  
  
3.  Sincronizzare la sottoscrizione per replicare la riga modificata.  
  
  
