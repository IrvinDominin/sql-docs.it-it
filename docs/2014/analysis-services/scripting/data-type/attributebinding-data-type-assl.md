---
title: Tipo di dati AttributeBinding (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- AttributeBinding Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- AttributeBinding
helpviewer_keywords:
- AttributeBinding data type
ms.assetid: 24d511a9-d0eb-4150-9f78-541e03963d67
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c5330fe2694c8d15b2e2fa1354a8deddbaaff269
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48229031"
---
# <a name="attributebinding-data-type-assl"></a>Tipo di dati AttributeBinding (ASSL)
  Definisce un tipo di dati derivato che rappresenta un'associazione per un [attributo](../objects/attribute-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<AttributeBinding>  
   <AttributeID>...</AttributeID>  
      <Type>...</Type>  
   <Ordinal>...</Ordinal>  
</AttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipi di dati di base|[associazione](binding-data-type-assl.md)|  
|Tipi di dati derivati|None|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|[Elemento AttributeID](../properties/id-element-assl.md), [ordinale](../properties/ordinal-element-assl.md), [tipo](../properties/type-element-binding-assl.md)|  
|Elementi derivati|Vedere [associazione](binding-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sul `Binding` tipo di dati, incluse le tabelle di oggetti di Analysis Services Scripting Language (ASSL) derivati dal `Binding` tipo di dati, vedere [associazione tipo di dati &#40;ASSL&#41;](binding-data-type-assl.md).  
  
 Per una panoramica delle associazioni di dati in ASSL, vedere [origini dati e associazioni &#40;multidimensionale di SSAS&#41;](../../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.AttributeBinding>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi Analysis Services Scripting Language XML dei dati &#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
