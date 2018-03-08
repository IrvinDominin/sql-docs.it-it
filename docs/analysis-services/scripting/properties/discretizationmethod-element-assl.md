---
title: Elemento DiscretizationMethod (ASSL) | Documenti Microsoft
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
apiname: DiscretizationMethod Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DiscretizationMethod
helpviewer_keywords: DiscretizationMethod element
ms.assetid: 4cfe015f-ad6c-47e1-8aff-c9c7677867b1
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fd84d0426afa9ee1272c26c8ca7ac302972748b4
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="discretizationmethod-element-assl"></a>Elemento DiscretizationMethod (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Definisce il metodo da utilizzare per la discretizzazione.  
  
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
  
## <a name="remarks"></a>Osservazioni  
 Il valore della **DiscretizationMethod** elemento determina come i valori per il **DimensionAttribute** o **ScalarMiningStructureColumn** vengono discretizzati o organizzati in un set di gruppi specifico. Per ulteriori informazioni sui metodi di discretizzazione, vedere [metodi di discretizzazione &#40; Data Mining &#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Automatico*|Equivale al metodo di discretizzazione AUTOMATIC per le colonne della struttura di data mining.|  
|*EqualAreas*|Equivale al metodo di discretizzazione EQUAL_AREAS per le colonne della struttura di data mining.|  
|*Cluster*|Equivale al metodo di discretizzazione CLUSTERS per le colonne della struttura di data mining.|  
|*Thresholds*|Equivale al metodo di discretizzazione THRESHOLDS per le colonne della struttura di data mining.|  
|*EqualRanges*|Equivale al metodo di discretizzazione EQUAL_RANGES per le colonne della struttura di data mining.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **DiscretizationMethod** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.DiscretizationMethod>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
