---
title: Modificare la posizione di un punto di interruzione | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.breakpt.location.file
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17e1810114e209c8012792b1e67502c3638afa3a
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="edit-a-breakpoint-location"></a>Modifica della posizione di un punto di interruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] La posizione del punto di interruzione specifica la riga e il carattere in cui si trova il punto di interruzione in un file di script [!INCLUDE[tsql](../../includes/tsql-md.md)]. È possibile modificare la posizione del punto di interruzione per spostare il punto di interruzione in un'altra posizione nello script o in uno script diverso.  
  
## <a name="editing-a-location"></a>Modifica di una posizione  
 Quando si modifica la posizione di un punto di interruzione, il punto di interruzione viene spostato nella nuova posizione, insieme a tutte le proprietà esistenti, ad esempio un numero di passaggi o una condizione.  
  
#### <a name="to-edit-a-breakpoint-location"></a>Per modificare la posizione di un punto di interruzione  
  
1.  Nella finestra dell'editor fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Posizione** dal menu di scelta rapida.  
  
     oppure  
  
     Nella finestra **Punti di interruzione** fare clic con il pulsante destro del mouse sul glifo del punto di interruzione e quindi scegliere **Posizione** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Punto di interruzione del file** modificare **File** per specificare un nuovo file, **Riga** per specificare una nuova riga o **Carattere** per specificare una nuova posizione all'interno della riga. Se il nuovo file specificato è già aperto in una finestra dell'editor di query, il punto di interruzione viene spostato in tale finestra. Se il file non è aperto, viene aperta una nuova finestra dell'editor, il file viene caricato e il punto di interruzione viene spostato nella nuova posizione.  
  
     L'opzione **Il codice sorgente può essere diverso dalla versione originale** non ha effetto nel caso di debug di [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Specifica di un numero di passaggi](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Impostazione di un'azione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-action.md)   
 [Impostare una condizione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Specificare un filtro per un punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-filter.md)  
  
  
