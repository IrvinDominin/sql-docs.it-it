---
title: Eseguire la pulizia dei metadati di merge (programmazione Transact-SQL della replica) | Microsoft Docs
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
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b559c7ea2f1cd882a9a737935416dbd5e1869187
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48179481"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>Pulizia dei metadati di merge (programmazione Transact-SQL della replica)
  La rimozione dei metadati della replica di tipo merge viene eseguita periodicamente dall'agente di merge in base all'impostazione di memorizzazione per la pubblicazione. Nel server di pubblicazione e nel Sottoscrittore ciò avviene nelle tabelle di sistema [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql), [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql), [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)e [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) . È inoltre possibile rimuovere i dati in tali tabelle a livello di programmazione utilizzando le stored procedure di replica.  
  
### <a name="to-manually-clean-up-merge-metadata"></a>Per pulire manualmente i metadati di merge  
  
1.  Nel database di pubblicazione del server di pubblicazione eseguire [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql).  
  
2.  (Facoltativo) Tenere presente il numero di righe rimosse nel passaggio 1 dalle tabelle di sistema [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql), [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)e [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql) . Tali valori sono restituiti rispettivamente nei parametri di output **@num_genhistory_rows**, **@num_contents_rows**e **@num_tombstone_rows** .  
  
3.  Ripetere i passaggi 1 e 2 nel Sottoscrittore per eseguire la pulizia dei metadati nel database di sottoscrizione.  
  
## <a name="see-also"></a>Vedere anche  
 [Scadenza e disattivazione delle sottoscrizioni](../subscription-expiration-and-deactivation.md)  
  
  
