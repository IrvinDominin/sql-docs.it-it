---
title: Tipo di proprietà (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Type
- Field20::Type
helpviewer_keywords:
- Type property [ADO]
ms.assetid: 8a4c079f-9f4f-4545-801d-85983b8db71e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33bf90a2ac3101cbf582449f2b5495f110a37a62
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35282570"
---
# <a name="type-property-ado"></a>Proprietà di tipo (ADO)
Indica il tipo di dati o di tipo operativo di un [parametro](../../../ado/reference/ado-api/parameter-object.md), [campo](../../../ado/reference/ado-api/field-object.md), o [proprietà](../../../ado/reference/ado-api/property-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un [DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md) valore.  
  
## <a name="remarks"></a>Remarks  
 Per **parametro** oggetti, il **tipo** proprietà è di lettura/scrittura. Per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md), **tipo** è di lettura/scrittura solo dopo il [ Valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà per il **campo** è stato specificato e il provider di dati è stato aggiunto il nuovo **campo** chiamando il [aggiornare](../../../ado/reference/ado-api/update-method.md)metodo il **campi** insieme.  
  
 Per tutti gli altri oggetti, il **tipo** proprietà è di sola lettura.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Oggetto Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà Type (campo) (VB)](../../../ado/reference/ado-api/type-property-example-field-vb.md)   
 [Esempio di proprietà Type (proprietà) (VC + +)](../../../ado/reference/ado-api/type-property-example-property-vc.md)   
 [Proprietà RecordType (ADO)](../../../ado/reference/ado-api/recordtype-property-ado.md)   
 [Proprietà Type (flusso ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)
