---
title: Tipo di elemento (PerspectiveCalculation) (ASSL) | Documenti Microsoft
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
apiname: Type Element (PerspectiveCalculation)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: d7b87aea-3265-4f3c-a7ee-4f3e90f9a0b7
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1418dc67807b1d5a1833829f257e5549f1a92aa1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="type-element-perspectivecalculation-assl"></a>Elemento Type (PerspectiveCalculation) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Indica il tipo del [PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<PerspectiveCalculation>  
   ...  
   <Type>...</Type>  
   ...  
</PerspectiveCalculation>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Oggetto PerspectiveCalculation](../../../analysis-services/scripting/data-type/perspectivecalculation-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Membro*|membro calcolato|  
|*Set*|Set denominato|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.PerspectiveCalculationType>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.PerspectiveCalculation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
