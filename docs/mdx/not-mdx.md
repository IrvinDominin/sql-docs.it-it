---
title: NON (MDX) | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NOT
dev_langs:
- kbMDX
helpviewer_keywords:
- NOT operator [MDX]
ms.assetid: c11bd3b0-54b3-4a6d-babc-6067722194db
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b6da446a370065c3782ac3c76445988d266b60d7
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="not-mdx"></a>NOT (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Esegue la negazione logica di un'espressione numerica.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
NOT Expression1  
```  
  
#### <a name="parameters"></a>Parametri  
 *Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un valore numerico.  
  
## <a name="return-value"></a>Valore restituito  
 Un valore booleano che restituisce **false** se l'argomento restituisce **true**; in caso contrario, **true**.  
  
## <a name="remarks"></a>Osservazioni  
 Il **non** gestisce l'espressione come un valore booleano (zero, 0, come **false**; in caso contrario, **true**) prima di eseguire la negazione logica. Nella tabella seguente viene illustrato come la **non** operatore esegue la negazione logica.  
  
|*Expression1*|Valore restituito|  
|-------------------|------------------|  
|**true**|**false**|  
|**false**|**true**|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento agli operatori MDX &#40; MDX &#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
