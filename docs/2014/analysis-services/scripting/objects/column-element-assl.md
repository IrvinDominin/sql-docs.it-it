---
title: Elemento Column (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Column Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Column
helpviewer_keywords:
- Column element
ms.assetid: 10dc6d5e-c690-4415-adbb-eaeebaa29cb4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 314e5077f4212e2095d822e0e00d5028ca127a1b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218781"
---
# <a name="column-element-assl"></a>Elemento Column (ASSL)
  Descrive una colonna nella raccolta di colonne associate all'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Columns>  
   <Column xsi:type="MeasureBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="EventColumn">...</Column> <!-- parent of collection: Event -->  
   <!-- or -->  
   <Column xsi:type="MiningModelColumn">...</Column> <!-- parent of collection: MiningModel or MiningModelColumn -->  
   <!-- or -->  
   <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent of collection: MiningStructure or TableMiningStructureColumn -->  
</Columns>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza||  
|Valore predefinito|None|  
|Cardinalità||  
  
|Predecessore o padre|Tipo di dati|  
|------------------------|---------------|  
|[DrillThroughAction](../data-type/binding-data-type-assl.md), [CubeAttributeBinding](../data-type/attributebinding-data-type-assl.md)|  
|[Evento](../data-type/eventcolumn-data-type-assl.md)|  
|[Elemento MiningModel](miningmodel-element-assl.md), [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|[Elemento MiningStructure](miningstructure-element-assl.md), [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[Evento](event-element-assl.md)|1-n: elemento obbligatorio che può presentarsi più di una volta.|  
|Tutti gli altri|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Colonne](../collections/columns-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="see-also"></a>Vedere anche  
 [Gli oggetti &#40;ASSL&#41;](objects-assl.md)  
  
  
