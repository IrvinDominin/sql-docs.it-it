---
title: Elemento WritebackTableCreation (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- WritebackTableCreation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#WritebackTableCreation
- microsoft.xml.analysis.writebacktablecreation
- http://schemas.microsoft.com/analysisservices/2003/engine#WritebackTableCreation
helpviewer_keywords:
- WritebackTableCreation element
ms.assetid: e9579d63-e28c-4d4e-9f4a-21c5da24c276
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 454ee8dc998fbbebc5a867a29a289bce4ee818be
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48131491"
---
# <a name="writebacktablecreation-element-xmla"></a>Elemento WritebackTableCreation (XMLA)
  Determina se una tabella writeback viene creata durante la [processo](../xml-elements-commands/process-element-xmla.md) operazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Process>  
...  
   <WritebackTableCreation>...</WritebackTableCreation>  
...  
</Process>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Process](../xml-elements-commands/process-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per altre informazioni sulle opzioni di elaborazione disponibili per gli oggetti in un'istanza di Analysis Services, vedere [elaborazione di oggetti modello multidimensionale](../../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
 Il valore dell'elemento `WritebackTableCreation` è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Creare*|Crea una nuova tabella writeback nel caso questa non esista Se esiste già una tabella writeback, si verifica un errore.|  
|*CreateAlways*|Creare una tabella writeback nuova, sovrascrivendo qualsiasi tabella writeback esistente.|  
|*UseExisting*|Utilizzare la tabella writeback esistente, se esiste. Se non esiste, si verifica un errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
