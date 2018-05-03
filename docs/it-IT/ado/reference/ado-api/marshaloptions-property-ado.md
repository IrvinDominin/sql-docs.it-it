---
title: Proprietà MarshalOptions (ADO) | Documenti Microsoft
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
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae6a344b170053dec48878e4f7988cb6408ee318
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="marshaloptions-property-ado"></a>Proprietà MarshalOptions (ADO)
Indica i record del [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) devono essere sottoposti a marshalling al server.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md) valore. Il valore predefinito è **adMarshalAll**.  
  
## <a name="remarks"></a>Osservazioni  
 Quando si utilizza un client-side [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), i record che sono stati modificati sul client vengono scritte nel livello intermedio o di un server Web mediante una tecnica denominata marshalling su diversi, il processo di creazione di pacchetti e l'invio di metodo di interfaccia parametri attraverso i limiti di thread o processo. L'impostazione di **MarshalOptions** proprietà può migliorare le prestazioni quando viene effettuato il marshalling di dati remoti modificati per l'aggiornamento nel server Web o nel livello intermedio.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** questa proprietà viene utilizzata solo in un client-side **Recordset**.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà MarshalOptions (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [Esempio di proprietà MarshalOptions (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
