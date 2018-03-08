---
title: Elemento Cancel (XMLA) | Documenti Microsoft
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
apiname: Cancel Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.cancel
- http://schemas.microsoft.com/analysisservices/2003/engine#Cancel
- urn:schemas-microsoft-com:xml-analysis#Cancel
helpviewer_keywords: Cancel command
ms.assetid: de4062c1-7434-44dc-9f01-29fcf78963bd
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c50ff4e923e046a157c06ccb139e1b8645d1e9aa
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="cancel-element-xmla"></a>Elemento Cancel (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]Annulla un comando attualmente in esecuzione un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<Command>  
   <Cancel>  
      <ConnectionID>...</ConnectionID>  
      <SessionID>...</SessionID>  
      <SPID>...</SPID>  
      <CancelAssociated>...</CancelAssociated>  
   </Cancel>  
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
|Elementi figlio|[CancelAssociated](../../../analysis-services/xmla/xml-elements-properties/cancelassociated-element-xmla.md), [ConnectionID](../../../analysis-services/xmla/xml-elements-properties/connectionid-element-xmla.md), [SessionID](../../../analysis-services/xmla/xml-elements-properties/sessionid-element-xmla.md), [SPID](../../../analysis-services/xmla/xml-elements-properties/spid-element-xmla.md)|  
  
## <a name="remarks"></a>Osservazioni  
 Il **Annulla** comando Annulla comandi all'interno del contesto di una sessione attualmente in esecuzione. Se l'applicazione client non ha richiesto una sessione, un comando non può essere annullato.  
  
 Se il **Annulla** comando viene eseguito durante l'esecuzione di un **Batch** l'intero comando **Batch** viene annullato. Se il **Batch** comando è transazionale, tutti i comandi contenuti di **Batch** comando viene eseguito il rollback. Se il **Batch** comando non è transazionale, solo i comandi contenuti dal **Batch** comandi che erano in esecuzione al momento il **Annulla** comando è stato eseguito sono eseguire il rollback. I comandi in un transazionale **Batch** che era già stato eseguito potrebbe non essere rollback del comando.  
  
 In genere, il **Annulla** comando viene utilizzato per annullare l'esecuzione di comandi nella sessione attualmente attiva. In questo caso, nessuno degli elementi figlio per il **Annulla** comando deve essere specificato. Il **Annulla** comando può essere utilizzato anche dagli amministratori per annullare comandi eseguiti in connessioni o sessioni diverse dalla sessione attualmente attiva. Membri di un ruolo che ha autorizzazioni di amministratore per un database specificato possono annullare comandi per connessioni e sessioni applicabili a quel database, mentre gli amministratori del server possono annullare comandi per connessioni e sessioni per un'istanza di Analysis Services specificata.  
  
 Per recuperare informazioni sulle connessioni correnti e le sessioni per un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] istanza, il **Discover** metodo può essere eseguito per richiedere, rispettivamente, i set di righe dello schema DISCOVER_CONNECTIONS e di DISCOVER_SESSIONS. Membri di un ruolo che ha autorizzazioni di amministratore per un database specificato possono restituire sessioni solo per un database specificato, riportando tale database nella colonna restrizione SESSION_CURRENT_DATABASE per il set di righe dello schema di DISCOVER_SESSIONS. Per ulteriori informazioni sul **Discover** metodo, vedere [metodo individuare &#40; XMLA &#41; ](../../../analysis-services/xmla/xml-elements-methods-discover.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento batch &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Comandi &#40; XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
