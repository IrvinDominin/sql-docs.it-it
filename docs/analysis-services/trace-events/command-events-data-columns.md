---
title: Colonne di dati degli eventi di comando | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7f3c3be311e1f0ce7b53bd35b90fb94dfc03f07b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="command-events-data-columns"></a>Colonne di dati degli eventi di comando
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]La tabella seguente elenca le colonne di dati per ogni classe di evento di **eventi di comando** categoria di eventi.  
  
 La categoria di eventi **Eventi di comando** include le classi di eventi seguenti:  
  
-   [Classe Command Begin](#bkmk_1)  
  
-   [Classe Command End](#bkmk_2)  
  
 Nelle tabelle seguenti vengono elencate le colonne di dati per ognuna di queste classi di eventi.  
  
##  <a name="bkmk_1"></a> Colonne di dati della classe Command Begin  
  
|Colonna di dati|Description|  
|-----------------|-----------------|  
|ConnectionID|Contiene l'ID di connessione univoco associato all'evento di comando.|  
|TextData|Contiene i dati di tipo text associati all'evento di comando.|  
|ServerName|Contiene il nome dell'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di comando.|  
|CurrentTime|Contiene l'ora corrente dell'evento di comando.|  
|DatabaseName|Contiene il nome del database in cui è in esecuzione il comando.|  
|EventSubclass|Contiene la classe di evento dell'evento di comando. I valori supportati sono:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Altro|  
|NTUserName|Contiene il nome utente di Windows associato all'evento di comando. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|RequestProperties|Contiene le proprietà della richiesta XMLA (XML for Analysis) associata all'evento di comando.|  
|SPID|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di comando. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|StartTime|Contiene l'ora, se disponibile, in cui è iniziato l'evento di comando.|  
|SessionType|Contiene l'entità che ha provocato l'operazione.|  
|NTDomainName|Contiene l'account di dominio di Windows associato all'evento di autorizzazione per l'oggetto.|  
|ClientProcessID|Contiene l'ID del processo client univoco associato all'evento di comando.|  
  
##  <a name="bkmk_2"></a> Colonne di dati della classe Command End  
  
|Colonna di dati|Description|  
|-----------------|-----------------|  
|ConnectionID|Contiene l'ID di connessione univoco associato all'evento di comando.|  
|TextData|Contiene i dati di tipo text associati all'evento di comando.|  
|ServerName|Contiene il nome dell'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in cui è stato generato l'evento di comando.|  
|CurrentTime|Contiene l'ora corrente dell'evento di comando. Per il filtro, i formati sono *AAAA*-*MM*-*GG* e *AAAA*-*MM*-*GG HH*:*MM*:*SS*.|  
|DatabaseName|Contiene il nome del database in cui è in esecuzione il comando.|  
|Duration|Contiene un valore approssimativo dell'intervallo di tempo tra l'evento di inizio comando e l'evento di fine comando.|  
|EndTime|Contiene l'ora di fine dell'evento di comando. Per il filtro, i formati sono *AAAA*-*MM*-*GG* e *AAAA*-*MM*-*GG HH*:*MM*:*SS*.|  
|EventSubclass|Contiene la classe di evento dell'evento di comando. I valori supportati sono:<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Altro|  
|NTCanonicalUserName|Contiene il nome utente di Windows associato all'evento di comando. Il nome utente è in forma canonica. Ad esempio, engineering.microsoft.com/software/user.|  
|NTUserName|Contiene l'account utente di Windows associato all'evento di comando.|  
|SPID|Contiene l'ID del processo server (SPID, Server Process ID) che identifica in modo univoco la sessione utente associata all'evento di comando. Lo SPID corrisponde direttamente al GUID di sessione utilizzato da XMLA.|  
|StartTime|Contiene l'ora, se disponibile, in cui è iniziato l'evento di fine comando.|  
|CPUTime|Contiene la quantità di tempo CPU, in millisecondi, utilizzata dal processo tra l'evento di inizio comando e quello di fine comando.|  
|Errore|Contiene il numero di errore di eventuali errori associati all'evento di comando.|  
|Severity|Contiene il livello di gravità di un'eccezione associata all'evento di comando. I valori possibili sono:<br /><br /> 0 = Esito positivo<br /><br /> 1 = Messaggio informativo<br /><br /> 2 = Avviso<br /><br /> 3 = Errore|  
|Esito positivo|Contiene informazioni sull'esito positivo o negativo dell'evento di comando. I valori possibili sono:<br /><br /> 0 = esito negativo<br /><br /> 1 = esito positivo|  
|SessionType|Contiene l'entità che ha provocato l'operazione associata all'evento di fine comando.|  
|NTDomainName|Contiene l'account di dominio di Windows associato all'evento di comando.|  
|ClientProcessID|Contiene l'ID del processo client univoco associato all'evento di comando.|  
  
## <a name="see-also"></a>Vedere anche  
 [Command Events Event Category](../../analysis-services/trace-events/command-events-event-category.md)  
  
  
