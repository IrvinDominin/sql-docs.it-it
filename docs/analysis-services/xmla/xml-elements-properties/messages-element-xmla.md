---
title: I messaggi di elemento (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- Messages Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Messages
- microsoft.xml.analysis.messages
- urn:schemas-microsoft-com:xml-analysis#Messages
helpviewer_keywords:
- Messages element
ms.assetid: 719d15ff-f18b-4c56-80ba-a9114c0b7d8a
caps.latest.revision: 11
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b45be9ceeaf0feb601ea873b5e62f3a34e99ae5a
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="messages-element-xmla"></a>Elemento Messages (XMLA)
  Contiene una raccolta di [messaggio](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md) gli elementi restituiti da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] da un [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) o [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) (metodo) chiamata.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Resultset>  
   <Messages>  
      <Message>  
   </Messages>  
</Resultset>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Nessuno|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Set di risultati](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|  
|Elementi figlio|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Questo elemento viene utilizzato nei casi in cui una chiamata al metodo **Discover** o un singolo comando XMLA all'interno di una chiamata al metodo **Execute** viene completato correttamente, ma con errori o avvisi. In questi casi, un **messaggi** elemento viene aggiunto al [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elemento dopo tutti gli altri elementi, che a sua volta contiene uno o più **messaggio** elementi. Ogni **messaggio** elemento rappresenta un singolo messaggio, un errore o avviso, restituito dal [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  