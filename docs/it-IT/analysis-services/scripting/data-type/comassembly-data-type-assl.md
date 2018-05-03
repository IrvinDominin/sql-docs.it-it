---
title: Il tipo di dati ComAssembly (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ComAssembly Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ComAssembly
helpviewer_keywords:
- ComAssembly data type
ms.assetid: 23c0f4b3-b6ac-4ec8-9254-74d2f84f5244
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4f5a8bfcdbd60d71db4928d345d0d8ae62de2a2a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="comassembly-data-type-assl"></a>Tipo di dati ComAssembly (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Definisce un tipo di dati derivato che rappresenta una libreria COM associata a un elemento [Server](../../../analysis-services/scripting/objects/server-element-assl.md) o [Database](../../../analysis-services/scripting/objects/database-element-assl.md) .  
  
> [!IMPORTANT]  
>  Gli assembly COM potrebbero comportare un rischio per la sicurezza. A causa di tale rischio e di altre considerazioni, gli assembly COM sono stati deprecati in [!INCLUDE[ssASversion10](../../../includes/ssasversion10-md.md)] e potrebbero non essere supportati nelle versioni future.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ComAssembly>  
      <!-- The following elements extend Assembly -->  
   <Source>...</Source>  
</ComAssembly>  
```  
  
## <a name="data-type-characteristics"></a>Caratteristiche tipo di dati  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipi di dati di base|[Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md)|  
|Tipi di dati derivati|Nessuno|  
  
## <a name="data-type-relationships"></a>Relazioni di tipo di dati  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elementi padre|Nessuno|  
|Elementi figlio|[Origine](../../../analysis-services/scripting/properties/source-element-comassembly-assl.md)|  
|Elementi derivati|Vedere [Assembly](../../../analysis-services/scripting/objects/assembly-element-assl.md) (raccolta[Assemblies](../../../analysis-services/scripting/collections/assemblies-element-assl.md) di [Database](../../../analysis-services/scripting/objects/database-element-assl.md) o [Server](../../../analysis-services/scripting/objects/server-element-assl.md))|  
  
## <a name="remarks"></a>Osservazioni  
 Il **ComAssembly** elemento contiene un riferimento (il nome file completo o l'identificatore programmatico) a una libreria COM associata a un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] o con una versione specifica database in un'istanza di [!INCLUDE[ssAS](../../../includes/ssas-md.md)].  
  
 L'elemento corrispondente nel modello a oggetti oggetti AMO (Analysis Management) è <xref:Microsoft.AnalysisServices.ComAssembly>.  
  
## <a name="see-also"></a>Vedere anche  
 [Tipo di dati ClrAssembly &#40;ASSL&#41;](../../../analysis-services/scripting/data-type/clrassembly-data-type-assl.md)   
 [Analysis Services Scripting Language tipi di dati XML & #40; ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
