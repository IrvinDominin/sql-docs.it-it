---
title: Elemento HoldoutSeed | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
f1_keywords:
- HoldoutSeed
helpviewer_keywords:
- HoldoutSeed element
ms.assetid: 6b608bb3-c075-4744-9722-f5fb9fa1cc7e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b97d88ee83d92d22f72db13d20ce37bb6ea9da08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48097598"
---
# <a name="holdoutseed-element"></a>Elemento HoldoutSeed
  Specifica il valore di inizializzazione per una partizione di dati di controllo ripetibile che contiene il set di test di una [MiningStructure](../objects/miningstructure-element-assl.md) elemento. Questo valore di inizializzazione assicura che il contenuto del modello rimanga lo stesso durante la rielaborazione. Se non specificato o impostato su 0, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea un valore di inizializzazione utilizzando un algoritmo di hash sul nome della struttura di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructure>  
   ...  
   <ddl100_100:HoldoutSeed>...</ddl100_100:HoldoutSeed>  
   ...  
</MiningStructure>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Description|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Long|  
|Valore predefinito|0|  
|Cardinalità|0-1: elemento facoltativo che può verificarsi una volta e una volta soltanto.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[Elemento MiningStructure](../objects/miningstructure-element-assl.md)|  
|Elementi figlio|None|  
  
## <a name="remarks"></a>Note  
 Quando si crea per la prima volta una struttura di data mining, l'ID e il nome sono gli stessi. Tuttavia, è possibile modificare il nome della struttura di data mining. Pertanto, per garantire la ripetibilità della partizione, non ci si deve basare sul valore di inizializzazione creato dal nome, ma è necessario impostare espressamente un valore di inizializzazione.  
  
 Inoltre, quando si crea una copia di una struttura di data mining utilizzando l'istruzione `EXPORT`, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] manterrà il nome nella nuova struttura di data mining, ma genererà automaticamente un nuovo ID. Pertanto, è possibile avere due strutture di data mining che condividono lo stesso nome, ma hanno ID diversi. Due strutture di data mining qualsiasi con lo stesso nome avranno il medesimo valore di inizializzazione. Tuttavia, dal momento che il partizionamento dei dati dipende anche dai dati di origine, il contenuto effettivo delle partizioni di ciascuna struttura potrebbe essere diverso.  
  
 Le nuove proprietà `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed`, o `HoldoutActualSize` sono disponibili solo in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] e versioni successive. È pertanto necessario utilizzare per queste proprietà un prefisso con il nuovo spazio dei nomi, come illustrato nella descrizione della sintassi. In caso contrario, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] viene restituito un errore.  
  
 **Nota** nelle [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] non supportava l'utilizzo di partizioni di controllo su una struttura di data mining. Pertanto, le istruzioni Scripting Linguage (ASSL) [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] contenenti i parametri di controllo `HoldoutMaxCases`, `HoldoutMaxPercent`, `HoldoutSeed` o `HoldoutActualSize` non possono essere utilizzate in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si utilizza uno di questi parametri di controllo in un'istruzione ASSL in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] restituirà un errore.  
  
 L'elemento che corrisponde al padre di `HoldoutSeed` nell'oggetto gli oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructure>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà &#40;ASSL&#41;](properties-assl.md)   
 [Elemento HoldoutActualSize](holdoutactualsize-element.md)   
 [Elemento HoldoutMaxPercent](holdoutmaxpercent-element.md)   
 [Elemento HoldoutMaxCases](holdoutmaxcases-element.md)  
  
  
