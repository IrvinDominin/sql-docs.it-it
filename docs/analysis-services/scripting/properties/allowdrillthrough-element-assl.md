---
title: Elemento AllowDrillThrough (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: AllowDrillThrough Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: AllowDrillThrough
helpviewer_keywords: AllowDrillThrough element
ms.assetid: 53c9e4a3-a376-447d-a13f-80d845cc9789
caps.latest.revision: "51"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3863648b3c8978fa8ac3b8ba981c6fa634c30ef0
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="allowdrillthrough-element-assl"></a>Elemento AllowDrillThrough (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Determina se il drill-through è permesso sull'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningModel> <!-- or MiningModelPermission -->  
<!-- or MiningStructurePermission -->   ...  
   <AllowDrillThrough>...</AllowDrillThrough>  
   ...  
</MiningModel>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Boolean|  
|Valore predefinito|**False**|  
|Cardinalità|0-1: Elemento facoltativo che può verificarsi una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|[Elemento MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md), [MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md), [MiningStructurePermission](../../../analysis-services/scripting/objects/miningstructurepermission-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **AllowDrillThrough** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.MiningModel>, <xref:Microsoft.AnalysisServices.MiningModelPermission>, e <xref:Microsoft.AnalysisServices.MiningStructurePermission>.  
  
## <a name="drillthrough-on-mining-structures"></a>Drill-through sulle strutture di data mining  
 In [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], è possibile definire **AllowDrillthrough** le autorizzazioni per strutture di data mining, nonché modelli di data mining. Quando si assegna questa autorizzazione a un ruolo, qualsiasi membro del ruolo può eseguire query sul modello di data mining e restituire le colonne della struttura non incluse nel modello. Si supponga di creare un modello che utilizza solo le colonne relative al codice, al reddito e agli acquisti del cliente. Se si abilita il drill-through sul modello, gli utenti possono restituire le informazioni nelle altre colonne della struttura di data mining, ad esempio nomi o messaggi di posta elettronica del cliente.  
  
 Pertanto, per proteggere i dati sensibili, è necessario prestare attenzione nell'aggiunta di colonne alla struttura di data mining. Concedere inoltre l'autorizzazione **AllowDrillthrough** su una struttura solo quando necessario.  
  
 Per eseguire il drill-through nelle colonne della struttura, utilizzare una query con uno dei formati seguenti:  
  
 `SELECT * FROM <structure>.CASES`  
  
 o Gestione configurazione  
  
 `SELECT StructureColumn('<structure-column-name>') FROM <model>.CASES`  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento Role &#40; ASSL &#41;](../../../analysis-services/scripting/objects/role-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
