---
title: CopyRecordOptionsEnum uguale al | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CopyRecordOptionsEnum
helpviewer_keywords:
- CopyRecordOptionsEnum enumeration [ADO]
ms.assetid: 2fa4eec5-d50b-4fd3-8ae7-40af441ba12b
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 21f9d27d8e606119ab3dcbbf6b67fe30f4f6bc3f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="copyrecordoptionsenum"></a>CopyRecordOptionsEnum
Specifica il comportamento del [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) metodo.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adCopyAllowEmulation**|4|Indica che il *origine* provider tenta di simulare la copia mediante lo scaricamento e se questo metodo ha esito negativo a causa di operazioni di caricamento *destinazione*si trova su un server diverso oppure che viene gestita da un'altra provider di *origine*. Si noti che diverse funzionalità del provider possono compromettere le prestazioni o perdita di dati.|  
|**adCopyNonRecursive**|2|Copia la directory corrente, ma nessuna delle relative sottodirectory, nella destinazione. L'operazione di copia non è ricorsiva.|  
|**adCopyOverWrite**|1|Sovrascrive il file o la directory se il *destinazione* punta a un file o directory esistente.|  
|**adCopyUnspecified**|-1|Valore predefinito. Esegue l'operazione di copia predefinito: l'operazione non riesce se il file di destinazione o la directory esiste già e le copie di operazione in modo ricorsivo.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo CopyRecord (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)
