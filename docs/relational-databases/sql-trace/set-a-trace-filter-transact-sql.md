---
title: "Impostare un filtro di traccia (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtri [SQL Server], tracce"
  - "tracce [SQL Server], filtri"
ms.assetid: 7b976a84-7381-43a6-a828-ba83ada71cbe
caps.latest.revision: 20
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 20
---
# Impostare un filtro di traccia (Transact-SQL)
  In questo argomento viene descritto come utilizzare stored procedure per creare un filtro che recupera solo le informazioni necessarie su un evento di cui è in corso la traccia.  
  
### Per impostare un filtro di traccia  
  
1.  Se la traccia è già in esecuzione, eseguire **sp_trace_setstatus** specificando **@status = 0** per arrestarla.  
  
2.  Eseguire **sp_trace_setfilter** per configurare il tipo di informazioni da recuperare per l'evento di cui è in corso la traccia.  
  
> [!IMPORTANT]  
>  A differenza di quanto avviene con le normali stored procedure, i parametri di tutte le stored procedure di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] (**sp_trace_*xx***) sono fortemente tipizzati e non supportano la conversione automatica del tipo di dati. Se questi parametri non vengono chiamati con i tipi di dati corretti per i parametri di input, come indicato nella descrizione dell'argomento, la stored procedure restituirà un errore.  
  
## Vedere anche  
 [Filtrare una traccia](../../relational-databases/sql-trace/filter-a-trace.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)  
  
  