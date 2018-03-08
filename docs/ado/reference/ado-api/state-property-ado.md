---
title: "Lo stato delle proprietà (ADO) | Documenti Microsoft"
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
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d8f1b832d0af4840bab697cbcd9b62eca4f90496
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="state-property-ado"></a>Proprietà state (ADO)
Indica per tutti gli oggetti applicabili se lo stato dell'oggetto è aperto o chiuso. Se l'oggetto è in esecuzione un metodo asincrono, indica se lo stato corrente dell'oggetto connessione, l'esecuzione o il recupero.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore che può essere un [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) valore. Il valore predefinito è **adStateClosed**.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile utilizzare il **stato** proprietà per determinare lo stato corrente di un oggetto specifico in qualsiasi momento.  
  
 L'oggetto **stato** proprietà può avere una combinazione di valori. Ad esempio, se viene eseguita un'istruzione, questa proprietà sarà assegnato un valore combinato di **adStateOpen** e **adStateExecuting**.  
  
 Il **stato** proprietà è di sola lettura.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [Esempio ConnectionString, ConnectionTimeout e la proprietà State (VC + +)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
