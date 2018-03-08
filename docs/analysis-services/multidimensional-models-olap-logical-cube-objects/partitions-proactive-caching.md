---
title: Memorizzazione nella cache attiva (partizioni) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 25a6306e19f6eff72f84fffde0372ed0bc3d76e6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="partitions---proactive-caching"></a>Le partizioni, la memorizzazione nella cache
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
La memorizzazione nella cache attiva fornisce funzionalità automatiche di creazione e gestione della cache MOLAP per gli oggetti OLAP. I cubi incorporano immediatamente le modifiche apportate ai dati nel database, in base alle notifiche ricevute dal database. L'obiettivo della memorizzazione nella cache attiva consiste nel fornire le prestazioni della modalità MOLAP standard, garantendo l'immediatezza e la semplicità di gestione offerte da ROLAP.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching> semplice è composto dalla specifica temporale e dalla notifica per la tabella. La specifica temporale definisce l'intervallo di tempo entro il quale eseguire l'aggiornamento della cache dopo la ricezione di una notifica di modifica. La notifica per la tabella definisce lo schema di notifica tra la tabella dati e l'oggetto <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
 La modalità di archiviazione OLAP multidimensionale (MOLAP) consente di ottimizzare il tempo di risposta alle query, ma comporta una certa latenza dei dati. La modalità di archiviazione OLAP relazionale (ROLAP) in tempo reale consente agli utenti di vedere immediatamente le ultime modifiche apportate in un'origine dei dati, ma comporta un notevole calo delle prestazioni rispetto alla modalità di archiviazione MOLAP perché non esistono riepiloghi precalcolati dei dati e perché i dati relazionali non sono ottimizzati per query di tipo OLAP. Se in un'applicazione è necessario consentire agli utenti di visualizzare dati recenti, ma si desidera anche usufruire dei vantaggi in termini di prestazioni offerti dalla modalità di archiviazione MOLAP, è possibile utilizzare un'opzione di SQL Server Analysis Services denominata memorizzazione nella cache attiva, soprattutto in combinazione con l'utilizzo di partizioni. La memorizzazione nella cache attiva viene impostata in base alla partizione e in base alla dimensione. Le opzioni di memorizzazione nella cache attiva consentono di raggiungere un compromesso tra le prestazioni avanzate dell'archiviazione MOLAP e l'immediatezza dell'archiviazione ROLAP e supportano l'elaborazione automatica delle partizioni in caso di modifica dei dati sottostanti o in base a una pianificazione impostata.  
  
## <a name="proactive-caching-configuration-options"></a>Opzioni di configurazione della memorizzazione nella cache attiva  
 In SQL Server Analysis Services sono disponibili varie opzioni di configurazione della memorizzazione nella cache attiva che consentono di ottimizzare le prestazioni, ridurre al minimo la latenza e pianificare l'elaborazione. Le caratteristiche della memorizzazione nella cache attiva semplificano il processo di gestione dell'obsolescenza dei dati. Le impostazioni di memorizzazione nella cache attiva determinano la frequenza con cui viene ricompilata la struttura OLAP multidimensionale, denominata anche cache MOLAP, se vengono eseguite query sullo spazio di archiviazione MOLAP obsoleto durante la ricompilazione della cache o sull'origine dei dati ROLAP sottostante e se la cache viene ricompilata in base a una pianificazione o in base alle modifiche apportate nel database.  
  
### <a name="minimizing-latency"></a>Riduzione al minimo della latenza  
 Quando la memorizzazione nella cache attiva è impostata in modo da ridurre al minimo la latenza, le query utente eseguite su un oggetto OLAP vengono indirizzate allo spazio di archiviazione ROLAP o MOLAP a seconda che siano state apportate modifiche recenti ai dati e del modo in cui è stata configurata la memorizzazione nella cache attiva. Il motore query indirizza le query verso l'origine dei dati nello spazio di archiviazione MOLAP fino a quando non vengono apportate modifiche nell'origine dei dati. Per ridurre al minimo la latenza, dopo l'implementazione di modifiche in un'origine dei dati gli oggetti MOLAP nella cache possono essere eliminati e le query indirizzate allo spazio di archiviazione ROLAP mentre gli oggetti MOLAP vengono ricompilati nella cache. Dopo la ricompilazione e l'elaborazione degli oggetti MOLAP, le query vengono indirizzate automaticamente allo spazio di archiviazione MOLAP. L'aggiornamento della cache può essere estremamente rapido per una partizione di piccole dimensioni, ad esempio per la partizione corrente che può essere limitata al giorno corrente.  
  
### <a name="maximizing-performance"></a>Ottimizzazione delle prestazioni  
 Per ottimizzare le prestazioni riducendo al tempo stesso la latenza, è inoltre possibile utilizzare la memorizzazione nella cache senza eliminare gli oggetti MOLAP correnti. Le query in questo caso continuano a essere eseguite sugli oggetti MOLAP mentre i dati vengono letti ed elaborati in una nuova cache. Questa modalità di archiviazione consente di ottenere prestazioni migliori, ma è possibile che i dati restituiti dalle query non siano aggiornati durante la fase di compilazione della nuova cache.  
  
## <a name="see-also"></a>Vedere anche  
 [Archiviazione della dimensione](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Archiviazione della partizione set &#40; Analysis Services - multidimensionale &#41;](../../analysis-services/multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
