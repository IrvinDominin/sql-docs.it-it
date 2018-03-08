---
title: Evento EndOfRecordset (ADO) | Documenti Microsoft
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
- EndOfRecordset
- Recordset::EndOfRecordset
helpviewer_keywords:
- EndOfRecordset event [ADO]
ms.assetid: 475de5e2-f634-4954-9edf-0027a6ba38d6
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79d37ae42a9c9e607ba4d8dba8917fccd7f20c42
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="endofrecordset-event-ado"></a>Evento EndOfRecordset (ADO)
Il **EndOfRecordset** eventi viene chiamato quando viene eseguito un tentativo di spostare in una riga oltre la fine del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
EndOfRecordset fMoreData, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parametri  
 *fMoreData*  
 Oggetto **VARIANT_BOOL** valore che, se impostato su VARIANT_TRUE, indica più righe sono stati aggiunti per il **Recordset**.  
  
 *adStatus*  
 Un [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) valore di stato.  
  
 Quando **EndOfRecordset** viene chiamato, questo parametro è impostato su **adStatusOK** se l'operazione che ha causato l'evento ha esito positivo. È impostato su **adStatusCantDeny** se questo evento non è possibile richiedere l'annullamento dell'operazione che ha causato l'evento.  
  
 Prima di **EndOfRecordset** restituisce un valore, impostare questo parametro su **adStatusUnwantedEvent** per impedire notifiche successive.  
  
 *pRecordset*  
 Oggetto **Recordset** oggetto. Il **Recordset** per cui si è verificato l'evento.  
  
## <a name="remarks"></a>Osservazioni  
 Un **EndOfRecordset** evento può verificarsi se il [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) operazione ha esito negativo.  
  
 Questo gestore eventi viene chiamato quando viene effettuato un tentativo di spostare oltre la fine del **Recordset** oggetto, ad esempio a seguito della chiamata **MoveNext**. In questo caso, tuttavia, è possibile recuperare altri record da un database e li aggiunge alla fine del **Recordset**. In questo caso, impostare *fMoreData* su VARIANT_TRUE, quindi restituiscono da **EndOfRecordset**. Chiamare quindi **MoveNext** per accedere ai record appena recuperati.  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di modello di eventi ADO (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [Riepilogo dei gestori eventi ADO](../../../ado/guide/data/ado-event-handler-summary.md)
