---
title: "Tipo di esempio di proprietà (proprietà) (VB) | Documenti Microsoft"
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
- Type property [property] [ADO], Visual Basic example
ms.assetid: 2ee8e4c5-1d66-4a77-8892-6dad7e07e611
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ea71c68359ffb7c312b38675ae55f26e8eee479
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="type-property-example-property-vb"></a>Esempio di proprietà Type (proprietà) (VB)
Questo esempio viene illustrato il [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà. Si tratta di un modello di un'utilità per elencare i nomi e tipi di una raccolta, ad esempio [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md), [campi](../../../ado/reference/ado-api/fields-collection-ado.md)e così via.  
  
 Non è necessaria aprire la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) per accedere a relativo **proprietà** insieme; diventano esistenza quando il **Recordset** viene creata un'istanza di oggetto. Tuttavia, l'impostazione di [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) proprietà **adUseClient** aggiunge diverse proprietà dinamiche per la **Recordset** dell'oggetto **proprietà** insieme, rendendo più interessante l'esempio. Dimostrativo, si utilizza in modo esplicito il [elemento](../../../ado/reference/ado-api/item-property-ado.md) proprietà per accedere a ogni [proprietà](../../../ado/reference/ado-api/property-object-ado.md) oggetto.  
  
```  
'BeginTypePropertyVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' recordset variables  
    Dim rst As ADODB.Recordset  
    Dim prop As ADODB.Property  
     ' property variables  
    Dim ix As Integer  
    Dim strMsg As String  
  
     ' create client-side recordset  
    Set rst = New ADODB.Recordset  
    rst.CursorLocation = adUseClient  
     ' enumerate property types  
    For ix = 0 To rst.Properties.Count - 1  
        Set prop = rst.Properties.Item(ix)  
        Select Case prop.Type  
           Case adBigInt  
              strMsg = "adBigInt"  
           Case adBinary  
              strMsg = "adBinary"  
           Case adBoolean  
              strMsg = "adBoolean"  
           Case adBSTR  
              strMsg = "adBSTR"  
           Case adChapter  
              strMsg = "adChapter"  
           Case adChar  
              strMsg = "adChar"  
           Case adCurrency  
              strMsg = "adCurrency"  
           Case adDate  
              strMsg = "adDate"  
           Case adDBDate  
              strMsg = "adDBDate"  
           Case adDBTime  
              strMsg = "adDBTime"  
           Case adDBTimeStamp  
              strMsg = "adDBTimeStamp"  
           Case adDecimal  
              strMsg = "adDecimal"  
           Case adDouble  
              strMsg = "adDouble"  
           Case adEmpty  
              strMsg = "adEmpty"  
           Case adError  
              strMsg = "adError"  
           Case adFileTime  
              strMsg = "adFileTime"  
           Case adGUID  
              strMsg = "adGUID"  
           Case adIDispatch  
              strMsg = "adIDispatch"  
           Case adInteger  
              strMsg = "adInteger"  
           Case adIUnknown  
              strMsg = "adIUnknown"  
           Case adLongVarBinary  
              strMsg = "adLongVarBinary"  
           Case adLongVarChar  
              strMsg = "adLongVarChar"  
           Case adLongVarWChar  
              strMsg = "adLongVarWChar"  
           Case adNumeric  
              strMsg = "adNumeric"  
           Case adPropVariant  
              strMsg = "adPropVariant"  
           Case adSingle  
              strMsg = "adSingle"  
           Case adSmallInt  
              strMsg = "adSmallInt"  
           Case adTinyInt  
              strMsg = "adTinyInt"  
           Case adUnsignedBigInt  
              strMsg = "adUnsignedBigInt"  
           Case adUnsignedInt  
              strMsg = "adUnsignedInt"  
           Case adUnsignedSmallInt  
              strMsg = "adUnsignedSmallInt"  
           Case adUnsignedTinyInt  
              strMsg = "adUnsignedTinyInt"  
           Case adUserDefined  
              strMsg = "adUserDefined"  
           Case adVarBinary  
              strMsg = "adVarBinary"  
           Case adVarChar  
              strMsg = "adVarChar"  
           Case adVariant  
              strMsg = "adVariant"  
           Case adVarNumeric  
              strMsg = "adVarNumeric"  
           Case adVarWChar  
              strMsg = "adVarWChar"  
           Case adWChar  
              strMsg = "adWChar"  
           Case Else  
              strMsg = "*UNKNOWN*"  
        End Select  
            'show results  
        Debug.Print "Property " & ix & ": " & prop.Name & _  
                    ", Type = " & strMsg  
    Next ix  
  
    ' clean up  
    Set rst = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    Set rst = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
'EndTypePropertyVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di proprietà (ADO)](../../../ado/reference/ado-api/property-object-ado.md)   
 [Proprietà Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)
