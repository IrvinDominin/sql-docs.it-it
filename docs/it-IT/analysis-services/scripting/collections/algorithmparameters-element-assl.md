---
title: Elemento AlgorithmParameters (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- AlgorithmParameters Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AlgorithmParameters
helpviewer_keywords:
- AlgorithmParameters element
ms.assetid: 240cbb60-7fa3-46ef-b5be-cd14c9ec10de
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d09c836acab6843fa85ef5b206f7f72694bc975d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="algorithmparameters-element-assl"></a>Elemento AlgorithmParameters (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene la raccolta di parametri per l'algoritmo utilizzato da un [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel>  
   ...  
   <AlgorithmParameters>  
      <AlgorithmParameter>...</AlgorithmParameter>  
   </AlgorithmParameters>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)|  
|Elementi figlio|[AlgorithmParameter](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **AlgorithmParameters** raccolta contiene un set estensibile di parametri, rappresentato come coppie nome/valore, per un algoritmo del modello di data mining. Il set di parametri applicabili è dipendente dall'algoritmo. Per ulteriori informazioni sui parametri per un algoritmo specifico, vedere la documentazione appropriata relativa all'algoritmo.  
  
 I parametri dell'algoritmo disponibili, incluse le informazioni relative a convalida e visualizzazione, possono essere recuperati dal set di righe dello schema DMSCHEMA_MINING_SERVICE_PARAMETERS.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AlgorithmParameterCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Algorithm &#40;ASSL&#41;](../../../analysis-services/scripting/properties/algorithm-element-assl.md)   
 [Set di righe DMSCHEMA_MINING_SERVICE_PARAMETERS](../../../analysis-services/schema-rowsets/data-mining/dmschema-mining-service-parameters-rowset.md)   
 [Raccolte & #40; ASSL & #41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  
