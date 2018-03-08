---
title: Elemento Security (XMLA) | Documenti Microsoft
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
apiname: Security Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.security
- urn:schemas-microsoft-com:xml-analysis#Security
- http://schemas.microsoft.com/analysisservices/2003/engine#Security
helpviewer_keywords: Security element
ms.assetid: 0b601f69-d16d-4d10-9361-b8afaa6ed357
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e5dbfc3276c972f37e9ed19223fd7a011a1f99b7
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="security-element-xmla"></a>Elemento Security (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Specifica la modalità di backup o il ripristino delle definizioni di sicurezza, ad esempio ruoli e autorizzazioni, durante un [Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md) o [ripristinare](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md) comando.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Backup> <!-- or Restore -->  
   ...  
   <Security>...</Security>  
   ...  
</Backup>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|*SkipMembership*|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Backup](../../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md), [ripristino](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Remarks  
 Il **sicurezza** elemento determina se le definizioni di sicurezza, ad esempio ruoli e autorizzazioni, definiti in un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] database vengono sottoposti a backup o ripristinato durante, rispettivamente, un **Backup** o **ripristinare** comando. Questo elemento determina inoltre se gli account utente di Windows e i gruppi definiti come membri delle definizioni di sicurezza sono inclusi come parte di **Backup** o **ripristinare** comando.  
  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*SkipMembership*|Include le definizioni di sicurezza ma esclude le informazioni sull'appartenenza durante **Backup** o **ripristinare** comandi.|  
|*CopyAll*|Include le definizioni di sicurezza e informazioni sull'appartenenza durante **Backup** o **ripristinare** comandi.|  
|*IgnoreSecurity*|Esclude le definizioni di sicurezza durante **Backup** o **ripristinare** comandi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento SynchronizeSecurity &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/synchronizesecurity-element-xmla.md)   
 [Proprietà &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
