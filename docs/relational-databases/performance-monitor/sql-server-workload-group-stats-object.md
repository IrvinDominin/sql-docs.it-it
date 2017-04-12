---
title: "SQL Server - Oggetto Statistiche gruppi del carico di lavoro | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "12/04/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "oggetto Statistiche gruppi del carico di lavoro"
  - "SQLServer: Statistiche gruppi del carico di lavoro"
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# SQL Server - Oggetto Statistiche gruppi del carico di lavoro
  L'oggetto SQLServer: Statistiche gruppi del carico di lavoro contiene contatori delle prestazioni che forniscono informazioni sulle statistiche del gruppo del carico di lavoro di Resource Governor.  
  
 Ciascun gruppo del carico di lavoro attivo crea un'istanza dell'oggetto prestazioni SQLServer: Statistiche gruppi del carico di lavoro con lo stesso nome dell'istanza del gruppo del carico di lavoro di Resource Governor. Nella seguente tabella vengono descritti i contatori supportati in questa istanza.  
  
|Nome contatore|Descrizione|  
|------------------|-----------------|  
|**Thread paralleli attivi**|Numero corrente degli utilizzi di thread paralleli.|  
|**Richieste attive**|Numero di richieste attualmente in esecuzione nel gruppo del carico di lavoro. Tale numero deve essere equivalente al conteggio di righe da sys.dm_exec_requests filtrate per ID del gruppo.|  
|**Richieste bloccate**|Numero di richieste bloccate nel gruppo del carico di lavoro. Tale valore può essere utilizzato per determinare le caratteristiche del carico di lavoro.|  
|**% CPU ritardata**|CPU di sistema ritardata per tutte le richieste nell'istanza specificata dell'oggetto prestazione come percentuale del tempo totale di attività.| 
|**Base % CPU ritardata**|Solo per uso interno.| 
|**% effettiva CPU**|Utilizzo della CPU di sistema da parte di tutte le richieste nell'istanza specificata dell'oggetto prestazione come percentuale del tempo totale di attività.| 
|**Base % effettiva CPU**|Solo per uso interno.| 
|**% di utilizzo CPU**|Utilizzo della larghezza di banda della CPU da parte di tutte le richieste nel gruppo del carico di lavoro misurato in relazione al computer e normalizzato a tutte le CPU del sistema. Tale valore viene modificato quando si modifica la quantità di CPU disponibile per il processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Il valore non è normalizzato secondo i dati ricevuti dal processo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .| 
|**Base % di utilizzo CPU**|Solo per uso interno.| 
|**% CPU violata**|Differenza tra la percentuale di prenotazione della CPU e la percentuale di pianificazione effettiva.|  
|**Tempo massimo CPU richieste (ms)**|Il tempo massimo della CPU, in millisecondi, utilizzato da una richiesta attualmente in esecuzione nel gruppo del carico di lavoro.|  
|**Concessione di memoria massima per le richieste (KB)**|Valore massimo della concessione di memoria, in kilobyte (KB), per una query.|  
|**Ottimizzazioni query/sec**|Numero di ottimizzazioni di query che si sono verificate nel gruppo del carico di lavoro al secondo. Tale valore può essere utilizzato per determinare le caratteristiche del carico di lavoro.|  
|**Richieste in coda**|Numero corrente di richieste in coda in attesa di essere prelevate. Questo conteggio può essere diverso da zero se si verifica una limitazione dopo il raggiungimento del limite GROUP_MAX_REQUESTS.|  
|**Concessioni di memoria ridotte/sec**|Numero di query che ottengono una quantità di memoria inferiore a quella ideale nel gruppo del carico di lavoro.|  
|**Richieste completate/sec**|Numero di richieste completate nel gruppo del carico di lavoro. Questo numero è cumulativo.|  
|**Piani non ottimali/sec**|Numero di piani non ottimali generati nel gruppo del carico di lavoro al secondo.|  
  
## Vedere anche  
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server - Oggetto Statistiche del pool di risorse](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  