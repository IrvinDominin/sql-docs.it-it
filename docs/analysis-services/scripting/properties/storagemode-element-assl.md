---
title: Elemento StorageMode (ASSL) | Documenti Microsoft
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
apiname: StorageMode Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: StorageMode
helpviewer_keywords: StorageMode element
ms.assetid: 197e8153-1ab6-43ba-a7e9-ae9be19ac511
caps.latest.revision: "40"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5c166d27a9047a0cf5e5aabb9b7f1b0f21713df0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="storagemode-element-assl"></a>Elemento StorageMode (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina la modalità di archiviazione per l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, Partition -->  
   ...  
   <StorageMode>...</StorageMode>  
   ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*MOLAP*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento CUBE &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/cube-element-assl.md), [Dimensione elemento &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/dimension-element-assl.md), [Elemento MeasureGroup &#40; ASSL &#41; ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md), [Partizione elemento &#40; ASSL &#41;](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*MOLAP*|L'elemento padre utilizza l'archiviazione OLAP multidimensionale (MOLAP).|  
|*ROLAP*|L'elemento padre utilizza l'archiviazione OLAP relazionale (ROLAP).|  
|*HOLAP*|L'elemento padre utilizza l'archiviazione OLAP ibrido (HOLAP).<br /><br /> Nota: Questo valore non è valido per [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md) gli elementi padre.|  
|*InMemory*|L'elemento padre utilizza l'archiviazione IMBI.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **StorageMode** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.StorageMode>.  
  
 Gli elementi che corrispondono ai padri di **StorageMode** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.MeasureGroup>, e <xref:Microsoft.AnalysisServices.Partition>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
