---
title: Utilizzo di un oggetto Recordset | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 01c630d8-eb35-4bd0-a99f-7c0f85316cc1
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05a2c989d1f14849ef39b4ec93f4677ebc52510e
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35273180"
---
# <a name="using-a-recordset-object"></a>Utilizzo di un oggetto Recordset
In alternativa, è possibile utilizzare **Open** per stabilire una connessione in modo implicito e inviare un comando tramite la connessione in un'unica operazione. Ad esempio, in Visual Basic:  
  
```  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
  
' Create and Open the Recordset object.  
Set oRs = New ADODB.Recordset  
oRs.CursorLocation = adUseClient  
oRs.Open sSQL, sConn, adOpenStatic, _  
               adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
oRs.Close          
Set oRs = Nothing  
```  
  
 Si noti che **oRs.Open** accetta una stringa di connessione (*sConn*), al posto di un **connessione** oggetto (*oConn*), come valore del relativo  **ActiveConnection** parametro. Anche in cui viene applicato il tipo di cursore sul lato client impostando il **CursorLocation** proprietà il **Recordset** oggetto. Nuovamente, confrontare questa operazione con il **HelloData** esempio.
