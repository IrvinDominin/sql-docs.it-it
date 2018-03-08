---
title: Il filtro per aggiornata i record | Documenti Microsoft
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
helpviewer_keywords:
- filtering for updated records [ADO]
ms.assetid: 4a798921-d7bb-47c9-a252-550fd9463ec9
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c6fee8a407c5cc01e768eb86854c07d215fc420d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="filtering-for-updated-records"></a>Il filtro per i record aggiornati
Prima di chiamare UpdateBatch, è possibile utilizzare la proprietà filtro Recordset per visualizzare solo i record che sono stati modificati dopo l'apertura del Recordset o l'ultima chiamata al metodo UpdateBatch. A tale scopo, impostare la proprietà Filter su adFilterPendingRecords per determinare il numero di record verrà aggiornato, come illustrato nell'esempio di codice nella sezione successiva.  
  
## <a name="remarks"></a>Osservazioni  
 In questo esempio estende l'esempio precedente UpdateBatch filtro Recordset appena prima della chiamata al metodo UpdateBatch, visualizzare i record che verranno modificato e consentendo di annullare l'aggiornamento (tramite il metodo CancelBatch).  
  
```  
'BeginFilterPend  
    '...  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    objRs1.Filter = adFilterPendingRecords  
  
    MsgBox "There are " & objRs1.RecordCount & " records pending.", _  
            , "Filter Pending"  
  
    ' Cancel the updates  
    objRs1.CancelBatch  
'EndFilterPend  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)
