---
title: Formattazione degli intervalli su un misuratore (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 06eff5cef73ab96d5e694714e98288fad21f4ddc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37212551"
---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>Formattazione di intervalli su un misuratore (Generatore report e SSRS)
  Un intervallo del misuratore è un'area sulla scala del misuratore tramite cui viene indicata un'importante sottosezione dei valori sul misuratore. L'uso di un intervallo del misuratore consente di indicare visivamente quando il valore dell'indicatore di misura rientra in un determinato intervallo di valori. Gli intervalli sono definiti da un valore iniziale e un valore finale.  
  
 È anche possibile utilizzare gli intervalli per definire le diverse sezioni di un misuratore. Su un misuratore con valori compresi tra 0 e 10 è ad esempio possibile definire un intervallo rosso contenente i valori da 0 a 3, un intervallo giallo contenente i valori da 4 a 7 e un intervallo verde contenente i valori da 8 a 10. Se il valore iniziale specificato è maggiore di quello finale specificato, i valori vengono scambiati in modo che quello iniziale diventi quello finale e viceversa.  
  
 È possibile posizionare l'intervallo con una procedura analoga a quella che consente di posizionare gli indicatori di misura su una scala. La posizione dell'intervallo dipende dalle proprietà **Posizione** e **Distanza dalla scala** . Per altre informazioni, vedere [Misuratori &#40;Generatore report e SSRS&#41;](gauges-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di scale su un misuratore &#40;Generatore report e SSRS&#41;](formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formattazione degli indicatori di misura su un misuratore &#40;Generatore report e SSRS&#41;](formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Impostare un valore minimo o massimo su un misuratore &#40;Generatore report e SSRS&#41;](set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiunta di un indicatore di prestazioni chiave al report &#40;Generatore report&#41;](../tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [Misuratori &#40;Generatore report e SSRS&#41;](gauges-report-builder-and-ssrs.md)  
  
  
