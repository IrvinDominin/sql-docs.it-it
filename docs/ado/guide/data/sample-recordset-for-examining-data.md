---
title: Per l'analisi dei dati di esempio Recordset | Documenti Microsoft
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
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d72ef02cdc7abac1b51fa2450ca9d6766311bda0
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="sample-recordset-for-examining-data"></a>Set di record di esempio per l'analisi dei dati
In primo luogo, si esaminerà il **Recordset** dell'oggetto restituito utilizzando la seguente query SQL, eseguita su base in Microsoft SQL Server i dati di esempio Northwind.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 I risultanti **Recordset** oggetto contiene tutte le produce nel database di cui è illustrato nella tabella seguente.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Pere secca organici frutta|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle rossi|45.6000|  
|51|Manjimup essiccati mele|53.0000|  
|74|Tofu a lunga conservazione|10.0000|  
  
 Se si è interessati a ottenere questi risultati manualmente, provare a eseguire l'esempio JScript seguente:  
  
-   [Esempio di JScript per restituire un Recordset](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
