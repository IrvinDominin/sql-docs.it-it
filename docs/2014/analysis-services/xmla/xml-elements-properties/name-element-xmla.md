---
title: Nome elemento (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Name Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Name
- urn:schemas-microsoft-com:xml-analysis#Name
- microsoft.xml.analysis.name
helpviewer_keywords:
- Name element
ms.assetid: cc1a93df-0b1b-4c38-9183-4f11c26fea6a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 422bd152e82a471ce0f130a26aaa12a56026419a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48127901"
---
# <a name="name-element-xmla"></a>Elemento Name (XMLA)
  Contiene il nome di un membro dell'attributo per l'elemento padre [attributo](attribute-element-xmla.md) oppure [traduzione](translation-element-xmla.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Attribute> <!-- or Translation -->  
   ...  
   <Name>...</Name>  
   ...  
</Attribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|None|  
|Predecessore o padre:|Cardinalità|  
|[Attribute](attribute-element-xmla.md)|1-1: elemento obbligatorio visualizzato una sola volta.|  
|[Traduzione](translation-element-xmla.md)|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Attributo](attribute-element-xmla.md), [traduzione](translation-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Per gli elementi `Attribute`, l'elemento `Name` contiene il nome del membro dell'attributo da inserire o aggiornare durante, rispettivamente, il comando `Insert` o `Update`.  
  
 Per gli elementi `Translation`, l'elemento `Name` contiene la didascalia del membro dell'attributo, nel linguaggio specificato dall'elemento `Language` dell'oggetto `Translation` padre. Se l’elemento `Name` non viene specificato o contiene una stringa vuota, viene utilizzato il valore dell’elemento `Name` per l’elemento `Attribute` che contiene l’elemento `Translation`.  
  
## <a name="see-also"></a>Vedere anche  
 [Inserire l'elemento &#40;XMLA&#41;](../xml-elements-commands/insert-element-xmla.md)   
 [Elemento di linguaggio &#40;XMLA&#41;](language-element-xmla.md)   
 [Aggiornare l'elemento &#40;XMLA&#41;](../xml-elements-commands/update-element-xmla.md)   
 [Proprietà &#40;XMLA&#41;](xml-elements-properties.md)  
  
  
