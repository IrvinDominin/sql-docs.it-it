---
title: "Esempio di proprietà IndexNulls (VB) | Documenti Microsoft"
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
- IndexNulls property [ADOX], Visual Basic example
ms.assetid: 45204669-32c0-4690-aab9-ddf0fd71ae48
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d06e784cac696737b5e913ec5bb302a6c976173
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="indexnulls-property-example-vb"></a>Esempio di proprietà IndexNulls (VB)
Questo esempio viene illustrato il [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) proprietà di un [indice](../../../ado/reference/adox-api/index-object-adox.md). Il codice crea un nuovo indice e imposta il valore di **IndexNulls** basato sull'input dell'utente (da un elenco denominato List1). Quindi, **indice** viene aggiunto il **dipendenti** [tabella](../../../ado/reference/adox-api/table-object-adox.md) nel *Northwind* [catalogo](../../../ado/reference/adox-api/catalog-object-adox.md). Il nuovo **indice** viene applicato a un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) in base il **dipendenti** tabella e **Recordset** viene aperto. Viene aggiunto un nuovo record per il **dipendenti** tabella, con un **Null** valore nel campo indicizzato. Se viene visualizzato il nuovo record dipende dall'impostazione del **IndexNulls** proprietà.  
  
```  
' BeginIndexNullsVB  
Private Sub cmdIndexNulls_Click()  
    IndexNullsX  
End Sub  
  
Sub IndexNullsX()  
  
    Dim cnn As New ADODB.Connection  
    Dim catNorthwind As New ADOX.Catalog  
    Dim idxNew As New ADOX.Index  
    Dim rstEmployees As New ADODB.Recordset  
    Dim varBookmark As Variant  
  
    ' Connect the catalog.  
    cnn.Open "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "data source=c:\Program Files\" & _  
        "Microsoft Office\Office\Samples\Northwind.mdb;"  
  
    Set catNorthwind.ActiveConnection = cnn  
  
    ' Append Country column to new index  
    idxNew.Columns.Append "Country"  
    idxNew.Name = "NewIndex"  
  
    ' Set IndexNulls based on user selection in listbox List1  
    Select Case List1.List(List1.ListIndex)  
        Case "Allow"  
            idxNew.IndexNulls = adIndexNullsAllow  
        Case "Ignore"  
            idxNew.IndexNulls = adIndexNullsIgnore  
        Case Else  
            End  
    End Select  
  
    'Append new index to Employees table  
    catNorthwind.Tables("Employees").Indexes.Append idxNew  
  
    rstEmployees.Index = idxNew.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        ' Add a new record to the Employees table.  
        .AddNew  
        !FirstName = "Gary"  
        !LastName = "Haarsager"  
        .Update  
  
        ' Bookmark the newly added record  
        varBookmark = .Bookmark  
  
        ' Use the new index to set the order of the records.  
        .MoveFirst  
  
        Debug.Print "Index = " & .Index & _  
            ", IndexNulls = " & idxNew.IndexNulls  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & _  
                IIf(IsNull(!Country), "[Null]", !Country) & _  
                " - " & !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        ' Delete new record because this is a demonstration.  
        .Bookmark = varBookmark  
        .Delete  
  
        .Close  
    End With  
  
    ' Delete new Index because this is a demonstration.  
    catNorthwind.Tables("Employees").Indexes.Delete idxNew.Name  
    Set catNorthwind = Nothing  
  
End Sub  
' EndIndexNullsVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Index (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Proprietà IndexNulls (ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
