---
title: Gli attributi di proprietà (ADO) | Documenti Microsoft
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
- Connection15::Attributes
- Field20::Attributes
- _Parameter::Attributes
helpviewer_keywords:
- Attributes property [ADO]
ms.assetid: acc15d40-68a6-4ba9-85bd-12d331aecaa6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d79fd70f69ca609e2fbf38abe58da158c48f8306
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="attributes-property-ado"></a>Proprietà Attributes (ADO)
Indica una o più caratteristiche di un oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **lungo** valore.  
  
 Per un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto, il **attributi** proprietà è di lettura/scrittura e il relativo valore può essere la somma di uno o più [XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md) valori. Il valore predefinito è zero (0).  
  
 Per un [parametro](../../../ado/reference/ado-api/parameter-object.md) oggetto, il **attributi** proprietà è di lettura/scrittura e il relativo valore può essere la somma di una o più [ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md) valori. Il valore predefinito è **adParamSigned**.  
  
 Per un [campo](../../../ado/reference/ado-api/field-object.md) oggetto, il **attributi** proprietà può essere la somma di uno o più [FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md) valori. È in genere di sola lettura. Tuttavia, per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md), **attributi** è di sola lettura/scrittura Dopo il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà per il **campo** è stato specificato e il nuovo **campo** è stato aggiunto dal provider di dati chiamando il [ Aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo il **campi** insieme.  
  
 Per un [proprietà](../../../ado/reference/ado-api/property-object-ado.md) oggetto, il **attributi** proprietà è di sola lettura e il relativo valore può essere la somma di una o più [PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md) valori.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **attributi** proprietà per impostare o restituire le caratteristiche di **connessione** oggetti, **parametro** oggetti, **campo** oggetti, o **Proprietà** oggetti.  
  
 Quando si impostano più attributi, è possibile sommare le costanti appropriate. Se si imposta il valore della proprietà a una somma tra cui costanti incompatibili, si verifica un errore.  
  
> [!NOTE]
>  **Utilizzo del servizio dati remoti** questa proprietà non è disponibile in un client-side **connessione** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|  
|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Oggetto Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà di nome (VB) e gli attributi](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Esempio di proprietà di nome (VC + +) e gli attributi](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
 [Metodo AppendChunk (ADO)](../../../ado/reference/ado-api/appendchunk-method-ado.md)   
 [BeginTrans, CommitTrans e RollbackTrans metodi (ADO)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)   
 [Metodo GetChunk (ADO)](../../../ado/reference/ado-api/getchunk-method-ado.md)
