---
title: Bloccare l'elemento (XMLA) | Documenti Microsoft
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
apiname: Lock Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Lock
- microsoft.xml.analysis.lock
- http://schemas.microsoft.com/analysisservices/2003/engine#Lock
helpviewer_keywords: Lock command
ms.assetid: a819e805-4793-43bb-8af3-16a19f8bdab3
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 98e5087dc10ae495dec711c35fa807cb9fd68e02
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="lock-element-xmla"></a>Elemento Lock (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Blocca un oggetto specificato in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Lock>  
      <ID>...</ID>  
      <Object>...</Object>  
      <Mode>...</Mode>  
   </Lock>  
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
|Elementi figlio|[ID](../../../analysis-services/xmla/xml-elements-properties/id-element-xmla.md), [modalità](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md), [oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)|  
  
## <a name="remarks"></a>Remarks  
 Il **blocco** comando Blocca un oggetto, per utilizzo condiviso o esclusivo, all'interno del contesto della transazione attualmente attiva. Solo gli amministratori di database o gli amministratori del server possono eseguire in modo esplicito un **blocco** comando. Un blocco su un oggetto impedisce alle transazioni di eseguire il commit finché non viene rimosso. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supporta due tipi di blocchi, blocchi condivisi e blocchi esclusivi. Per ulteriori informazioni sui tipi di blocco supportati da [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], vedere [elemento Mode &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-properties/mode-element-xmla.md).  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] consente solo che i database vengano bloccati. Il **oggetto** elemento deve contenere un riferimento a un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database. Se il **oggetto** elemento non è specificato o se il **oggetto** elemento fa riferimento a un oggetto diverso da un database, si verifica un errore.  
  
 Altri comandi eseguono implicitamente un **blocco** comando un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database. Qualsiasi operazione che legge dati o metadati da un database, ad esempio **Discover** metodo o un **Execute** metodo in esecuzione un **istruzione** comando, applica implicitamente un oggetto condiviso blocco del database. Qualsiasi transazione che esegue il commit delle modifiche nei dati o metadati per un oggetto su un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database, ad esempio un **Execute** metodo in esecuzione un **Alter** comando, applica implicitamente un blocco esclusivo sul database.  
  
 Tutti i blocchi sono contenuti nel contesto della transazione corrente. Quando viene eseguito il commit oppure il rollback della transazione corrente, tutti i blocchi definiti all'interno della transazione vengono rilasciati automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Sblocca elemento &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)   
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
