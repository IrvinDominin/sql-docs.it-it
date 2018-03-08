---
title: Le conversioni del cubo | Documenti Microsoft
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
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- multiple language support [Analysis Services]
- international considerations [Analysis Services]
- global considerations [Analysis Services]
- cubes [Analysis Services], translations
- OLAP objects [Analysis Services], translations
- translations [Analysis Services], cubes
ms.assetid: 4e4fd6a4-d324-4508-b75a-2a57de9ab8ff
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 65ba720400e5549bfe640297269f4d00afe5c988
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="cube-translations"></a>Traduzioni di cubi
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Una traduzione è un semplice meccanismo che consente di modificare la lingua delle etichette e delle didascalie visualizzate. Ogni traduzione è definita come una coppia di valori: una stringa con il testo tradotto e un numero con l'ID della lingua. Le traduzioni sono disponibili per tutti gli oggetti in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Nel caso delle dimensioni è possibile tradurre anche i valori di attributo. L'applicazione client è responsabile della ricerca dell'impostazione della lingua definita dall'utente e del passaggio alla visualizzazione di tutte le didascalie e le etichette nella lingua in questione. Un oggetto può disporre di un numero illimitato di traduzioni.  
  
 Un oggetto <xref:Microsoft.AnalysisServices.Translation> semplice è composto dal numero ID della lingua e dalla didascalia tradotta. Il numero di ID di lingua è un **intero** con l'ID di lingua. La didascalia tradotta è il testo tradotto.  
  
 In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], conversione di un cubo è una rappresentazione specifiche della lingua del nome di un oggetto cubo, ad esempio una didascalia o una cartella di visualizzazione. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta anche conversioni di dimensione e nomi del membro.  
  
 Le traduzioni offrono supporto server per applicazioni client in grado di supportare più lingue. Spesso, i dati dei cubi vengono visualizzati da utenti di paesi diversi. La possibilità di tradurre i diversi elementi di un cubo in diverse lingue è utile in quanto consente a tali utenti di visualizzare e comprendere i metadati del cubo. Un utente aziendale in Francia, ad esempio, può accedere a un cubo da una workstation in cui vengono utilizzate le impostazioni locali francesi e visualizzare i valori delle proprietà dell'oggetto in francese. Analogamente, un utente aziendale in Germania può accedere allo stesso cubo da una workstation in cui vengono utilizzate le impostazioni locali tedesche e visualizzare i valori delle proprietà dell'oggetto in tedesco.  
  
 Le informazioni sulle regole di confronto e sulla lingua per il computer client sono archiviate in forma di identificatore delle impostazioni locali (LCID). Al momento della connessione, il client passa l'identificatore delle impostazioni locali all'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. L'istanza utilizza l'identificatore per determinare il set di traduzioni da utilizzare per visualizzare i metadati degli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per ogni utente aziendale. Se un oggetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non contiene la traduzione specificata, per restituire il contenuto al client viene utilizzata la lingua predefinita.  
  
## <a name="see-also"></a>Vedere anche  
 [Traduzioni delle dimensioni](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Supporto delle traduzioni in Analysis Services](../../analysis-services/translation-support-in-analysis-services.md)   
 [Suggerimenti per la globalizzazione e procedure consigliate &#40; Analysis Services &#41;](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
