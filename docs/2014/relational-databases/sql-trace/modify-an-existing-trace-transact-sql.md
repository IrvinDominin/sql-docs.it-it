---
title: Modificare una traccia esistente (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- traces [SQL Server], modifying
- modifying traces
ms.assetid: 8792b43f-2510-44e3-9239-e73ad8227b89
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4d5308b708e32a1e886aadc2c78d3f504c3a6640
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163571"
---
# <a name="modify-an-existing-trace-transact-sql"></a>Modificare una traccia esistente (Transact-SQL)
  In questo argomento viene descritto come utilizzare stored procedure per modificare una traccia esistente.  
  
### <a name="to-modify-an-existing-trace"></a>Per modificare una traccia esistente  
  
1.  Se la traccia è già in esecuzione, eseguire **sp_trace_setstatus** specificando **@status = 0** per arrestarla.  
  
2.  Per modificare eventi di traccia, eseguire **sp_trace_setevent** usando i parametri per specificare le modifiche. Nell'ordine i parametri sono i seguenti:  
  
    -   **@traceid** (ID traccia)  
  
    -   **@eventid** (ID evento)  
  
    -   **@columnid** (ID colonna)  
  
    -   **@on** (ON)  
  
     Quando si modifica il parametro **@on** , tenere presente l'interazione con il parametro **@columnid** :  
  
    |ON|ID colonna|Risultato|  
    |--------|---------------|------------|  
    |ON (**1**)|NULL|L'evento viene abilitato. Tutte le colonne vengono cancellate.|  
    ||NOT NULL|La colonna viene abilitata per l'evento specificato.|  
    |OFF (**0**)|NULL|L'evento viene disabilitato. Tutte le colonne vengono cancellate.|  
    ||NOT NULL|La colonna viene disabilitata per l'evento specificato.|  
  
> [!IMPORTANT]  
>  A differenza di quanto avviene con le normali stored procedure, i parametri di tutte le stored procedure di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_* xx***) sono fortemente tipizzati e non supportano la conversione automatica del tipo di dati. Se tali parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituisce un errore.  
  
## <a name="see-also"></a>Vedere anche  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql)  
  
  
