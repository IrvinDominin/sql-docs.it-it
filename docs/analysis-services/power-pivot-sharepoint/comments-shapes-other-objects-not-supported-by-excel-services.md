---
title: I commenti, forme o altri oggetti non supportati da Excel Services | Documenti Microsoft
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
ms.assetid: ade92e15-dfbf-496b-9378-a00bd83ba750
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e81433f28d9b3b3f20ceb99f2e6436a689ba4e86
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="comments-shapes-other-objects-not-supported-by-excel-services"></a>Commenti, forme, altri oggetti non supportati da Excel Services
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Questo errore si verifica quando si aggiungono filtri dei dati a una cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] da un elenco dei campi [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .  
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Applicabile a|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] per SharePoint|  
|Versione prodotto|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Causa|In Excel Web Access non è possibile eseguire il rendering dell'oggetto Shape usato per controllare la collocazione e la formattazione dei filtri dei dati aggiunti a una cartella di lavoro dall'elenco dei campi [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
|Testo del messaggio|Le funzionalità seguenti non sono supportate in Excel Services e potrebbero non venire visualizzate del tutto o parzialmente:<br /><br /> Commenti, forme o altri oggetti<br /><br /> Alcune funzionalità, ad esempio le query su dati esterni, visualizzano i dati memorizzati nella cache che possono essere aggiornati solo in Microsoft Excel.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene visualizzato in Excel Web Access quando si apre una cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] in un browser e si fa clic sul pulsante **Dettagli** per il messaggio **Funzionalità non supportate. È possibile che la cartella di lavoro non venga visualizzata come previsto**.  
  
 Questo errore si verifica perché la cartella di lavoro di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] contiene filtri dei dati il cui layout viene controllato da un oggetto Shape nascosto in Excel. L'oggetto Shape controlla la formattazione e la collocazione dei filtri dei dati nelle posizioni orizzontali e verticali.  
  
 In Excel Services non è possibile eseguire il rendering di un oggetto Shape ma, poiché l'oggetto è nascosto, il fatto che non venga eseguito il rendering non rappresenta un problema.  
  
## <a name="user-action"></a>Azione dell'utente  
 Questo errore può essere ignorato. Fare clic su **OK** per chiudere il messaggio di errore e continuare a usare la cartella di lavoro e i filtri dei dati senza alcun problema.  
  
  
