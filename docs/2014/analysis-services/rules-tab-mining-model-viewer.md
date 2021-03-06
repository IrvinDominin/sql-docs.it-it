---
title: Scheda (Visualizzatore modello di Data Mining) regole | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 999ea0b432733fc3458cb6f50e964209c1313b54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059601"
---
# <a name="rules-tab-mining-model-viewer"></a>Scheda Regole (Visualizzatore modello di data mining)
  Usare il riquadro **Regole** in un modello di associazione per visualizzare le regole che l'algoritmo ha consentito di estrarre dai dati. Nelle regole vengono descritte le modalità di correlazione tra gli elementi e di relativo utilizzo per creare indicazioni.  
  
 È possibile utilizzare le opzioni nel visualizzatore per filtrare il numero di regole visualizzate.  
  
> [!WARNING]  
>  Per impostazione predefinita, nel visualizzatore vengono mostrate solo le regole che superano la soglia di probabilità definita in **Probabilità minima** . Non è possibile rendere più piccolo questo valore tramite il visualizzatore, poiché la soglia di probabilità per l'output della regola viene determinata durante la creazione del modello. Per altre informazioni, vedere [Riferimento tecnico per l'algoritmo Microsoft Association Rules](data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 **Per altre informazioni:** [Algoritmo Microsoft Association Rules](data-mining/microsoft-association-algorithm.md)e [Visualizzare un modello utilizzando il Visualizzatore Microsoft Association Rules](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Opzioni  
 **Aggiorna contenuto visualizzatore**  
 Consente di ricaricare il modello di data mining nel visualizzatore.  
  
 **Modello di data mining**  
 Fare clic su un modello di data mining da visualizzare contenuto nella struttura di data mining corrente. Il modello di data mining verrà aperto nel visualizzatore associato.  
  
 **Visualizzatore**  
 Consente di scegliere un visualizzatore da utilizzare per la visualizzazione del modello di data mining selezionato. È possibile usare il visualizzatore personalizzato per ogni modello di data mining o **Microsoft Generic Content Tree Viewer**. Se disponibili, è anche possibile utilizzare i visualizzatori plug-in.  
  
 **Probabilità minima**  
 Modificare questo valore per impostare la probabilità minima richiesta per una regola da visualizzare nel visualizzatore. Aumentando il valore della probabilità verrà ridotto il numero di regole visualizzate.  
  
 **Priorità minima**  
 Modificare questo valore per impostare la priorità minima richiesta per una regola da visualizzare nel visualizzatore. Aumentando il valore della priorità verrà ridotto il numero di regole visualizzate.  
  
 **Regola di filtro**  
 Consente di digitare un valore stringa per filtrare il numero di regole da mostrare nel visualizzatore.  
  
 È anche possibile digitare espressioni regolari .NET come criteri di filtro. Ad esempio, tramite l'espressione seguente vengono restituite tutte le regole contenenti 'Road Bottle Cage' sul lato sinistro della regola:  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 Si noti che potrebbe essere necessario aggiornare la vista per visualizzare l'applicazione dei criteri di filtro. È anche possibile attivare e disattivare l'opzione **Mostra nomi lunghi** per aggiornare l'elenco.  
  
 Per impostazione predefinita, i criteri di filtro si applicano alla combinazione nome e cognome dell'attributo-valore; pertanto, se viene visualizzato solo il nome dell'attributo, è probabile che i criteri di filtro non siano stati applicati correttamente. Usare l'elenco a discesa **Mostra** per selezionare **Mostra nome e valore dell'attributo**, quindi verificare che l'elenco di set di elementi sia filtrato correttamente.  
  
 **Mostra**  
 Consente di impostare la modalità di visualizzazione della regola nel visualizzatore. È possibile selezionare una delle tre opzioni seguenti:  
  
-   Mostra nome e valore dell'attributo  
  
-   Mostra solo il valore dell'attributo  
  
-   Mostra solo il nome dell'attributo  
  
 **Mostra nomi lunghi**  
 Consente di visualizzare il nome della regola nel modo in cui viene visualizzato nel contenuto del modello di data mining.  
  
 **Numero massimo di righe**  
 Consente di impostare il limite del numero di regole che è possibile visualizzare nel visualizzatore.  
  
 **Probabilità**  
 In questa colonna del grafico viene visualizzata la probabilità per ogni regola.  
  
 È possibile fare clic sull'intestazione di colonna per ordinare in base alla probabilità.  
  
 **Priorità**  
 In questa colonna del grafico viene visualizzata la priorità per ogni regola.  
  
 È possibile fare clic sull'intestazione di colonna per ordinare in base alla priorità.  
  
 **Rule**  
 In questa colonna del grafico viene visualizzata la descrizione per ogni regola, in base al formato specificato tramite le opzioni **Mostra** e **Mostra nomi lunghi**.  
  
 È possibile fare clic sull'intestazione di colonna per ordinare in base al testo della regola.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Visualizzatori modello di data mining &#40;Progettazione modelli di Data Mining&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Visualizzatori modello di data mining](data-mining/data-mining-model-viewers.md)  
  
  
