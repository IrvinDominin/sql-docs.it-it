---
title: Interfaccia ADORecordsetConstruction | Documenti Microsoft
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
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c19ec5d0b2439af92306dc655520a25b7ed5bc51
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="adorecordsetconstruction-interface"></a>Interfaccia ADORecordsetConstruction
Il **ADORecordsetConstruction** interfaccia viene utilizzata per costruire un oggetto ADO **Recordset** oggetto da OLE DB **set di righe** oggetto in un'applicazione C/C++.  
  
 Questa interfaccia supporta le proprietà seguenti:  
  
## <a name="properties"></a>Proprietà  
  
|||  
|-|-|  
|[capitolo](../../../ado/reference/ado-api/chapter-property-ado.md)|Lettura/scrittura.<br />Ottiene o imposta il valore OLE DB **capitolo** oggetto da/su questo ADO **Recordset** oggetto.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Lettura/scrittura.<br />Ottiene o imposta il valore OLE DB **RowPosition** oggetto da/su questo ADO **Recordset** oggetto.|  
|[Rowset](../../../ado/reference/ado-api/rowset-property-ado.md)|Lettura/scrittura.<br />Ottiene o imposta il valore OLE DB **set di righe** oggetto da/su questo ADO **Recordset** oggetto.|  
  
## <a name="methods"></a>Metodi  
 Nessuno  
  
## <a name="events"></a>Eventi  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Data OLE DB **set di righe** oggetto (`pRowset`), la costruzione di un oggetto ADO **Recordset** oggetto (`adoRs`) gli importi di tre operazioni di base seguenti:  
  
1.  Creare un oggetto ADO **Recordset** oggetto:  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Query di **IADORecordsetConstruction** interfaccia il **Recordset** oggetto:  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Chiamare il `IADORecordsetConstruction::put_Rowset` il metodo di proprietà per impostare OLE DB `Rowset` sull'oggetto ADO `Recordset` oggetto:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 I risultanti `adoRs` oggetto rappresenta l'oggetto ADO **Recordset** oggetto costruito da OLE DB **set di righe** oggetto.  
  
 È inoltre possibile costruire un oggetto ADO **Recordset** oggetto da OLE DB **capitolo** o **RowPosition** oggetto.  
  
## <a name="requirements"></a>Requisiti  
 **Versione:** ADO 2.0 e versioni successiva  
  
 **Libreria:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Recordset ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Proprietà Rowset (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
