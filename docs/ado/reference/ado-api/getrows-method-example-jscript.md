---
title: Esempio di metodo GetRows (JScript) | Documenti Microsoft
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
- JScript
helpviewer_keywords:
- Getrows method [ADO], JScript example
ms.assetid: d33467a5-5a56-450d-98c1-c3ce6f9f103c
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a6b3d16d4d9fb84d56a3bb7941f03348410d7d3d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="getrows-method-example-jscript"></a>Esempio di metodo GetRows (JScript)
Questo esempio viene utilizzato il [GetRows](../../../ado/reference/ado-api/getrows-method-ado.md) metodo per recuperare tutte le righe del *Custiomers* tabella da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) e per inserire una matrice con i dati risultanti. Il **GetRows** metodo restituirà inferiore al numero desiderato di righe in due casi: se [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) è stato raggiunto, oppure se **GetRows** ha tentato di recuperare un record eliminato da un altro utente. La funzione restituisce **False** solo se il secondo caso si verifica. Tagliare e incollare il codice seguente in blocco note o un altro editor di testo e salvarlo come **GetRowsJS**.  
  
```  
<!-- BeginGetRowsJS -->  
<%@ LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
  
<head>  
<title>ADO Recordset.GetRows Example (JScript)</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body bgcolor="white">  
  
<h1>ADO Recordset.GetRows Example (JScript)</h1>  
    <!-- Page text goes here -->  
<%  
        var Connect = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var mySQL = "select * from customers;";  
    var showblank = " ";  
    var shownull = "-null-";  
  
    var connTemp = Server.CreateObject("ADODB.Connection");  
  
    try  
    {  
        connTemp.Open(Connect);  
        var rsTemp = Server.CreateObject("ADODB.Recordset");  
        rsTemp.ActiveConnection = connTemp;  
        rsTemp.CursorLocation = adUseClient;  
        rsTemp.CursorType = adOpenKeyset;  
        rsTemp.LockType = adLockOptimistic;  
        rsTemp.Open(mySQL);  
  
        rsTemp.MoveFirst();  
  
        if (rsTemp.RecordCount == 0)  
        {  
            Response.Write("No records matched ");  
            Response.Write (mySQL & "So cannot make table...");  
            connTemp.Close();  
            Response.End();  
        } else  
        {  
            Response.Write('<table width="100%" border="2">');  
            Response.Write('<tr class="thead2">');  
  
            //  Headings On The Table for each Field Name  
            for (var i=0; i<rsTemp.Fields.Count; i++)  
            {  
                fieldObject = rsTemp.fields(i);  
                Response.Write('<td width="' + Math.floor(100 / rsTemp.Fields.Count) + '%">' + fieldObject.name + "</td>");  
            }  
  
            Response.Write("</tr>");  
  
            // JScript doesn't support multi-dimensional arrays  
            // so we'll convert the returned array to a single  
            // dimensional JScript array and then display the data.  
            tempArray = rsTemp.GetRows();  
            recArray = tempArray.toArray();  
  
            var col = 1;  
            var maxCols = rsTemp.Fields.Count;  
  
            for (var thisField=0; thisField<recArray.length; thisField++)  
            {  
                if (col == 1)  
                    Response.Write('<tr class="tbody">');  
                if (recArray[thisField] == null)  
                        recArray[thisField] = shownull;  
                if (recArray[thisField] == "")  
                        recArray[thisField] = showblank;  
                Response.Write("<td>" + recArray[thisField] + "</td>");  
                col++  
                if (col > maxCols)  
                {  
                    Response.Write("</tr>");  
                    col = 1;  
                }  
            }  
            Response.Write("</table>");  
        }  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // clean up  
        if (rsTemp.State == adStateOpen)  
            rsTemp.Close;  
        if (connTemp.State == adStateOpen)  
            connTemp.Close;  
        rsTemp = null;  
        connTemp = null;  
    }  
%>  
  
</body>  
  
</html>  
<!-- EndGetRowsJS -->  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo GetRows (ADO)](../../../ado/reference/ado-api/getrows-method-ado.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
