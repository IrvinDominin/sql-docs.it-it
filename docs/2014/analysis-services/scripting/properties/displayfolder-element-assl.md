---
title: Elemento DisplayFolder (ASSL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DisplayFolder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DisplayFolder
helpviewer_keywords:
- DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73de197b50ebd3636cb97e6a011fee1e8c3a71af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220101"
---
# <a name="displayfolder-element-assl"></a>Elemento DisplayFolder (ASSL)
  Specifica la cartella nella quale elencare l'elemento padre. [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] le applicazioni per sviluppatori e amministratori possono supportare l'utilizzo di cartelle di visualizzazione per suddividere più elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<CalculationProperty> <!-- or Hierarchy, Kpi, Measure, Translation -->  
   ...  
   <DisplayFolder>...</DisplayFolder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[CalculationProperty](../objects/calculationproperty-element-assl.md), [gerarchia](../objects/hierarchy-element-assl.md), [Kpi](../objects/kpi-element-assl.md), [misura](../objects/measure-element-assl.md), [traduzione](../objects/translation-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Nei cubi di dimensioni maggiori possono essere presenti centinaia di misure e gerarchie. La proprietà `DisplayFolder` definisce l'aspetto utente nel client. Il valore della proprietà `DisplayFolder` può contenere una delle opzioni seguenti:  
  
-   Può essere vuoto, per indicare che la misura non appartiene a una cartella.  
  
-   Contiene il nome di una sola cartella, per indicare che deve essere eseguito il rendering della misura come appartenente a una cartella con lo stesso nome.  
  
-   Contiene più nomi di cartella separati da una barra rovesciata (\\), che indica una gerarchia di cartelle incorporata.  
  
 Il `DisplayFolder` proprietà si applica a `CalculationProperty` solo se gli elementi il valore di [CalculationType](calculationtype-element-assl.md) è impostata su *membro*.  
  
 Gli elementi che corrispondono agli elementi padre di `DisplayFolder` nel modello a oggetti AMO (Analysis Management Objects) sono <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure> e <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [Proprietà &#40;ASSL&#41;](properties-assl.md)  
  
  
