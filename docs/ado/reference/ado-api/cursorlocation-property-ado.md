---
title: "Proprietà CursorLocation (ADO) | Documenti Microsoft"
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
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 194035b9ac6dfe320d90266c406976d93e18484a
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="cursorlocation-property-ado"></a>Proprietà CursorLocation (ADO)
Indica la posizione del servizio di cursore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore che può essere impostato su uno del [CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 Questa proprietà consente di scegliere tra varie librerie di cursori accessibili al provider. In genere, è possibile scegliere tra l'utilizzo di una libreria di cursori sul lato client o che si trova nel server.  
  
 Impostazione di questa proprietà influisce sulle connessioni stabilite solo dopo aver impostata la proprietà. Modifica il **CursorLocation** proprietà ha effetto sulle connessioni esistenti.  
  
 I cursori restituiti dal [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) metodo erediteranno questa impostazione. **Recordset** oggetti erediterà automaticamente questa impostazione dalle connessioni associate.  
  
 Questa proprietà è di lettura/scrittura in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) o un oggetto chiuso [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)e di sola lettura su un oggetto aperto **Recordset**.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** quando utilizzato sul lato client **Recordset** o **connessione** oggetto, il **CursorLocation** proprietà può essere impostata solo su **adUseClient**.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Appendice A: Provider](../../../ado/guide/appendixes/appendix-a-providers.md)
