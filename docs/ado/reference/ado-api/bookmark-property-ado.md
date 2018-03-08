---
title: "Proprietà Bookmark (ADO) | Documenti Microsoft"
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
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3c6076acd2bde7e82bf142bad76093d582106877
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="bookmark-property-ado"></a>Proprietà Bookmark (ADO)
Indica un segnalibro che identifica in modo univoco il record corrente in un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dell'oggetto o imposta il record corrente in un **Recordset** oggetto sul record identificato da un segnalibro valido.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Variant** un'espressione che restituisca un segnalibro valido.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **segnalibro** proprietà per salvare la posizione del record corrente e tornare al record specifico in qualsiasi momento. I segnalibri sono disponibili solo in **Recordset** gli oggetti che supportano la funzionalità corrispondente.  
  
 Quando si apre un **Recordset** dell'oggetto, ognuno dei relativi record dispone di un segnalibro univoco. Per salvare il segnalibro per il record corrente, assegnare il valore di **segnalibro** proprietà a una variabile. Per tornare rapidamente al record specifico in qualsiasi momento dopo il passaggio a un altro record, impostare il **Recordset** dell'oggetto **segnalibro** sul valore della variabile.  
  
 L'utente potrebbe non essere in grado di visualizzare il valore del segnalibro. Inoltre, gli utenti non devono aspettarsi che segnalibri in modo da essere direttamente confrontabili??? due segnalibri che fanno riferimento allo stesso record possono avere valori diversi.  
  
 Se si utilizza il [Clone](../../../ado/reference/ado-api/clone-method-ado.md) metodo per creare una copia di un **Recordset** oggetto, il **segnalibro** impostazioni delle proprietà per originale e il duplicato **Recordset**  oggetti sono identici e utilizzarle in modo intercambiabile. Tuttavia, non è possibile utilizzare i segnalibri da diversi **Recordset** oggetti in modo intercambiabile, anche se sono stati creati dall'origine o comando stesso.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando utilizzato sul lato client **Recordset** oggetto, il **segnalibro** proprietà è sempre disponibile.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà di segnalibro (VB), EOF e BOF](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [Esempio di proprietà di segnalibro (VC + +), EOF e BOF](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Metodo Supports](../../../ado/reference/ado-api/supports-method.md)
