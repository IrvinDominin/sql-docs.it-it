---
title: Elemento DataSourceID (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DataSourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 2d71ba53-1684-4da0-8da4-fb75033c971b
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 86a5e07518097e01509f24f2969580dec7ba0c34
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37263587"
---
# <a name="datasourceid-element-assl"></a>Elemento DataSourceID (ASSL)
  Identifica la [DataSource](../objects/datasource-element-assl.md) associato l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CubeBinding> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</CubeBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|Dipende dal contesto|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md), [CubeDimensionBinding](../data-type/binding-data-type-assl.md), [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md), [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md), [QueryBinding](../data-type/querybinding-data-type-assl.md), [DataSourceView](../objects/datasourceview-element-assl.md), [TableBinding](../data-type/tablebinding-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Gli elementi che corrispondono ai padri di `DataSourceID` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CubeDimensionBinding>, <xref:Microsoft.AnalysisServices.DimensionBinding>, <xref:Microsoft.AnalysisServices.MeasureGroupBinding>, <xref:Microsoft.AnalysisServices.QueryBinding>, <xref:Microsoft.AnalysisServices.DataSourceView> e <xref:Microsoft.AnalysisServices.TableBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ID &#40;ASSL&#41;](id-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
