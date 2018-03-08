---
title: "Valore di proprietà (ADO) | Documenti Microsoft"
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
- Field20::Value
- _Parameter::Value
helpviewer_keywords:
- Value property [ADO]
ms.assetid: 48919c74-86d4-462e-99b9-8854ceb8d683
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c48952d89eb58a835ab3372784c0fea468f492af
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="value-property-ado"></a>Valore proprietà (ADO)
Indica il valore assegnato a un [campo](../../../ado/reference/ado-api/field-object.md), [parametro](../../../ado/reference/ado-api/parameter-object.md), o [proprietà](../../../ado/reference/ado-api/property-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **Variant** valore che indica il valore dell'oggetto. Dipende dal valore predefinito di [tipo](../../../ado/reference/ado-api/type-property-ado.md) proprietà.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **valore** proprietà per impostare o restituire dati da **campo** oggetti, per impostare o restituire i valori dei parametri con **parametro** oggetti, oppure per impostare o restituire le impostazioni di proprietà con **Proprietà** oggetti. Se il **valore** proprietà è di lettura/scrittura o sola lettura dipende da numerosi fattori??? vedere gli argomenti corrispondenti per ulteriori informazioni.  
  
 ADO consente l'impostazione e restituzione di dati binari lungo con il **valore** proprietà.  
  
> [!NOTE]
>  Per **parametro** oggetti, le letture ADO la **valore** proprietà una sola volta dal provider. Se un comando contiene un **parametro** cui **valore** proprietà è vuota e si crea un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) dal comando, assicurarsi di chiudere il  **Recordset** prima di recuperare il **valore** proprietà. In caso contrario, per alcuni provider di **valore** proprietà può essere vuota e non deve contenere il valore corretto.  
>   
>  Per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto, il **valore** deve essere impostata prima di qualsiasi altro **campo** le proprietà possono essere specificate. Innanzitutto, un valore specifico per il **valore** proprietà necessario è stata assegnata e [aggiornamento](../../../ado/reference/ado-api/update-method.md) sul **campi** raccolta denominata. Quindi, altre proprietà, ad esempio [tipo](../../../ado/reference/ado-api/type-property-ado.md) o [attributi](../../../ado/reference/ado-api/attributes-property-ado.md) accessibili.  
  
## <a name="applies-to"></a>Si applica a  
  
||||  
|-|-|-|  
|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Oggetto Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di valore della proprietà (Visual Basic)](../../../ado/reference/ado-api/value-property-example-vb.md)   
 [Esempio di proprietà Value (VC++)](../../../ado/reference/ado-api/value-property-example-vc.md)   
