---
title: "Nome proprietà (ADO) | Documenti Microsoft"
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
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eac3504e262f52700351c9d4313ed39d9723c844
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="name-property-ado"></a>Nome proprietà (ADO)
Indica il nome di un oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Restituisce o imposta un **stringa** valore che indica il nome di un oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **nome** proprietà per assegnare un nome a o recuperare il nome di un **comando**, **proprietà**, **campo**, o **parametro**  oggetto.  
  
 Il valore è di lettura/scrittura in un **comando** oggetto e di sola lettura su un **proprietà** oggetto.  
  
 Per un **campo** oggetto **nome** è di sola lettura. Tuttavia, per i nuovi **campo** gli oggetti che sono stati accodati per il [campi](../../../ado/reference/ado-api/fields-collection-ado.md) raccolta di un [Record](../../../ado/reference/ado-api/record-object-ado.md), **nome** è lettura/scrittura solo dopo che il [valore](../../../ado/reference/ado-api/value-property-ado.md) proprietà per il **campo** è stato specificato e il provider di dati è stato aggiunto il nuovo **campo** chiamando il [ Aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo il **campi** insieme.  
  
 Per **parametro** oggetti non ancora aggiunti al [parametri](../../../ado/reference/ado-api/parameters-collection-ado.md) raccolta, il **nome** proprietà è di lettura/scrittura. Per accodati **parametro** oggetti e tutti gli altri oggetti, il **nome** proprietà è di sola lettura. Nome non deve essere univoco all'interno di una raccolta.  
  
 È possibile recuperare il **nome** proprietà di un oggetto da un riferimento ordinale, dopo il quale è possibile fare riferimento all'oggetto direttamente per nome. Ad esempio, se `rstMain.Properties(20).Name` produce `Updatability`, successivamente è possibile fare riferimento a questa proprietà come `rstMain.Properties("Updatability")`.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto Field](../../../ado/reference/ado-api/field-object.md)|  
|[Oggetto Parameter](../../../ado/reference/ado-api/parameter-object.md)|[Oggetto Property (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà di nome (VB) e gli attributi](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Esempio di proprietà di nome (VC + +) e gli attributi](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
