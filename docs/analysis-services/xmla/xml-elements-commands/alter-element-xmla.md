---
title: Elemento ALTER (XMLA) | Documenti Microsoft
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
apiname: Alter Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Alter
- microsoft.xml.analysis.alter
- urn:schemas-microsoft-com:xml-analysis#Alter
helpviewer_keywords: Alter command
ms.assetid: 84e58385-c9ba-48fa-a867-94d35b777a56
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d6d234801cb298f15982bfc4ac1d75a493dd6aa8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="alter-element-xmla"></a>Elemento Alter (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Contiene gli elementi di Analysis Services Scripting Language (ASSL) utilizzati dal [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md) metodo per modificare gli oggetti in un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Alter Scope="enum" AllowCreate="boolean" ObjectExpansion="enum">  
      <Object>...</Object>  
      <ObjectDefinition>...</ObjectDefinition>  
   </Alter>  
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
|Elementi figlio|[Oggetto](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [ObjectDefinition](../../../analysis-services/xmla/xml-elements-properties/objectdefinition-element-xmla.md)|  
  
## <a name="attributes"></a>Attributi  
  
|attribute|Description|  
|---------------|-----------------|  
|AllowCreate|(Facoltativo **booleano** attributo) indica se gli oggetti definiti nel **Alter** comando deve essere creato se non esiste già.<br /><br /> Se impostato su true, gli oggetti definiti nel **ObjectDefinition** elemento vengono create nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza se non esiste già. In altre parole, il **Alter** comando viene considerato come un **crea** se gli oggetti non esistono già nell'istanza di comando.<br /><br /> Se questo attributo viene omesso o impostato su **false**, si verifica un errore se gli oggetti non esistono già.|  
|ObjectExpansion|(Facoltativo **Enum** attributo) definisce l'ambito della modifica deve essere eseguita dal **Execute** metodo.<br /><br /> Se impostato su *ObjectProperties*, **ObjectDefinition** elemento deve contenere solo la definizione completa dell'oggetto principale da modificare, inclusi gli oggetti secondari subordinati. Gli oggetti principali subordinati dell'oggetto da modificare non vengono modificati.<br /><br /> Nota: Quando si utilizza il *ObjectProperties* impostazione con il [ClrAssembly](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md) tipo di dati, il [dati](../../../analysis-services/scripting/objects/data-element-assl.md) elemento dell'oggetto associato [ClrAssemblyFile](../../../analysis-services/scripting/data-type/clrassemblyfile-data-type-assl.md) non è necessario specificare i tipi di dati. Se non specificato, il **ClrAssembly** utilizza i file esistenti.<br /><br /> Se impostato su *ExpandFull*, **ObjectDefinition** elemento deve contenere non solo la definizione dell'oggetto da modificare, ma anche le definizioni di tutti gli oggetti principali discendenti dell'oggetto per essere modificato.<br /><br /> Nota: Il *ExpandFull* impostazione non può essere usata con il [Server](../../../analysis-services/scripting/objects/server-element-assl.md) elemento.|  
|Ambito|(Facoltativo **Enum** attributo) definisce la durata degli oggetti definiti nel **ObjectDefinition** elemento.<br /><br /> Se impostato su *sessione*, gli oggetti definiti nel **ObjectDefinition** l'elemento esiste solo per la durata della sessione XMLA.<br /><br /> Nota: Quando si utilizza il *sessione* impostazione, il **ObjectDefinition** elemento può contenere solo [dimensione](../../../analysis-services/scripting/objects/dimension-element-assl.md), [cubo](../../../analysis-services/scripting/objects/cube-element-assl.md), o [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md) elementi ASSL.<br /><br /> Se questo attributo viene omesso, gli oggetti definiti nel **ObjectDefinition** elemento vengono rese persistenti nel [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.|  
  
## <a name="remarks"></a>Remarks  
 Ogni **Alter** comando modifica la definizione di un oggetto principale sotto l'oggetto padre specificato da di [ParentObject](../../../analysis-services/xmla/xml-elements-properties/parentobject-element-xmla.md) elemento.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
