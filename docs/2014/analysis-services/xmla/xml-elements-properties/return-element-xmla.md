---
title: Elemento Return (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- return Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.return
- http://schemas.microsoft.com/analysisservices/2003/engine#return
- urn:schemas-microsoft-com:xml-analysis#return
helpviewer_keywords:
- return element
ms.assetid: 3cfe8b74-fec3-4987-a74a-5f731444e024
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9484532d235d923dae8b28ab42bd7e4af4523346
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217531"
---
# <a name="return-element-xmla"></a>Elemento return (XMLA)
  Contiene informazioni restituite da una [DiscoverResponse](../xml-elements-objects-discoverresponse.md) elemento in risposta a un [Discover](../xml-elements-methods-discover.md) chiamata al metodo o un [ExecuteResponse](../xml-elements-objects-executeresponse.md) elemento in risposta a un [Execute](../xml-elements-methods-execute.md) chiamata al metodo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DiscoverResponse> <!-- or ExecuteResponse -->  
   <return>  
      <root>...</root>  
      <!-- or -->  
      <results>...</results> <!-- ExecuteResponse only -->  
   </return>  
</DiscoverResponse>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[DiscoverResponse](../xml-elements-objects-discoverresponse.md), [ExecuteResponse](../xml-elements-objects-executeresponse.md)|  
|Predecessore:[DiscoverResponse](../xml-elements-objects-discoverresponse.md)|Figlio: <br />                        [root](root-element-xmla.md)|  
|Predecessore: <br />                        [ExecuteResponse](../xml-elements-objects-executeresponse.md)|Figlio: [radice](root-element-xmla.md) o [risultati](results-element-xmla.md)|  
  
## <a name="remarks"></a>Note  
 L'elemento `return` contiene i dati restituiti dai metodi `Discover` ed `Execute`. L'elemento `return` contiene in genere un singolo elemento `root`, che contiene a sua volta i dati restituiti da una chiamata al metodo `Discover` o `Execute` o un'eccezione XMLA (XML for Analysis) restituita da una chiamata al metodo non riuscita. Se il metodo `Execute` contiene un comando `Batch` che esegue più operazioni, l'elemento `return` contiene l'elemento `results` che, a sua volta, contiene un elemento `root` per ogni comando eseguito correttamente o non correttamente dal comando `Batch`.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
