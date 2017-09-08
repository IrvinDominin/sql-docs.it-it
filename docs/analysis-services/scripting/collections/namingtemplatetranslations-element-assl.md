---
title: Elemento NamingTemplateTranslations (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- NamingTemplateTranslations Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NamingTemplateTranslations
helpviewer_keywords:
- NamingTemplateTranslations element
ms.assetid: fde65778-1fa3-490a-9874-8bf2052ef25c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ed377512b4d2e27e6f3ec0d85066ac72b9996499
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="namingtemplatetranslations-element-assl"></a>Elemento NamingTemplateTranslations (ASSL)
  Fornisce una raccolta di conversioni localizzate per il [NamingTemplate](../../../analysis-services/scripting/properties/namingtemplate-element-assl.md) dell'elemento padre, [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md).  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute xsi:type="DimensionAttribute">  
   ...  
   <NamingTemplateTranslations>  
            <NamingTemplateTranslation xsi:type="Translation">...</NamingTemplateTranslation>  
...</NamingTemplateTranslations>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](../../../analysis-services/scripting/objects/attribute-element-assl.md) di tipo [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|Elementi figlio|[NamingTemplateTranslation](../../../analysis-services/scripting/objects/namingtemplatetranslation-element-assl.md) di tipo [traduzione](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore del **NamingTemplateTranslation** elemento viene utilizzato solo dagli attributi padre (in altre parole, il valore di [utilizzo](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md) dell'elemento padre **DimensionAttribute**è impostato su *padre*.)  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.DimensionAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolte &#40; ASSL &#41;](../../../analysis-services/scripting/collections/collections-assl.md)  
  
  