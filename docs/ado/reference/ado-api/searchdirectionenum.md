---
title: SearchDirectionEnum | Documenti Microsoft
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
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 46b8e127ed67c71a733cf232e92e967a031b4314
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Specifica la direzione di una ricerca di record all'interno di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Interruzione all'inizio di ricerche con le versioni precedenti, il **Recordset**. Se non viene trovata una corrispondenza, il puntatore del record è posizionato in corrispondenza [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Ricerca in avanti, fino alla fine del **Recordset**. Se non viene trovata una corrispondenza, il puntatore del record è posizionato in corrispondenza [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Find (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
