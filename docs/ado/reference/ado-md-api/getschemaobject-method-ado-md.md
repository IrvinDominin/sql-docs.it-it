---
title: Metodo GetSchemaObject (ADO MD) | Documenti Microsoft
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
- GetSchemaObject
- Cellset::GetSchemaObject
helpviewer_keywords:
- GetSchemaObject method [ADO MD]
ms.assetid: 36b754b4-6b17-4dd1-a925-bca46938b7c4
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 01142e27e03cd85dcdd59e92737ee46a3bb4cf09
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="getschemaobject-method-ado-md"></a>Metodo GetSchemaObject (ADO MD)
Recupera un oggetto dello schema ADO MD ([dimensione](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [gerarchia](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [livello](../../../ado/reference/ado-md-api/level-object-ado-md.md), o [membro](../../../ado/reference/ado-md-api/member-object-ado-md.md)) dal relativo [UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set object = CubeDef.GetSchemaObject (ObjType, UniqueName)  
```  
  
#### <a name="parameters"></a>Parametri  
 *ObjType*  
 Oggetto [SchemaObjectTypeEnum](../../../ado/reference/ado-md-api/schemaobjecttypeenum.md) valore che specifica il tipo di oggetto dello schema (dimensione, gerarchia, livello o membro) da recuperare.  
  
 *UniqueName*  
 Oggetto **stringa** specificando il **UniqueName** valore della proprietà dell'oggetto da recuperare.  
  
## <a name="remarks"></a>Osservazioni  
 **GetSchemaObject** recupera gli oggetti utilizzando i nomi univoci, come specificato dal **UniqueName** proprietà. Non è necessario conoscere i nomi degli oggetti padre e raccolte padre non è necessario essere popolati per recuperare un oggetto dello schema.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto CubeDef (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)
