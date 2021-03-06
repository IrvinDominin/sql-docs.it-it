---
title: Provider obbligatori per il Data Shaping | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 482139f8aa3dc42bbd17593b58fcc8510f1fc9a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713839"
---
# <a name="required-providers-for-data-shaping"></a>Provider necessari per il data shaping
Il data shaping in genere richiede due provider. Il provider di servizi [Data shaping per OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), fornisce i dati di data shaping, funzionalità e un provider di dati, ad esempio il Provider OLE DB per SQL Server, che include le righe di dati per popolare il data shaping [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Il nome del provider di servizi (MSDataShape) può essere specificato come valore dei [Connection](../../../ado/reference/ado-api/connection-object-ado.md) oggetto [Provider](../../../ado/reference/ado-api/provider-property-ado.md) proprietà o parola chiave della stringa di connessione "Provider = MSDataShape;".  
  
 Il nome del provider di dati può essere specificato come valore dei **Provider di dati** proprietà dinamiche, che viene aggiunto al **connessione** oggetto [proprietà](../../../ado/reference/ado-api/properties-collection-ado.md) raccolta in base al il Data shaping per OLE DB o parola chiave della stringa di connessione "**Provider di dati = * * * provider*".  
  
 Nessun provider di dati è obbligatorio se il **Recordset** non viene popolata (ad esempio, come un creato **Recordset** in cui le colonne vengono create con la nuova parola chiave). In tal caso, specificare "**Provider di dati =** none;".  
  
## <a name="example"></a>Esempio  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di Data Shaping](../../../ado/guide/data/data-shaping-example.md)   
 [Grammatica formale per Shape](../../../ado/guide/data/formal-shape-grammar.md)   
 [Comandi Shape in generale](../../../ado/guide/data/shape-commands-in-general.md)
