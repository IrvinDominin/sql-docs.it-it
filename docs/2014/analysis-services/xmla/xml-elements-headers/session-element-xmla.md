---
title: Elemento Session (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2f18754a2ef7d44a2a85bb9da78378bc631ecd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080391"
---
# <a name="session-element-xmla"></a>Elemento Session (XMLA)
  Utilizza l'intestazione SOAP in un messaggio di richiesta SOAP per identificare una sessione esplicita esistente in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 **Namespace** urn:schemas-microsoft-com:xml-analysis  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|None|  
|Elementi figlio|None|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|SessionId|L'attributo `String` obbligatorio che identifica la sessione da utilizzare. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] utilizza un identificatore univoco globale (GUID) per identificare una sessione.|  
  
## <a name="remarks"></a>Note  
 L'elemento dell'intestazione `Session` identifica una sessione esistente avviata in modo esplicito nell'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. L'elemento `Session` fa parte dell'intestazione SOAP nei tipi di messaggi seguenti:  
  
-   Una risposta SOAP che contiene un [BeginSession](session-element-xmla.md) elemento dell'intestazione SOAP.  
  
-   Una richiesta SOAP per identificare la sessione in cui eseguire la [Discover](../xml-elements-methods-discover.md) oppure [Execute](../xml-elements-methods-execute.md) (metodo).  
  
 Un identificatore di sessione non garantisce che una sessione rimanga valida. La sessione specificata nell'elemento `Session` può scadere. Una sessione può ad esempio scadere in caso di timeout oppure se la connessione associata alla sessione viene disconnessa. Se la sessione scade e non è più valida, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] termina la sessione ed esegue il rollback di qualsiasi transazione in corso. Tutti i messaggi SOAP inviati con un identificatore di sessione non più valido hanno esito negativo e viene generato un errore SOAP che indica che non è possibile trovare la sessione specificata.  
  
 Se un elemento `Session` non viene inviato come parte di una richiesta SOAP, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] avvia in modo implicito una sessione per la durata della chiamata al metodo `Discover` o `Execute`, quindi termina la sessione dopo che la chiamata al metodo è stata completata.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento EndSession &#40;XMLA&#41;](endsession-element-xmla.md)   
 [Gestione di connessioni e sessioni &#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [Le intestazioni &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
