---
title: Metodo SetEOS | Documenti Microsoft
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
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 600625802c16c8e6860c462fe369f70eb9c1805c
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="seteos-method"></a>Metodo SetEOS
Imposta la posizione che rappresenta la fine del flusso.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Osservazioni  
 **SetEOS** aggiorna il valore della [fine del flusso](../../../ado/reference/ado-api/eos-property.md) proprietà, rendendo corrente [posizione](../../../ado/reference/ado-api/position-property-ado.md) la fine del flusso. Qualsiasi byte o caratteri che seguono la posizione corrente vengono troncati.  
  
 Poiché [scrivere](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), e [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) non troncano i valori supplementari esistente **flusso** oggetti, è possibile troncare questi byte o caratteri impostando la nuova posizione finale del flusso con **SetEOS**.  
  
> [!CAUTION]
>  Se si imposta **fine del flusso** in una posizione prima della fine del flusso effettiva, si perderanno tutti i dati dopo che il nuovo **fine del flusso** posizione.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
