---
title: "Proprietà Status (Recordset ADO) | Documenti Microsoft"
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
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1a8b65d43534fd75a9d6d8e659959100c5bea14f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="status-property-ado-recordset"></a>Proprietà Status (Recordset ADO)
Indica lo stato del record corrente rispetto all'aggiornamento batch o altre operazioni bulk.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce la somma di uno o più [RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **stato** proprietà per individuare le modifiche in sospeso per i record modificati durante l'aggiornamento in batch. È inoltre possibile utilizzare il **stato** proprietà per visualizzare lo stato del record con esito negativo durante le operazioni bulk, ad esempio quando si chiama il [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), o [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) metodi su un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto o impostare il [filtro](../../../ado/reference/ado-api/filter-property.md) proprietà in un **Recordset** oggetto in una matrice di segnalibri. Questa proprietà, è possibile determinare come un record specificato non è riuscita e risolverlo di conseguenza.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Status (Recordset) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Esempio di proprietà Status (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
