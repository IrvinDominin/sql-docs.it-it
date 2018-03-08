---
title: "Proprietà (flusso ADO) Size | Documenti Microsoft"
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
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfd7bc505122ec142e61d53cdd3502c8c6ad3075
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="size-property-ado-stream"></a>Proprietà Size (flusso ADO)
Indica le dimensioni del flusso in numero di byte.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **lungo** valore che specifica le dimensioni del flusso in numero di byte. Il valore predefinito è la dimensione di flusso, oppure -1 se la dimensione del flusso non è noto.  
  
## <a name="remarks"></a>Osservazioni  
 **Dimensioni** può essere utilizzato solo con open [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti.  
  
> [!NOTE]
>  Qualsiasi numero di bit può essere archiviato un **flusso** oggetto, limitato solo dalle risorse di sistema. Se il **flusso** contiene più di bit che può essere rappresentato da un **lungo** valore **dimensioni** viene troncato e pertanto non rappresentare accuratamente il numero di **Flusso**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà Size (parametro ADO)](../../../ado/reference/ado-api/size-property-ado-parameter.md)
