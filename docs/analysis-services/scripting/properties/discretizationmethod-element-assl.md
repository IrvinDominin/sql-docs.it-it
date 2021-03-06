---
title: Elemento DiscretizationMethod (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 81064689788574061f103b973a5435beb3e83893
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38002203"
---
# <a name="discretizationmethod-element-assl"></a>Elemento DiscretizationMethod (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce il metodo da usare per la discretizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationMethod>...</DiscretizationMethod>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*Nessuno*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Il valore dei **DiscretizationMethod** elemento determina come i valori per il **DimensionAttribute** oppure **ScalarMiningStructureColumn** vengono discretizzati o organizzati in un set di gruppi specifico. Per altre informazioni sui metodi di discretizzazione, vedere [metodi di discretizzazione &#40;Data Mining&#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Automatico*|Equivale al metodo di discretizzazione AUTOMATIC per le colonne della struttura di data mining.|  
|*EqualAreas*|Equivale al metodo di discretizzazione EQUAL_AREAS per le colonne della struttura di data mining.|  
|*Cluster*|Equivale al metodo di discretizzazione CLUSTERS per le colonne della struttura di data mining.|  
|*Thresholds*|Equivale al metodo di discretizzazione THRESHOLDS per le colonne della struttura di data mining.|  
|*EqualRanges*|Equivale al metodo di discretizzazione EQUAL_RANGES per le colonne della struttura di data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **DiscretizationMethod** nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
