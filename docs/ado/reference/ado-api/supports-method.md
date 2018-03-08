---
title: Supporta metodo | Documenti Microsoft
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
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b78cb1325b720207f6a18201971ef627314bfee
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="supports-method"></a>Supporta (metodo)
Determina se un oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto supporta un determinato tipo di funzionalità.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **booleano** valore che indica se tutte le funzionalità identificato dal *CursorOptions* argomento sono supportati dal provider.  
  
#### <a name="parameters"></a>Parametri  
 *CursorOptions*  
 Oggetto **lungo** espressione costituita da uno o più [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **supporta** metodo per determinare i tipi di funzionalità un **Recordset** supporta dell'oggetto. Se il **Recordset** oggetto supporta le funzionalità la cui costanti corrispondenti sono *CursorOptions*, **supporta** restituisce **True**. In caso contrario, restituisce **False**.  
  
> [!NOTE]
>  Sebbene il **supporta** metodo può restituire **True** per una determinata funzionalità non garantisce che il provider può rendere la funzionalità disponibile in tutte le circostanze. Il **supporta** metodo restituisce semplicemente se il provider supporta la funzionalità specificata, presupponendo che vengano soddisfatte determinate condizioni. Ad esempio, il **supporta** metodo può indicare che un **Recordset** oggetto supporta gli aggiornamenti anche se il cursore è basato su un join tra più tabelle, alcune colonne di cui non sono aggiornabili.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo di supporto (VB)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Esempio di metodo di supporto (VC + +)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [Proprietà CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
