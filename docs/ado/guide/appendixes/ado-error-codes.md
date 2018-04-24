---
title: Codici di errore ADO | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], error codes
ms.assetid: 3aee61c7-a9b7-4596-b78e-5828a00d0281
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 55b434f3106e8c4847aeabcec90694bd9d89a7c6
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="capture-ado-error-codes"></a>Acquisire i codici di errore ADO
Oltre agli errori del provider restituiti nel [errore](../../../ado/reference/ado-api/error-object.md) gli oggetti del [errori](../../../ado/reference/ado-api/errors-collection-ado.md) insieme, ADO può restituire errori al meccanismo di gestione delle eccezioni dell'ambiente in fase di esecuzione. Utilizzare il meccanismo di intercettazione degli errori del linguaggio di programmazione, ad esempio il **in caso di errore** istruzione in Microsoft® Visual Basic o **try-catch** bloccare nella Microsoft Visual C++®, per acquisire gli errori di ADO.

 Per l'elenco dei codici di errore ADO, vedere [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md).

## <a name="see-also"></a>Vedere anche
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md) [raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)
