---
title: Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo Merge (programmazione Transact-SQL della replica) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ac76aac61b5e0848e40ced7a0d6afda4a3a289a8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090891"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>Caricamento bulk dei dati nelle tabelle in una pubblicazione di tipo merge (programmazione Transact-SQL della replica)
  Quando i dati vengono caricati nelle tabelle utilizzando [bcp Utility](../../tools/bcp-utility.md) o il comando [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) , per impostazione predefinita, i trigger della replica di tipo merge che gestiscono i dati di rilevamento nella tabella di sistema [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) non vengono attivati. È possibile forzare l'attivazione dei trigger della replica di tipo merge al momento del caricamento dei dati o inserire i metadati di replica generati a livello di programmazione dopo l'operazione di copia bulk utilizzando le stored procedure di replica.  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>Per eseguire il caricamento bulk dei dati nelle tabelle pubblicate mediante la replica di tipo merge utilizzando l'utilità bcp  
  
1.  Nel server di pubblicazione o nel Sottoscrittore eseguire l' [bcp Utility](../../tools/bcp-utility.md) o [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) per inserire i dati in una tabella pubblicata mediante la replica di tipo merge.  
  
2.  Utilizzare uno dei metodi seguenti per assicurarsi che i metadati di replica vengano generati per i dati inseriti.  
  
    -   Eseguire la copia bulk utilizzando l'opzione FIRE_TRIGGERS.  
  
    -   Nel database in cui sono stati inseriti i dati eseguire [sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql). Specificare il nome della tabella nella quale sono stati inseriti i dati per **@table_name**.  
  
  
