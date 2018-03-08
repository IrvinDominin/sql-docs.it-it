---
title: Elemento BeginTransaction (XMLA) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BeginTransaction Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#BeginTransaction
- microsoft.xml.analysis.begintransaction
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginTransaction
helpviewer_keywords: BeginTransaction command
ms.assetid: fca122fc-b57c-4ba6-849b-ca8c93cf64e9
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e7ce11d146e54e2ee90c7944bc0ee27eb4f01175
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="begintransaction-element-xmla"></a>Elemento BeginTransaction (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Inizia una transazione nella sessione corrente con un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <BeginTransaction />  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|None|  
|Valore predefinito|None|  
|Cardinalità|0-n: Elemento facoltativo che può ricorrere più di una volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Il **BeginTransaction** comando avvia una transazione attiva nella sessione corrente. Se è già presente una transazione attiva, l'istanza di [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] incrementa il conteggio dei riferimenti delle transazioni per la sessione corrente. Diversamente, l'istanza inizierà una transazione nuova e imposterà il conteggio dei riferimenti per la sessione corrente a 1. Se una transazione attiva viene specificata in modo esplicito utilizzando il **BeginTransaction** comando, tutti i comandi successivi vengono eseguiti all'interno della transazione specificata in modo esplicito.  
  
 Quando la sessione corrente è terminata e il conteggio dei riferimenti per le transazioni è maggiore di zero, viene eseguito il rollback di tutte le transazioni attive.  
  
 Se non ci sono transazioni attive specificate in modo esplicito nella sessione corrente, ogni comando eseguito nella sessione corrente viene eseguito in una transazione implicitamente definita. Il commit della transazione implicita viene eseguito se il comando riesce, o viene eseguito il rollback se il comando si interrompe.  
  
## <a name="see-also"></a>Vedere anche  
 [Annulla l'elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)   
 [Elemento CommitTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)   
 [Elemento RollbackTransaction &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)   
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
