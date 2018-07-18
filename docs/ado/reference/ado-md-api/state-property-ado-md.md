---
title: Lo stato delle proprietà (ADO MD) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- State
- Cellset::State
helpviewer_keywords:
- State property [ADO MD]
ms.assetid: 06d480ca-9eb6-4570-a45d-a73539bddd32
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 975a9354734e0f6e5d0a2502b89b43c886be5fa3
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35284560"
---
# <a name="state-property-ado-md"></a>Proprietà state (ADO MD)
Indica lo stato corrente del set di celle.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **lungo** intero che indica la condizione corrente del [set di celle](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto ed è di sola lettura. I seguenti valori validi sono: **adStateClosed** (0) e **adStateOpen** (1).  
  
## <a name="remarks"></a>Remarks  
 Utilizzare il [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) i nomi delle costanti, è necessario disporre della libreria dei tipi ADO a cui fa riferimento nel progetto. Vedere [utilizzo di ADO con ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md) per ulteriori informazioni.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Close (metodo) (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Metodo Open (ADO MD)](../../../ado/reference/ado-md-api/open-method-ado-md.md)
