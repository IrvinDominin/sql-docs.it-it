---
title: SELECT INTO (DMX) | Documenti Microsoft
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
f1_keywords:
- SELECT
- SELECT_INTO
- SELECT INTO
dev_langs: DMX
helpviewer_keywords:
- mining models [Analysis Services], copying
- SELECT INTO statement
- mining models [Analysis Services], creating
- copying mining models
ms.assetid: 31ab9b4c-e20d-41ee-886f-6665c22c6ad5
caps.latest.revision: "42"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5d373c62b61469835ed8a6c41e9231c5eff67fd8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="select-into-dmx"></a>SELECT INTO (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crea un nuovo modello di data mining compilato in base alla struttura di data mining di un modello di data mining esistente. Il **SELECT INTO** istruzione crea il nuovo modello di data mining copiando lo schema e altre informazioni che non sono specifici dell'algoritmo effettivo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT INTO <new model>   
USING <algorithm> [(<parameter list>)] [WITH DRILLTHROUGH[,] [FILTER(<expression>)]]  
FROM <existing model>  
```  
  
## <a name="arguments"></a>Argomenti  
 *nuovo modello*  
 Nome univoco del nuovo modello da creare.  
  
 *algoritmo*  
 Nome definito dal provider di un algoritmo di data mining.  
  
 *elenco di parametri*  
 Facoltativo. Elenco delimitato da virgole dei parametri definiti dal provider per l'algoritmo.  
  
 *expression*  
 Espressione che restituisce una condizione di filtro valida sui dati di training. Per ulteriori informazioni sulle espressioni che possono essere utilizzate come filtri, vedere [filtri per i modelli di Data Mining &#40; Analysis Services - Data Mining &#41; ](../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).  
  
 *modello esistente*  
 Nome del modello esistente da copiare.  
  
## <a name="remarks"></a>Osservazioni  
 Se il modello esistente è stato sottoposto a training, il nuovo modello verrà automaticamente elaborato quando viene eseguita l'istruzione. In caso contrario il nuovo modello rimarrà non elaborato.  
  
 Il **SELECT INTO** istruzione funziona solo se la struttura del modello esistente è compatibile con l'algoritmo del nuovo modello. Pertanto, questa istruzione è molto utile per creare e testare rapidamente modelli basati sullo stesso algoritmo. Se si modifica il tipo di algoritmo, il nuovo algoritmo deve supportare il tipo di dati di ogni colonna presente nel modello esistente, altrimenti potrebbe verificarsi un errore quando viene elaborato il modello.  
  
 Il **WITH DRILLTHROUGH** clausola consente il drill-through sul nuovo modello di data mining. È possibile attivare il drill-through solo al momento della creazione del modello.  
  
## <a name="example-1-altering-the-parameters-of-the-model"></a>Esempio 1: Modifica dei parametri del modello  
 L'esempio seguente crea un nuovo modello di data mining basato su un modello di data mining esistente, `TM_Clustering`, create nel [Basic Data Mining Tutorial](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c). Il parametro CLUSTER_COUNT viene modificato in modo che nel nuovo modello esistano al massimo cinque cluster. Nel modello esistente viene invece utilizzato il valore predefinito 10.  
  
```  
SELECT * INTO [New_Clustering]  
USING [Microsoft_Clustering] (CLUSTER_COUNT = 5)   
FROM [TM Clustering]  
```  
  
## <a name="example-2-adding-a-filter-to-the-model"></a>Esempio 2: Aggiunta di un filtro al modello  
 Nell'esempio seguente viene creato un nuovo modello di data mining basato su un modello di data mining esistente e viene aggiunto un filtro nel modello. Il filtro limita i dati di training solo ai clienti che vivono in un'area specifica.  
  
```  
SELECT * INTO [Clustering Europe Region]  
USING [Microsoft_Clustering] WITH FILTER(Region='Europe')  
FROM [TM Clustering]  
```  
  
> [!NOTE]  
>  I filtri applicati alla tabella del case possono essere modificati mediante l'istruzione SELECT INTO come mostrato in questo esempio. Tuttavia, se il modello originale contiene un filtro in una tabella nidificata, il filtro della tabella nidificata non può essere modificato o rimosso mediante questa sintassi, ma viene copiato dal modello originale senza alcuna modifica. Per creare un modello con un filtro diverso in una tabella nidificata, utilizzare la sintassi ALTER STRTUCTURE...ADD MODEL.  
  
## <a name="see-also"></a>Vedere anche  
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40; DMX &#41; Istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
