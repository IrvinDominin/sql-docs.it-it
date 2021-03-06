---
title: risultati Element (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7fc64d6b31f1b05d8bf5b4d1c80d75dff0583e86
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968663"
---
# <a name="results-element-xmla"></a>Elemento results (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) gli elementi restituiti dai [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo utilizzando il [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando.  
  
 **Namespace** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche di elementi  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Elementi-relazioni  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[restituire](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Elementi figlio|[root](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 Se un **Batch** eseguito dal **Execute** metodo, il **restituire** elemento contiene un singolo **risultati** elemento invece di un singolo **radice** elemento. Il contenuto del **risultati** elemento dipende dalle impostazioni utilizzate per eseguire il **Batch** comando.  
  
 Per non transazionale **Batch** comandi, il **risultati** elemento contiene uno **radice** (elemento) per ogni comando eseguito dal **Batch**comando, se il comando viene completato con esito positivo o negativo. Per transazionali **Batch** comandi, il **risultati** elemento contiene una sola **radice** elemento che contiene le informazioni sull'errore per il comando non riuscito all'interno di **Batch** comando.  
  
## <a name="see-also"></a>Vedere anche
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
