---
title: "Cluster di esempio di proprietà (VB) | Documenti Microsoft"
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
dev_langs:
- VB
helpviewer_keywords:
- Clustered property [ADOX], Visual Basic example
ms.assetid: 1cd30769-c8af-43e7-be27-12ed0434daa1
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2d1fd197bf6b50ad4f5fbf31591c9ce33f39956a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="clustered-property-example-vb"></a>Esempio di proprietà Clustered (VB)
Questo esempio viene illustrato il [Clustered](../../../ado/reference/adox-api/clustered-property-adox.md) proprietà di un [indice](../../../ado/reference/adox-api/index-object-adox.md). Si noti che i database Microsoft Jet non supporta gli indici cluster, pertanto in questo esempio restituirà **False** per il **Clustered** proprietà di tutti gli indici di **Northwind** database.  
  
```  
' BeginClusteredVB  
Sub Main()  
    On Error GoTo ClusteredXError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tblLoop As ADOX.Table  
    Dim idxLoop As ADOX.Index  
    Dim strCnn As String  
  
    strCnn = "Provider='SQLOLEDB';Data Source='MySqlServer';Initial Catalog='pubs';" & _  
        "Integrated Security='SSPI';"  
    ' Connect to the catalog.  
    cnn.Open strCnn  
    cat.ActiveConnection = cnn  
  
    ' Enumerate the tables.  
    For Each tblLoop In cat.Tables  
        'Enumerate the indexes.  
        For Each idxLoop In tblLoop.Indexes  
            Debug.Print tblLoop.Name & " " & _  
                idxLoop.Name & " " & idxLoop.Clustered  
        Next idxLoop  
    Next tblLoop  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ClusteredXError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndClusteredVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto del catalogo (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Proprietà Clustered (ADOX)](../../../ado/reference/adox-api/clustered-property-adox.md)   
 [Oggetto Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)
