---
title: "Oggetto di proprietà (ADOX) | Documenti Microsoft"
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
apitype: COM
helpviewer_keywords:
- Property object [ADOX]
ms.assetid: 6a56def6-dbe6-4ccc-a491-8d076889f019
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c9d13366eb3554738fbd50da2ed09db8bceb6f5d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="property-object-adox"></a>Oggetto di proprietà (ADOX)
Rappresenta una caratteristica di un oggetto ADOX.  
  
## <a name="remarks"></a>Osservazioni  
 Gli oggetti ADOX dispongono di due tipi di proprietà: incorporato e dinamici.  
  
 Proprietà predefinite sono quelle immediatamente disponibili per qualsiasi nuovo oggetto, utilizzando la sintassi MyObject. Non vengono visualizzati come oggetti di proprietà in un oggetto [raccolta delle proprietà](../../../ado/reference/ado-api/properties-collection-ado.md), sebbene sia possibile modificare i relativi valori, è pertanto possibile modificare le relative caratteristiche.  
  
 Proprietà dinamiche sono definite dal provider di dati sottostante e vengono visualizzati nella raccolta delle proprietà per l'oggetto ADOX appropriato.  Proprietà dinamiche possono fare riferimento solo tramite la raccolta utilizzando la sintassi MyObject.Properties(0) o MyObject.  
  
 È possibile eliminare il tipo di proprietà.  
  
 Un oggetto dinamico di proprietà presenta quattro proprietà predefinite di un proprio:  
  
 Il [nome](../../../ado/reference/ado-api/name-property-ado.md) proprietà è una stringa che identifica la proprietà.  
  
 Il [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà è un numero intero che specifica il tipo di dati di proprietà.  
  
 Il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà è una variabile variant contenente l'impostazione della proprietà. Valore è la proprietà predefinita per un oggetto di proprietà.  
  
 Il [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) proprietà è un valore long che indica le caratteristiche della proprietà specifiche del provider.  
  
 In questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Property ADOX](../../../ado/reference/adox-api/adox-property-object-properties-methods-and-events.md)
