---
title: Elemento DbTableName (ASSL) | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 65af09fd724f01017ecf372ce6d6134ff9c546e5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34033942"
---
# <a name="dbtablename-element-assl"></a>Elemento DbTableName (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il nome della tabella alla quale l'elemento padre è associato.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<TableBinding> <!-- or TableNotification -->  
   ...  
   <DbTableName>...</DbTableName>  
   ...  
</TableBinding>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|String|  
|Valore predefinito|Nessuno|  
|Cardinalità|1-1: elemento obbligatorio che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[TableBinding](../../../analysis-services/scripting/data-type/tablebinding-data-type-assl.md), [TableNotification](../../../analysis-services/scripting/objects/tablenotification-element-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Gli elementi che corrispondono ai padri di **DbTableName** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.TableBinding> e <xref:Microsoft.AnalysisServices.TableNotification>.  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
