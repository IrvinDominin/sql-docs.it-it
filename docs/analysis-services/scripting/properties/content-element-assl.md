---
title: Contenuto elemento (ASSL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Content Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Content
helpviewer_keywords: Content element
ms.assetid: 221addef-2f88-49c5-b8f5-9eee330497a9
caps.latest.revision: "43"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f9d0cd4dc1e60a59af3b8d3e976eeff888d24aa1
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="content-element-assl"></a>Elemento Content (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Viene descritto il contenuto della colonna di [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<ScalarMiningStructureColumn>  
   ...  
   <Content>...</Content>  
   ...  
</ScalarMiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|None|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Osservazioni  
 Questa enumerazione descrive il tipo di contenuto rappresentato da una colonna della struttura di data mining e può essere estesa nel modo necessario dai provider dell'algoritmo di data mining. Per altre informazioni sui tipi di contenuto, vedere [Tipi di contenuto &#40;Data mining&#41;](../../../analysis-services/data-mining/content-types-data-mining.md).  
  
 I valori inclusi nella tabella seguente sono in genere supportati da tutti i provider dell'algoritmo di data mining.  
  
|valore|Description|  
|-----------|-----------------|  
|*Discreti*|La colonna contiene valori discreti.|  
|*Continua*|I valori per la colonna definiscono un set continuo di dati numerici.|  
|*Discretizzati*|I valori nella colonna rappresentano gruppi, o bucket, di valori derivati da una colonna continua.|  
|*Ordinati*|I valori per la colonna definiscono un set ordinato.|  
|*Ciclico*|I valori per la colonna definiscono un set ordinato ciclico.|  
|*Probabilità*|I valori per la colonna specificano una probabilità per le colonne contenute nel [ClassifiedColumns](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md) dell'elemento padre **ScalarMiningStructureColumn**.|  
|*Variance*|I valori per la colonna specificano una varianza per le colonne contenute nel **ClassifiedColumns** dell'elemento padre **ScalarMiningStructureColumn**.|  
|*StdDev*|I valori per la colonna specificano una deviazione standard per le colonne contenute nel **ClassifiedColumns** dell'elemento padre **ScalarMiningStructureColumn**.|  
|*ProbabilityVariance*|I valori per la colonna specificano una varianza della probabilità per le colonne contenute nel **ClassifiedColumns** dell'elemento padre **ScalarMiningStructureColumn**.|  
|*ProbabilityStdDev*|I valori per la colonna specificano una deviazione standard della probabilità per le colonne contenute nel **ClassifiedColumns** dell'elemento padre **ScalarMiningStructureColumn**.|  
|*Supporto*|I valori per la colonna specificano informazioni di supporto per la colonna contenuta nel **ClassifiedColumns** dell'elemento padre **ScalarMiningStructureColumn**.<br /><br /> Nota: Questa colonna viene fornita come parte dello standard per i provider di algoritmi di data mining di terze parti. Non fare in modo che gli algoritmi forniti da Microsoft usano questa colonna.|  
|*Key*|La colonna è una colonna chiave.<br /><br /> Nota: Questo tipo di contenuto è applicabile solo alle colonne chiave, in cui il **IsKey** è impostato su **True**.|  
  
 Oltre a questi valori standard, inclusi con i provider dell'algoritmo di data mining [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] supportano i valori nella tabella seguente.  
  
|valore|Description|  
|-----------|-----------------|  
|*Sequenza di tasti*|La colonna è una colonna chiave e i valori per la colonna rappresentano una sequenza di eventi.<br /><br /> Nota: Questo tipo di contenuto è applicabile solo alle colonne chiave, in cui il **IsKey** è impostato su **True**.|  
|*Chiave temporale*|La colonna è una colonna chiave e i valori per la colonna rappresentano unità di misura temporali.<br /><br /> Nota: Questo tipo di contenuto è applicabile solo alle colonne chiave, in cui il **IsKey** è impostato su **True**.|  
|*Sequence*|I valori per la colonna rappresentano una sequenza di eventi.|  
|*Time*|I valori per la colonna rappresentano unità di misura temporali.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **contenuto** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento ClassifiedColumns &#40; ASSL &#41;](../../../analysis-services/scripting/collections/classifiedcolumns-element-assl.md)   
 [Proprietà &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
