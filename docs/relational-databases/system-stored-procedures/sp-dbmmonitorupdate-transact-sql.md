---
title: sp_dbmmonitorupdate (Transact-SQL) | Microsoft Docs
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
- sp_dbmmonitorupdate
- sp_dbmmonitorupdate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorupdate
- database mirroring [SQL Server], monitoring
ms.assetid: 9ceb9611-4929-44ee-a406-c39ba2720fd5
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e2970c0c6f75755e295fae32a1a5ceab046bb75d
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spdbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aggiorna la tabella di stato di Monitoraggio mirroring del database inserendo una nuova riga di tabella per ogni database con mirroring e tronca le righe precedenti al periodo di memorizzazione corrente. Il periodo di memorizzazione predefinito è 7 giorni (168 ore). Quando si aggiorna la tabella, **sp_dbmmonitorupdate** restituisce le metriche delle prestazioni.  
  
> [!NOTE]  
>  La prima volta **sp_dbmmonitorupdate** viene eseguita, crea la tabella dello stato di mirroring del database e **dbm_monitor** ruolo predefinito del database nel **msdb** database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>Argomenti  
 *database_name*  
 Nome del database per cui aggiornare lo stato di mirroring. Se *database_name* non viene specificato, la procedura Aggiorna la tabella dello stato per ogni database con mirroring nell'istanza del server.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_dbmmonitorupdate** può essere eseguito solo nel contesto del **msdb** database.  
  
 Se una colonna della tabella di stato non è valida per il ruolo di un partner, il valore è NULL per tale partner. Una colonna include inoltre valori NULL se le informazioni rilevanti non sono disponibili, ad esempio durante il failover o il riavvio del server.  
  
 Dopo aver **sp_dbmmonitorupdate** crea il **dbm_monitor** ruolo predefinito del database nel **msdb** database, i membri del **sysadmin** ruolo predefinito del server può aggiungere qualsiasi utente per il **dbm_monitor** ruolo predefinito del database. Il **dbm_monitor** ruolo consente ai membri di visualizzare lo stato di mirroring del database, ma non l'aggiornamento, ma non visualizzare o configurare gli eventi di mirroring del database.  
  
 Quando si aggiorna lo stato di mirroring di un database, **sp_dbmmonitorupdate** verifica l'ultimo valore le metriche delle prestazioni del mirroring per il quale è stata specificata una soglia di avviso. Se il valore supera la soglia, la procedura aggiunge un evento informativo al log eventi. Tutti valori sono medie eseguite dopo l'ultimo aggiornamento. Per altre informazioni, vedere [Usare valori di soglia avvisi e avvisi sulle metriche delle prestazioni di mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiornato lo stato di mirroring solo per il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
