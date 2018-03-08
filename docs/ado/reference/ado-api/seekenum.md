---
title: SeekEnum | Documenti Microsoft
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
- SeekEnum
helpviewer_keywords:
- SeekEnum enumeration [ADO]
ms.assetid: f0ec0c92-8253-47c6-9a14-e5dbccbad219
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 40c15bd116b4e0a7ba13127dc48ec18421b5924b
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="seekenum"></a>SeekEnum
Specifica il tipo di [Seek](../../../ado/reference/ado-api/seek-method.md) da eseguire.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adSeekFirstEQ**|1|Cerca la prima chiave uguale a *KeyValues*.|  
|**adSeekLastEQ**|2|Cerca l'ultima chiave uguale a *KeyValues*.|  
|**adSeekAfterEQ**|4|Cerca una chiave uguale a *KeyValues* o subito dopo dove sarebbero state eseguite corrispondenti.|  
|**adSeekAfter**|8|Cerca una chiave subito dopo la posizione in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
|**adSeekBeforeEQ**|16|Cerca una chiave uguale a *KeyValues*o appena prima dove sarebbero state eseguite corrispondenti.|  
|**adSeekBefore**|32|Cerca immediatamente prima di una chiave in cui una corrispondenza con *KeyValues* sarebbero state eseguite.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.Seek.FIRSTEQ|  
|AdoEnums.Seek.LASTEQ|  
|AdoEnums.Seek.AFTEREQ|  
|AdoEnums.Seek.AFTER|  
|AdoEnums.Seek.BEFOREEQ|  
|AdoEnums.Seek.BEFORE|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo Seek](../../../ado/reference/ado-api/seek-method.md)
