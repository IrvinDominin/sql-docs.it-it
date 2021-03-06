---
title: Elemento MembersWithData (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- MembersWithData Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MembersWithData
helpviewer_keywords:
- MembersWithData element
ms.assetid: 845087a2-b12d-4344-a8be-85ca61155296
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 17a3fced7327c1fb2211b1c80f774ae859757952
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089647"
---
# <a name="memberswithdata-element-assl"></a>Elemento MembersWithData (ASSL)
  Determina se visualizzare i membri dei dati per i membri non foglia nell'attributo padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <MembersWithData>...</MembersWithData>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*NonLeafDataVisible*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore del `MembersWithData` elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore della [utilizzo](usage-element-dimensionattribute-assl.md) elemento del `DimensionAttribute` elemento padre è impostato su *padre*) per determinare se Per visualizzare i membri di dati per i membri non foglia nell'attributo padre. Per altre informazioni sui membri dei dati, vedere [Attributi nelle gerarchie padre-figlio](../../multidimensional-models/parent-child-dimension-attributes.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*NonLeafDataHidden*|I dati non foglia sono nascosti.|  
|*NonLeafDataVisible*|I dati non foglia sono visibili.|  
  
 L'enumerazione che corrisponde ai valori consentiti di `MembersWithData` nel modello a oggetti AMO (Analysis Management Objects) è <xref:Microsoft.AnalysisServices.MembersWithData>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento MembersWithDataCaption &#40;ASSL&#41;](caption-element-assl.md)   
 [Tipo di dati DimensionAttribute &#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
