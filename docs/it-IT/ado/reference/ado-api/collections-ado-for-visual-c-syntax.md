---
title: Raccolte (sintassi ADO per Visual C++) | Documenti Microsoft
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
dev_langs:
- C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: da75220f32fcd90d0785d802b5281cb5016da063
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="collections-ado-for-visual-c-syntax"></a>Raccolte (sintassi ADO per Visual C++)
## <a name="parameters"></a>Parametri  
  
### <a name="methods"></a>Metodi  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Metodo Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Metodo Delete (raccolta di parametri ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Proprietà  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Proprietà Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>Campi  
  
### <a name="methods"></a>Metodi  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Metodo Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Metodo Delete (raccolta di parametri ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Proprietà  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Proprietà Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>Errori  
  
### <a name="methods"></a>Metodi  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Metodo Clear (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Proprietà  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Proprietà Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>Proprietà  
  
### <a name="methods"></a>Metodi  
  
```  
Refresh(void);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Metodo Refresh (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>Proprietà  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 Per ulteriori informazioni, vedere  
  
-   [Proprietà Count (ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Proprietà Item (ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta di errori (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Raccolta di campi (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta di parametri (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)