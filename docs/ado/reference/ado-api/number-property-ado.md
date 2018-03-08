---
title: "Numero di proprietà (ADO) | Documenti Microsoft"
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
- Error::Number
- Error::GetNumber
- Error::get_Number
helpviewer_keywords:
- number property [ADO]
ms.assetid: f92323c5-dd11-4a63-a505-d9014a0f067f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f6a98f38098d936ea6c2eee03b28d969f1c0e506
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="number-property-ado"></a>Proprietà Number (ADO)
Indica il numero che identifica in modo univoco un [errore](../../../ado/reference/ado-api/error-object.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **lungo** valore che può corrispondere a uno del [ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md) costanti.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **numero** proprietà per determinare l'errore verificatosi. Il valore della proprietà è un numero univoco che corrisponde alla condizione di errore.  
  
 Il [errori](../../../ado/reference/ado-api/errors-collection-ado.md) raccolta restituisce un valore HRESULT in formato esadecimale (ad esempio, 0x80004005) o come valore long (ad esempio, 2147467259). Tali valori HRESULT possono essere generati da componenti sottostanti, ad esempio OLE DB o OLE stesso. Per ulteriori informazioni su tali numeri, vedere [errori (OLE DB)](http://msdn.microsoft.com/en-us/ed74e62d-4948-4eeb-a7c9-fd7ad46af7fd) nel [riferimento per programmatori OLE DB](http://msdn.microsoft.com/en-us/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8)*.*  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Error](../../../ado/reference/ado-api/error-object.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQLState (VB), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vb.md)   
 [Esempio di proprietà SQLState (VC + +), HelpContext, HelpFile, NativeError, numero, origine e descrizione](../../../ado/reference/ado-api/description-helpcontext-helpfile-nativeerror-number-source-example-vc.md)   
 [Proprietà Description](../../../ado/reference/ado-api/description-property.md)   
 [Proprietà HelpContext, HelpFile](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)   
 [Proprietà Source (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)
