---
title: Risincronizzazione comando proprietà dinamica (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14aba77fcc6832412e6744f567887cc238c156ec
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="resync-command-property-dynamic-ado"></a>Risincronizzazione comando proprietà dinamica (ADO)
Specifica una stringa di un comando fornito dall'utente di [Resync](../../../ado/reference/ado-api/resync-method.md) i problemi dei metodi di aggiornamento dei dati nella tabella denominata nel [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) proprietà dinamiche.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che è una stringa di comando.  
  
## <a name="remarks"></a>Osservazioni  
 Il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto è il risultato di un'operazione di JOIN eseguita su più tabelle di base. Le righe interessate dipendono il *AffectRecords* parametro del [Resync](../../../ado/reference/ado-api/resync-method.md) metodo. Lo standard **Resync** metodo viene eseguito se il [tabella univoca](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) e **Resync Command** non sono impostate.  
  
 La stringa di comando del **Resync Command** proprietà è una stored procedure che identifica in modo univoco la riga da aggiornare o un comando con parametri e restituisce una singola riga con lo stesso numero e ordine delle colonne della riga da aggiornati. La stringa di comando contiene un parametro per ogni colonna chiave primaria di **tabella univoca**; in caso contrario, viene restituito un errore di run-time. I parametri vengono compilati automaticamente con i valori di chiave primaria della riga da aggiornare.  
  
 Di seguito sono riportati due esempi basati su SQL:  
  
 1\) il **Recordset** è definito da un comando:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 Il **Resync Command** proprietà è impostata su:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 Il **tabella univoca** è *ordini* e la relativa chiave primaria, *OrderID*, con parametri. Le Sub-select fornisce un modo semplice per garantire a livello di codice che lo stesso numero e ordine delle colonne vengono restituiti dal comando originale.  
  
 2\) il **Recordset** è definito da una stored procedure:  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 Il **Resync** metodo deve eseguire la stored procedure seguente:  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 Il **Resync Command** proprietà è impostata su:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 In questo caso, il **tabella univoca** è *ordini* e la relativa chiave primaria, *OrderID*, con parametri.  
  
 **Risincronizzazione comando** viene aggiunta una proprietà dinamica per il **Recordset** oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta quando il [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) è impostata su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
