---
title: "Proprietà DateCreated (ADOX) | Documenti Microsoft"
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
- _Table::get_DateCreated
- _Table::DateCreated
- _Table::GetDateCreated
helpviewer_keywords:
- DateCreated property [ADOX]
ms.assetid: 2bf4b00d-045c-444e-8af7-8af6297ed418
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c7f405958cdd28e6dd4ae285c29ce806c2a61074
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="datecreated-property-adox"></a>Proprietà DateCreated (ADOX)
Indica la data che di creazione dell'oggetto.  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un **Variant** valore che specifica la data di creazione. Il valore è null se **DateCreated** non è supportato dal provider.  
  
## <a name="remarks"></a>Osservazioni  
 Il **DateCreated** proprietà è null per gli oggetti appena aggiunti. Dopo l'aggiunta di un nuovo [visualizzazione](../../../ado/reference/adox-api/view-object-adox.md) o [procedura](../../../ado/reference/adox-api/procedure-object-adox.md), è necessario chiamare il [aggiornamento](../../../ado/reference/ado-api/refresh-method-ado.md) metodo il [viste](../../../ado/reference/adox-api/views-collection-adox.md) o [procedure ](../../../ado/reference/adox-api/procedures-collection-adox.md) insieme per ottenere valori per il **DateCreated** proprietà.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Procedure (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[Oggetto Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[Oggetto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio DateCreated e DateModified proprietà (Visual Basic)](../../../ado/reference/adox-api/datecreated-and-datemodified-properties-example-vb.md)   
 [Proprietà DateModified (ADOX)](../../../ado/reference/adox-api/datemodified-property-adox.md)
