---
title: Il tipo di dati Groupdimension (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: MeasureGroupDimension Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: MeasureGroupDimension
helpviewer_keywords: MeasureGroupDimension data type
ms.assetid: 9d1c1c19-31ce-4c42-b2e6-4c1b08875a83
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ea26210ea35408c1514a5de2a2b08342223c031a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="measuregroupdimension-data-type-assl"></a>Tipo di dati GroupDimension (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce un tipo di dati primitivo astratto che rappresenta la relazione tra una dimensione e un gruppo di misure.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MeasureGroupDimension>  
   <CubeDimensionID>...</CubeDimensionID>  
      <Annotations>...</Annotations>  
   <Source>...</Source>  
</MeasureGroupDimension>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|[DataMiningMeasureGroupDimension](../../../analysis-services/scripting/data-type/dataminingmeasuregroupdimension-data-type-assl.md), [DegenerateMeasureGroupDimension](../../../analysis-services/scripting/data-type/degeneratemeasuregroupdimension-data-type-assl.md), [ManyToManyMeasureGroupDimension](../../../analysis-services/scripting/data-type/manytomanymeasuregroupdimension-data-type-assl.md), [ReferenceMeasureGroupDimension](../../../analysis-services/scripting/data-type/referencemeasuregroupdimension-data-type-assl.md), [RegularMeasureGroupDimension](../../../analysis-services/scripting/data-type/regularmeasuregroupdimension-data-type-assl.md)|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Annotazioni](../../../analysis-services/scripting/collections/annotations-element-assl.md), [CubeDimensionID](../../../analysis-services/scripting/properties/cubedimensionid-element-assl.md), [origine](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|Elementi derivati|[Dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) ([dimensioni](../../../analysis-services/scripting/collections/dimensions-element-assl.md) insieme di [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Ogni **MeasureGroupDimension** è un riferimento a una delle dimensioni nel cubo. Questi definiscono quali dimensioni del cubo si applicano al gruppo di misure.  
  
 Il set di attributi fornito determina la granularità (ambito) con la quale sono note le misure sul gruppo di misure. Ad esempio, le misure che rappresentano le vendite del prodotto sono contenute nel gruppo di misure delle Vendite. Le informazioni per queste misure sono archiviate nell'origine dei dati sottostanti con una granularità mensile, piuttosto che settimanale o giornaliera. In questo caso, solo l'attributo mese sarebbe elencato per il **MeasureGroupDimension** che descrive la relazione tra una dimensione temporale e il gruppo di misure Sales. In rari casi, la granularità potrebbe essere definita in termini di set di attributi. Ad esempio, dato il set di attributi {giorno, settimana, mese anno}, dove il giorno implica settimana e mese, ma la settimana non implica il mese, le misure contenute nel gruppo di misure delle Previsioni potrebbero essere conosciute da mese e settimana, ma non dal giorno.  
  
 Se non è fornito alcun attributo, è come se solo l'attributo chiave per la dimensione venisse elencato (definizione del livello più basso della granularità). Ogni partizione di un gruppo di misure deve avere la stessa granularità. Il set di attributi elencato non deve essere ridondante riguardo alle relazioni tra attributi. Ad esempio, se il mese implica l’anno, la granularità è definita come mese, non mese e anno.  
  
 Oggetto **MeasureGroupDimension** deve includere una gerarchia solo se ha dati specifici al riguardo. (Non c'è modo di selezionare quali gerarchie si applicano a un particolare gruppo di misure). Analogamente, è necessario includere un [MeasureGroupAttribute](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md) solo se ha dati specifici al riguardo.  
  
 Ogni gerarchia deve essere un subset delle gerarchie incluse nel [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md). Non è possibile selezionare i livelli, sebbene alcuni livelli potrebbero essere disabilitati a seconda della granularità del gruppo di misure.  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.MeasureGroupDimension>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
