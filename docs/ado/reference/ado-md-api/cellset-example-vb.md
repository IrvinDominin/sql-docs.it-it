---
title: Esempio di set di celle (VB) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Cellset object [ADO MD], Visual Basic example
ms.assetid: 2666ad1c-b48e-4b2c-b269-5a9f4e4a7810
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb42d133c68942c690f9976af08e1283b49caf85
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35283360"
---
# <a name="cellset-example-vb"></a>Esempio di set di celle (VB)
Questo progetto di Visual Basic viene illustrato l'utilizzo di ADO MD per accedere ai dati del cubo di base. Visualizza le didascalie dei membri per le intestazioni di riga e colonna, quindi Visualizza i valori di celle specifiche all'interno del set di celle formattati.  
  
```  
Private Sub cmdCellSettoDebugWindow_Click()  
Dim cat As New ADOMD.Catalog  
Dim cst As New ADOMD.Cellset  
Dim i As Integer  
Dim j As Integer  
Dim strServer As String  
Dim strSource As String  
Dim strColumnHeader As String  
Dim strRowText As String  
  
On Error GoTo Error_cmdCellSettoDebugWindow_Click  
Screen.MousePointer = vbHourglass  
'*-----------------------------------------------------------------------  
'* Set Server to Local Host  
'*-----------------------------------------------------------------------  
    strServer = "LOCALHOST"  
  
'*-----------------------------------------------------------------------  
'* Set MDX query string Source  
'*-----------------------------------------------------------------------  
    strSource = strSource & "SELECT "  
    strSource = strSource & "{[Measures].members} ON COLUMNS,"  
    strSource = strSource & _  
        "NON EMPTY [Store].[Store City].members ON ROWS"  
    strSource = strSource & " FROM Sales"  
  
'*-----------------------------------------------------------------------  
'* Set Active Connection  
'*-----------------------------------------------------------------------  
        cat.ActiveConnection = "Data Source=" & strServer & _  
            ";Provider=msolap;"  
  
'*-----------------------------------------------------------------------  
'* Set Cell Set source to MDX query string  
'*-----------------------------------------------------------------------  
        cst.Source = strSource  
  
'*-----------------------------------------------------------------------  
'* Set Cell Sets active connection to current connection  
'*-----------------------------------------------------------------------  
    Set cst.ActiveConnection = cat.ActiveConnection  
  
'*-----------------------------------------------------------------------  
'* Open Cell Set  
'*-----------------------------------------------------------------------  
    cst.Open  
  
'*-----------------------------------------------------------------------  
'* Allow space for Row Header Text  
'*-----------------------------------------------------------------------  
strColumnHeader = vbTab & vbTab & vbTab & vbTab & vbTab & vbTab  
  
'*-----------------------------------------------------------------------  
'* Loop through Column Headers  
'*-----------------------------------------------------------------------  
       For i = 0 To cst.Axes(0).Positions.Count - 1  
            strColumnHeader = strColumnHeader & _  
                cst.Axes(0).Positions(i).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
       Next  
       Debug.Print vbTab & strColumnHeader & vbCrLf  
  
'*-----------------------------------------------------------------------  
'* Loop through Row Headers and Provide data for each row  
'*-----------------------------------------------------------------------  
        strRowText = ""  
        For j = 0 To cst.Axes(1).Positions.Count - 1  
            strRowText = strRowText & _  
                cst.Axes(1).Positions(j).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
            For k = 0 To cst.Axes(0).Positions.Count - 1  
                strRowText = strRowText & cst(k, j).FormattedValue & _  
                    vbTab & vbTab & vbTab & vbTab  
            Next  
            Debug.Print strRowText & vbCrLf  
            strRowText = ""  
        Next  
  
    Screen.MousePointer = vbDefault  
Exit Sub  
  
Error_cmdCellSettoDebugWindow_Click:  
   Beep  
   Screen.MousePointer = vbDefault  
   MsgBox "The Following Error has occurred:" & vbCrLf & _  
      Err.Description, vbCritical, " Error!"  
   Exit Sub  
End Sub  
```
