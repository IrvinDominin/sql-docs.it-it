---
title: "Esempio di proprietà ActiveCommand (VB) | Documenti Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ActiveCommand property [ADO], Visual Basic example
ms.assetid: 23b06499-62df-4f46-88eb-6da392f9b456
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd034cdbd1b8188cb76344c1fb74f1b1e3fc9ba5
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="activecommand-property-example-vb"></a>Esempio di proprietà ActiveCommand (VB)
Questo esempio viene illustrato il [ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md) proprietà.  
  
 Una subroutine viene passato un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) i cui **ActiveCommand** proprietà viene utilizzata per visualizzare il testo del comando e parametro che ha creato il **Recordset**.  
  
```  
'BeginActiveCommandVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
        'recordset and connection variables  
    Dim cmd As ADODB.Command  
    Dim rst As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
        'record variables  
    Dim strPrompt As String  
    Dim strName As String  
  
    Set Cnxn = New ADODB.Connection  
    Set cmd = New ADODB.Command  
  
    strPrompt = "Enter an author's name (e.g., Ringer): "  
    strName = Trim(InputBox(strPrompt, "ActiveCommandX Example"))  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
  
        'create SQL command string  
    cmd.CommandText = "SELECT * FROM Authors WHERE au_lname = ?"  
    cmd.Parameters.Append cmd.CreateParameter("LastName", adChar, adParamInput, 20, strName)  
  
    Cnxn.Open strCnxn  
    cmd.ActiveConnection = Cnxn  
  
        'create the recordset by executing command string  
    Set rst = cmd.Execute(, , adCmdText)  
        'see the results  
    Call ActiveCommandXprint(rst)  
  
    ' clean up  
    Cnxn.Close  
    Set rst = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndActiveCommandVB  
```  
  
 Il **ActiveCommandXprint** routine viene assegnata solo un **Recordset** dell'oggetto, deve visualizzare il testo del comando e parametro che ha creato il **Recordset**. Questa operazione può essere eseguita perché la **Recordset** dell'oggetto **ActiveCommand** proprietà produce associato [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
 Il **comando** dell'oggetto [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà restituisce il comando con parametri che ha creato il **Recordset**. Il **comando** dell'oggetto [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) insieme restituisce il valore che è stata sostituita con segnaposto per il parametro del comando ("**?**").  
  
 Infine, vengono stampati un messaggio di errore o il nome dell'autore e ID.  
  
```  
'BeginActiveCommandPrintVB  
Public Sub ActiveCommandXprint(rstp As ADODB.Recordset)  
  
    Dim strName As String  
  
    strName = rstp.ActiveCommand.Parameters.Item("LastName").Value  
  
    Debug.Print "Command text = '"; rstp.ActiveCommand.CommandText; "'"  
    Debug.Print "Parameter = '"; strName; "'"  
  
    If rstp.BOF = True Then  
       Debug.Print "Name = '"; strName; "', not found."  
    Else  
       Debug.Print "Name = '"; rstp!au_fname; " "; rstp!au_lname; _  
             "', author ID = '"; rstp!au_id; "'"  
    End If  
  
    rstp.Close  
    Set rstp = Nothing  
End Sub  
'EndActiveCommandPrintVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActiveCommand (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)