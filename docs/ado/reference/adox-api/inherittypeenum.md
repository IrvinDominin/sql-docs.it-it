---
title: InheritTypeEnum | Documenti Microsoft
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
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b3a167913b23005cf2b78e4acc682ec2af75157c
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35286650"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
Specifica il modo in cui gli oggetti ereditano le autorizzazioni impostate tramite [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md).  
  
|Costante|valore|Description|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|Sia gli oggetti e gli altri contenitori inclusi nell'oggetto primario ereditano la voce.|  
|**adInheritContainers**|2|Altri contenitori che sono contenuti nell'oggetto primario ereditano la voce.|  
|**adInheritNone**|0|Valore predefinito. Si verifica alcun ereditarietà.|  
|**adInheritNoPropagate**|4|Il **adInheritObjects** e **adInheritContainers** non vengono propagati a una voce ereditata.|  
|**adInheritObjects**|1|Gli oggetti non contenitore nel contenitore ereditano le autorizzazioni.|  
  
## <a name="applies-to"></a>Si applica a  
 [Metodo SetPermissions (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
