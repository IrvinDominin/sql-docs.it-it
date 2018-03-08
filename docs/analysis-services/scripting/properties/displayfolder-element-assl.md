---
title: Elemento DisplayFolder (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DisplayFolder Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DisplayFolder
helpviewer_keywords: DisplayFolder element
ms.assetid: 55184c02-03e7-4d6c-b87a-d4d34bc11d0e
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 932c14b5781ea6fad0fb292687ec0f8d614ddc94
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="displayfolder-element-assl"></a>Elemento DisplayFolder (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Specifica la cartella in cui elencare l'elemento padre. [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] applicazioni per sviluppatori e amministratori possono supportare l'utilizzo di cartelle di visualizzazione per suddividere più elementi in modo visivo.  
  
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
|Elementi padre|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md), [gerarchia](../../../analysis-services/scripting/objects/hierarchy-element-assl.md), [Kpi](../../../analysis-services/scripting/objects/kpi-element-assl.md), [misura](../../../analysis-services/scripting/objects/measure-element-assl.md), [traduzione](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Nei cubi di dimensioni maggiori possono essere presenti centinaia di misure e gerarchie. Il **DisplayFolder** proprietà definisce l'aspetto utente nel client. Il valore di **DisplayFolder** proprietà può contenere uno o più delle opzioni seguenti:  
  
-   Può essere vuoto, per indicare che la misura non appartiene a una cartella.  
  
-   Contiene il nome di una sola cartella, per indicare che deve essere eseguito il rendering della misura come appartenente a una cartella con lo stesso nome.  
  
-   Contiene più nomi di cartella, separati da una barra rovesciata (\\), che indica una gerarchia di cartelle incorporata.  
  
 Il **DisplayFolder** proprietà si applica a **CalculationProperty** solo se gli elementi il valore di [CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) è impostato su *membro* .  
  
 Gli elementi che corrispondono ai padri di **DisplayFolder** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.CalculationProperty>, <xref:Microsoft.AnalysisServices.Hierarchy>, <xref:Microsoft.AnalysisServices.Kpi>, <xref:Microsoft.AnalysisServices.Measure>, e <xref:Microsoft.AnalysisServices.Translation>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Calculationproperty &#40; ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [Elemento MdxScript &#40; ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [Elemento MdxScripts &#40; ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
