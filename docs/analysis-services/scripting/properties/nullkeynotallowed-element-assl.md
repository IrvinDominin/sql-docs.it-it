---
title: Elemento NullKeyNotAllowed (ASSL) | Documenti Microsoft
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
apiname: NullKeyNotAllowed Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: NullKeyNotAllowed
helpviewer_keywords: NullKeyNotAllowed element
ms.assetid: 4ece99eb-954b-4da1-add4-dd9efd5fff0a
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dfb9349ff91eae2c4e783f347f5df978d27c95c2
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="nullkeynotallowed-element-assl"></a>Elemento NullKeyNotAllowed (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina il modo in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] motore di elaborazione gestisce un errore di chiave null rilevato durante l'elaborazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ErrorConfiguration>  
   ...  
   <NullKeyNotAllowed>...</NullKeyNotAllowed>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*ReportAndContinue*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Si verificano errori di chiave Null quando in una colonna chiave in cui non sono consentiti valori Null ne viene rilevato uno, che fa sì che il record venga ignorato durante l'elaborazione. Tuttavia, questo errore si verifica solo se il [NullProcessing](../../../analysis-services/scripting/properties/nullprocessing-element-assl.md) elemento per il **DataItem** predecessore del **ErrorConfiguration** elemento padre è impostato su  *Errore*.  
  
 Il valore di questo elemento è limitato a una delle stringhe nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*IgnoreError*|L'errore viene ignorato e l'elaborazione prosegue.|  
|*ReportAndContinue*|L'errore viene segnalato e l'elaborazione prosegue.|  
|*ReportAndStop*|L'errore viene segnalato e l'elaborazione viene arrestata.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **NullKeyNotAllowed** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ErrorOption>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ErrorConfiguration &#40; ASSL &#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)  
  
  
