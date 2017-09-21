---
title: CursorLocationEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c0937fcab4319e24a2bd213971bea2761b94df75
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Specifica il percorso del servizio di cursore.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Utilizza i cursori sul lato client forniti da una libreria di cursori locali. I servizi cursore locali spesso consentirà molte funzionalità che i cursori forniti dal driver, non possono pertanto l'utilizzo di questa impostazione può garantire un vantaggio rispetto alla funzionalità che verranno abilitati. Per compatibilità con le versioni precedenti, il sinonimo **adUseClientBatch** è anche supportato.|  
|**adUseNone**|1|Non utilizza i servizi di cursore. (Questa costante è obsoleta e verrà visualizzato solo per compatibilità con le versioni precedenti).|  
|**adUseServer**|2|Valore predefinito. Utilizza i cursori forniti dal provider di dati o driver. Questi cursori sono a volte è molto flessibili e consentano ulteriori sensibilità alle modifiche apportate da altri file di dati. Tuttavia, alcune funzionalità del [il cursore per il servizio Microsoft OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), ad esempio l'associazione<br /><br /> [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetti, non possono essere simulati con cursori sul lato server e queste funzionalità non sarà disponibile con questa impostazione.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Pacchetto: **com.ms. wfc.**  
  
|Costante|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà CursorLocation (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)