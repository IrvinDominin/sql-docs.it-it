---
title: Type (elemento) (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.type
- http://schemas.microsoft.com/analysisservices/2003/engine#Type
- urn:schemas-microsoft-com:xml-analysis#Type
helpviewer_keywords:
- Type element
ms.assetid: 5d898123-a635-402a-be86-8249d7304fa4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 71f7745a3f3ea39309d871d5fafef737176d3a45
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054391"
---
# <a name="type-element-xmla"></a>Elemento Type (XMLA)
  Determina il tipo di elaborazione da eseguire per il [processo](../xml-elements-commands/process-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Process>  
...  
   <Type>...</Type>  
...  
</Process>  
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
|Elementi padre|[Process](../xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle opzioni disponibili per gli oggetti in un'istanza di elaborazione [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [l'elaborazione di oggetti modello multidimensionale](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Il valore dell'elemento `Type` è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*ProcessFull*|Elimina tutti i dati dall'oggetto interessato, quindi elabora tale oggetto.|  
|*ProcessAdd*|Aggiunge nuovi dati all'oggetto interessato.|  
|*ProcessUpdate*|Aggiorna i dati nell'oggetto interessato.|  
|*ProcessIndexes*|Crea o ricompila indici e aggregazioni nell'oggetto interessato.|  
|*ProcessScriptCache*|Se il cubo viene elaborato, il server ricompila la cache script MDX. In caso contrario, viene generato un errore.<br /><br /> **Nota** si applica solo al cubo.|  
|*ProcessData*|Elabora i dati solo nell'oggetto interessato.|  
|*ProcessDefault*|Rileva lo stato dell'oggetto interessato, quindi esegue l'opzione di elaborazione appropriata sull'oggetto interessato per ottimizzarlo completamente e ripristinare uno stato dell'oggetto completamente elaborato.|  
|*ProcessClear*|Elimina i dati dall'oggetto interessato e da tutti gli oggetti correlati.|  
|*ProcessStructure*|Elabora la struttura solo dell'oggetto interessato.|  
|*ProcessClearStructureOnly*|Cancella i dati solo dall'oggetto interessato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
