---
title: Elemento ConnectionString (XMLA) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c286aa928195181d5d1b344f71b648510ccceda1
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34575843"
---
# <a name="connectionstring-element-xmla"></a>Elemento ConnectionString (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una stringa di connessione utilizzata dall'elemento padre [percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md) o [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Location> <!-- or Source -->  
   ...  
   <ConnectionString>...</ConnectionString>  
   ...  
</Location>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Cardinalità|Vedere la tabella riportata di seguito.|  
  
|Predecessore o padre|Cardinalità|  
|------------------------|-----------------|  
|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|[Origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Percorso](../../../analysis-services/xmla/xml-elements-properties/location-element-xmla.md), [origine](../../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Per **percorso** elementi, il **ConnectionString** elemento contiene la stringa di connessione utilizzata dal **ripristinare** o **Sincronizza** comando per aggiornare un'origine dati locale o connettersi a un'istanza remota.  
  
 Per **origine** elementi, il **ConnectionString** elemento contiene la stringa di connessione utilizzata dal **Sincronizza** comando per connettersi all'istanza di origine.  
  
 Per ulteriori informazioni sul backup e ripristino degli oggetti, vedere [backup, ripristino e sincronizzazione di database &#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
## <a name="see-also"></a>Vedere anche
 [Elemento Restore &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Elemento Synchronize &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
