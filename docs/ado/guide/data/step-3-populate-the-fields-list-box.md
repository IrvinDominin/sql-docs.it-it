---
title: 'Passaggio 3: Popolare la casella di riepilogo di campi | Documenti Microsoft'
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
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53600209952c84dc19009348df580fb660cbe396
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="step-3-populate-the-fields-list-box"></a>Passaggio 3: Popolare la casella di riepilogo di campi
Per popolare la casella di elenco di campi, inserire il codice seguente nel gestore dell'evento Click del `lstMain`:  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 Questo codice dichiara e crea un'istanza locali Record e gli oggetti Recordset, `rec` e `rs`, rispettivamente.  
  
 La riga corrispondente alla risorsa selezionata `lstMain` diventa la riga corrente di `grs`. Quindi è deselezionata la casella di riepilogo dei dettagli e `rec` viene aperto con la riga corrente di `grs` come origine.  
  
 Se la risorsa è un record, come specificato da [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), il Recordset locale `rs` viene aperto sugli elementi figlio di rec. Quindi `lstDetails` viene riempita con i valori dalle righe di `rs`.  
  
 Se la risorsa è un semplice record, `recFields` viene chiamato. Per ulteriori informazioni su `recFields`, vedere il passaggio successivo.  
  
 Se la risorsa è un documento strutturato, viene implementato alcun codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione su Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 2: Inizializzare la casella di riepilogo principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Passaggio 4: Popolare la casella di riepilogo Details](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
