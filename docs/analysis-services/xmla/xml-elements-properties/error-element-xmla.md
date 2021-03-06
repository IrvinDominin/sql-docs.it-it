---
title: Elemento Error (XMLA) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f223bff2dced01c2b3f954ca14242b1a35c93813
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036649"
---
# <a name="error-element-xmla"></a>Elemento Error (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene informazioni sull'errore restituita da un'istanza di Analysis Services.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Message>  
   <Error   
      ErrorCode="unsignedint"   
      Severity="string"   
      Description="string"  
      Source="string"  
      HelpFile="string"  
   />  
</Message>  
<!-- or -->  
<Cell><!-- or row -->  
   <!-- A child element -->  
      <Error xmlns="urn:schemas-microsoft-com:xml-analysis:exception"  
         < ErrorCode>...</ErrorCode>  
         < Description>...</Description>  
         < Source>...</Source>  
         < HelpFile>...</HelpFile>  
      </Error>  
   <!-- /A child element -- >  
</Cell>  
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
|Elementi padre|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|  
|Elementi figlio|Vedere la tabella riportata di seguito.|  
  
|Ancestor|Elementi figlio|  
|--------------|--------------------|  
|[Message](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|None|  
|[Cella](../../../analysis-services/xmla/xml-elements-properties/cell-element-mddataset-xmla.md), [riga](../../../analysis-services/xmla/xml-elements-properties/message-element-xmla.md)|[Descrizione](../../../analysis-services/xmla/xml-elements-properties/description-element-xmla.md), [ErrorCode](../../../analysis-services/xmla/xml-elements-properties/errorcode-element-xmla.md), [HelpFile](../../../analysis-services/xmla/xml-elements-properties/helpfile-element-xmla.md), [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-error-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|ErrorCode|Obbligatorio **UnsignedInt** attributo (solo quando **messaggio** corrisponde all'elemento padre.) Contiene il codice restituito numerico dell'errore.|  
|Severity|Facoltativo **stringa** attributo (solo quando **messaggio** corrisponde all'elemento padre.) Contiene la gravità dell’errore.|  
|Description|Facoltativo **stringa** attributo (solo quando **messaggio** corrisponde all'elemento padre.) Contiene il testo descrittivo dell'errore.|  
|Origine|Facoltativo **stringa** attributo (solo quando **messaggio** corrisponde all'elemento padre.) Contiene il nome del componente che ha generato l’errore.|  
|FileGuida|Facoltativo **stringa** attributo (solo quando **messaggio** corrisponde all'elemento padre.) Contiene il percorso o URL al file Guida o all’argomento che descrive l'errore.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche
 [Elemento warning &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/warning-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
