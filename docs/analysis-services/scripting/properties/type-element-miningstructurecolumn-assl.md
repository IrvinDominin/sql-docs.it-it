---
title: Tipo di elemento (MiningStructureColumn) (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Type Element (MiningStructureColumn)
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ec79db597b6d7b9079e556628f0856e5257cf5d2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="type-element-miningstructurecolumn-assl"></a>Elemento Type (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il tipo di [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String (enumerazione)|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio visualizzato una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di questo elemento è limitato a una delle stringhe elencate nella tabella seguente.  
  
|Valore|Description|  
|-----------|-----------------|  
|*Long*|Intero con segno a 64 bit. Questo tipo di dati esegue il mapping al **Int64** tipo di dati di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] tipo di .NET Framework e i dati di DBTYPE_I8 in OLE DB.|  
|*Boolean*|Valore booleano. Esegue il mapping di questo tipo di dati per il **booleano** tipo di dati .NET Framework e il tipo di dati DBTYPE_BOOL in OLE DB.|  
|*Text*|Flusso con terminazione Null di caratteri Unicode. Esegue il mapping di questo tipo di dati per il **stringa** tipo di dati .NET Framework e il tipo di dati DBTYPE_WSTR in OLE DB.|  
|*Double*|Numero a precisione doppia in virgola mobile compreso tra -1.79E +308 e 1.79E +308. Esegue il mapping di questo tipo di dati per il **doppie** tipo di dati .NET Framework e il tipo di dati DBTYPE_R8 in OLE DB.|  
|*Data*|Tipo di dati data, registrato come numero a virgola mobile e doppia precisione. La parte intera è il numero di giorni a partire dal 30 dicembre 1899 mentre la parte frazionaria rappresenta una frazione del giorno. Esegue il mapping di questo tipo di dati per il **DateTime** tipo di dati .NET Framework e il tipo di dati DBTYPE_DATE in OLE DB.|  
|*Tabella*|Tabella nidificata. Questo tipo di dati esegue il mapping al tipo di dati di DBTYPE_HCHAPTER in OLE DB.<br /><br /> Nota: Le colonne della tabella in .NET Framework non è un tipo di dati intrinseco equivalente, ma sono invece supportate dal **DataReader** classe.|  
  
 L'enumerazione che corrisponde ai valori consentiti per **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 L'elemento che corrisponde all'elemento padre **tipo** nell'oggetto oggetti AMO (Analysis Management) è modello <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
