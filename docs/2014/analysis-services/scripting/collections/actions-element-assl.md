---
title: Elemento Actions (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Actions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Actions
helpviewer_keywords:
- Actions element
ms.assetid: 100a4209-2c22-4902-a8ca-f2bd99bf8fbb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d6fd5c27cd6f8f94102e66d68d9e6cdbaa3984a9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48087111"
---
# <a name="actions-element-assl"></a>Elemento Actions (ASSL)
  Contiene la raccolta di azioni per un [cubo](../objects/cube-element-assl.md) oppure [prospettiva](../objects/perspective-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Cube> <!-- or Perspective -->  
   ...  
   <Actions>  
      <Action xsi:type="DrillThroughAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="ReportAction">...</Action> <!-- ancestor: Cube -->  
      <Action xsi:type="StandardAction">...</Action> <!-- ancestor: Cube -->  
      <!-- or -->  
      <Action xsi:type="PerspectiveAction">...</Action> <!-- ancestor: Perspective -->  
      </Actions>  
      ...  
</Cube>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno (raccolta)|  
|Valore predefinito|Nessuno (raccolta)|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Cubo](../objects/cube-element-assl.md), [prospettiva](../objects/perspective-element-assl.md)|  
  
|Predecessore o padre|Elementi figlio|  
|------------------------|--------------------|  
|[Cubo](../data-type/action-data-type-assl.md), [ReportAction](../data-type/reportaction-data-type-assl.md), [StandardAction](../data-type/standardaction-data-type-assl.md)|  
|[Punto di vista](../data-type/perspectiveaction-data-type-assl.md)|  
  
## <a name="remarks"></a>Note  
 Gli elementi corrispondenti nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.ActionCollection> e <xref:Microsoft.AnalysisServices.PerspectiveActionCollection>.  
  
## <a name="see-also"></a>Vedere anche  
 [Le raccolte &#40;ASSL&#41;](collections-assl.md)  
  
  
