---
title: Il tipo di dati AggregationInstanceAttribute (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AggregationInstanceAttribute Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: AggregationInstanceAttribute data type
ms.assetid: fc5a98bf-7c3c-4faf-b9f8-16eb073d7dc7
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 985222fa93becdf4a83fef7e4ba79844da912553
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="aggregationinstanceattribute-data-type-assl"></a>Tipo di dati AggregationInstanceAttribute (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce un tipo di dati primitivo che rappresenta le informazioni su un attributo utilizzato da un'istanza di aggregazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AggregationInstanceAttribute>  
   <AttributeID>...</AttributeID>  
   <KeyColumns>...</KeyColumns>  
</AggregationInstanceAttribute>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|None|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md), [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|Elementi derivati|[Attribute](../../../analysis-services/scripting/objects/attribute-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Analysis Services Scripting Language tipi di dati XML &#40; ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
