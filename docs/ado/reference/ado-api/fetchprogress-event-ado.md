---
title: Evento FetchProgress (ADO) | Documenti Microsoft
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
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3bd5284c35e51a8cc711fe7612d1176241c00ac7
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="fetchprogress-event-ado"></a>Evento FetchProgress (ADO)
Il **FetchProgress**eventi viene chiamato periodicamente durante un'operazione asincrona di lunga durata per segnalare il numero di righe attualmente recuperato nel [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *Stato*  
 Oggetto **lungo** valore che indica il numero di record che attualmente sono state recuperate dall'operazione di recupero.  
  
 *MaxProgress*  
 Oggetto **lungo** previsto valore che indica il numero massimo di record da recuperare.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto che rappresenta l'oggetto per il quale vengono recuperati i record.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si utilizza **FetchProgress** con un elemento figlio **Recordset**, tenere presente che il *lo stato di avanzamento* e *MaxProgress* derivano i valori dei parametri sottostante [servizio cursore](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) set di righe. I valori restituiti rappresentano il numero totale di record nel set di righe sottostanti, non solo il numero di record nel capitolo corrente.  
  
> [!NOTE]
>  Per utilizzare **FetchProgress** con Microsoft Visual Basic, Visual Basic 6.0 o versione successiva è obbligatorio.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
