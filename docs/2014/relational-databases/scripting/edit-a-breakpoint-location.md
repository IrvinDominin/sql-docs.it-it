---
title: Modificare la posizione di un punto di interruzione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.location.file
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ffa9cad3ef994f3306a485d5a911f2e03eff0f2a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211441"
---
# <a name="edit-a-breakpoint-location"></a>Modifica della posizione di un punto di interruzione
  La posizione del punto di interruzione specifica la riga e il carattere in cui si trova il punto di interruzione in un file di script [!INCLUDE[tsql](../../includes/tsql-md.md)] . È possibile modificare la posizione del punto di interruzione per spostare il punto di interruzione in un'altra posizione nello script o in uno script diverso.  
  
## <a name="editing-a-location"></a>Modifica di una posizione  
 Quando si modifica la posizione di un punto di interruzione, il punto di interruzione viene spostato nella nuova posizione, insieme a tutte le proprietà esistenti, ad esempio un numero di passaggi o una condizione.  
  
#### <a name="to-edit-a-breakpoint-location"></a>Per modificare la posizione di un punto di interruzione  
  
1.  Nella finestra dell'editor fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Posizione** dal menu di scelta rapida.  
  
     oppure  
  
     Nella finestra **Punti di interruzione** fare clic con il pulsante destro del mouse sul glifo del punto di interruzione e quindi scegliere **Posizione** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Punto di interruzione del file** modificare **File** per specificare un nuovo file, **Riga** per specificare una nuova riga o **Carattere** per specificare una nuova posizione all'interno della riga. Se il nuovo file specificato è già aperto in una finestra dell'editor di query, il punto di interruzione viene spostato in tale finestra. Se il file non è aperto, viene aperta una nuova finestra dell'editor, il file viene caricato e il punto di interruzione viene spostato nella nuova posizione.  
  
     L'opzione **Il codice sorgente può essere diverso dalla versione originale** non ha effetto nel caso di debug di [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica di un numero di passaggi](specify-a-hit-count.md)   
 [Impostazione di un'azione del punto di interruzione](specify-a-breakpoint-action.md)   
 [Impostare una condizione del punto di interruzione](specify-a-breakpoint-condition.md)   
 [Specificare un filtro per un punto di interruzione](specify-a-breakpoint-filter.md)  
  
  
