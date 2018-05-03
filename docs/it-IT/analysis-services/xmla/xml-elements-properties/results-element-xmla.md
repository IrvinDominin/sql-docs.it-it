---
title: risultati Element (XMLA) | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- results Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.results
- urn:schemas-microsoft-com:xml-analysis#results
- http://schemas.microsoft.com/analysisservices/2003/engine#results
helpviewer_keywords:
- results element
ms.assetid: 3249a17a-7bfa-4753-b605-8f611ba7ae2b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d59d5be9eaf822b21ea3b5a24e0dacbe9dec56f7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="results-element-xmla"></a>Elemento results (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Contiene una raccolta di [radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md) elementi restituiti dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo usando il [Batch](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md) comando.  
  
 **spazio dei nomi** `http://schemas.microsoft.com/analysisservices/2003/xmla-multipleresults`  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<return>  
   <results>  
      <root>...</root>  
   </results>  
</return>  
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
|Elementi padre|[restituire](../../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
|Elementi figlio|[radice](../../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Se un **Batch** eseguito dal **Execute** (metodo), il **restituire** elemento contiene un singolo **risultati** elemento invece di un singolo **radice** elemento. Il contenuto del **risultati** elemento dipende dalle impostazioni utilizzate per eseguire il **Batch** comando.  
  
 Per non transazionale **Batch** comandi, il **risultati** elemento contiene una **radice** elemento per ogni comando eseguito dal **Batch**comando, se il completamento del comando esito positivo o negativo. Per transazionale **Batch** comandi, il **risultati** elemento contiene una sola classe **radice** elemento che contiene le informazioni sull'errore per il comando non riuscito all'interno di **Batch** comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
