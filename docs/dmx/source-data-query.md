---
title: '&lt;query di origine dati&gt; | Documenti Microsoft'
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: DMX
helpviewer_keywords:
- data sources [DMX]
- predictions [DMX]
- source data query element
- queries [DMX], source data
- external data access [DMX]
- <source data query> element
- training mining models
ms.assetid: 9dce5e37-1354-4d28-87c2-f9c419cb5b09
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: be1fd45bfd852174169f004cb165f6b760c07abc
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="ltsource-data-querygt"></a>&lt;query di origine dati&gt;
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Per eseguire il training di un modello di data mining e creare stime da un modello di data mining, è necessario accedere a dati esterni al [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database. Utilizzare il \<query di origine dati > clausola in estensioni DMX (Data Mining) per definire i dati esterni. Il [DMX INSERT INTO &#40; &#41;](../dmx/insert-into-dmx.md), [modello SELECT FROM &#60; &#62; DMX PREDICTION JOIN &#40; &#41; ](../dmx/select-from-model-prediction-join-dmx.md), e [SELECT FROM NATURAL PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md) tutte le istruzioni utilizzano  **\<query di origine dati >**.  
  
## <a name="query-types"></a>Tipi di query  
 I tre modi più comuni per specificare i dati di origine sono i seguenti:  
  
 [DMX OPENQUERY &#40; &#41;](../dmx/source-data-query-openquery.md)  
 Questa istruzione consente di eseguire una query su dati esterni a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], utilizzando un'origine dei dati esistente.  
  
 Mentre **OPENQUERY** è analoga a quella **OPENROWSET**, **OPENQUERY** offre i vantaggi seguenti:  
  
-   Una query DMX è molto più semplice per la scrittura **OPENQUERY**. Anziché creare una nuova stringa di connessione ogni volta che si scrive una query, è possibile avvalersi della stringa di connessione esistente nell'origine dei dati. L'oggetto origine dei dati consente inoltre di controllare l'accesso ai dati per i singoli utenti.  
  
-   L'amministratore dispone di un maggiore controllo sulla modalità di accesso ai dati sul server. Può ad esempio stabilire quali provider caricare nel server e a quali dati esterni è possibile accedere.  
  
 [DMX OPENROWSET &#40; &#41;](../dmx/source-data-query-openrowset.md)  
 Questa istruzione consente di eseguire una query su dati esterni a un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], utilizzando un'origine dei dati esistente.  
  
 [FORMA &#40; DMX &#41;](../dmx/source-data-query-shape.md)  
 Questa istruzione consente di eseguire query su più origini dei dati per creare una tabella nidificata. Utilizzando **forma**, è possibile combinare dati da più origini in una singola tabella gerarchica. In questo modo è possibile avvalersi della capacità di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di nidificare tabelle incorporando una tabella in un'altra tabella.  
  
 Per specificare i dati di origine è inoltre possibile utilizzare uno degli elementi seguenti:  
  
-   Qualsiasi istruzione DMX valida  
  
-   Qualsiasi istruzione MDX (Multidimensional Expressions) valida  
  
-   Una tabella che restituisce una stored procedure  
  
-   Un set di righe di XML for Analysis (XMLA)  
  
-   Un parametro di set di righe  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Data Mining Extensions &#40; DMX &#41; Riferimento istruzione](../dmx/data-mining-extensions-dmx-statements.md)   
 [Tabelle nidificate &#40; Analysis Services - Data Mining &#41;](../analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)  
  
  
