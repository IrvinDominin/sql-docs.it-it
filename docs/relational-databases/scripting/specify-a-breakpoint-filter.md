---
title: Specificare un filtro per un punto di interruzione | Microsoft Docs
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
- vs.debug.breakpt.contraints
helpviewer_keywords:
- Transact-SQL debugger, breakpoint filter
ms.assetid: 7bf1dddd-7b0b-4c47-8a7b-28a5569b4fa5
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a209cf9781830ae75a1a726a002ba4077cd8b96d
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="specify-a-breakpoint-filter"></a>Impostazione di un filtro per un punto di interruzione
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Un filtro per un punto di interruzione limita il punto di interruzione in modo che agisca solo su computer o processi e thread del sistema operativo specificati. I filtri per i punti di interruzione vengono in genere utilizzati per il debug di applicazioni parallele.  
  
##  <a name="BKMK_ActionConsiderations"></a> Considerazioni sui filtri  
 I filtri per i punti di interruzione non vengono in genere utilizzati con il debugger [!INCLUDE[tsql](../../includes/tsql-md.md)] perché gli script e le stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] non sono applicazioni parallele.  
  
#### <a name="to-specify-a-breakpoint-filter"></a>Per specificare un filtro per un punto di interruzione  
  
1.  Nella finestra dell'editor fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Filtro** dal menu di scelta rapida.  
  
     oppure  
  
     Nella finestra **Punti di interruzione** fare clic con il pulsante destro del mouse sul glifo del punto di interruzione, quindi scegliere **Filtro** dal menu di scelta rapida.  
  
2.  Nella finestra di dialogo **Filtri punti di interruzione** usare la casella **Filtro** per specificare i computer per nome o i processi e i thread del sistema operativo per nome o numero ID:  
  
    -   **MachineName** è il computer che esegue l'istanza del motore di database.  
  
    -   **ProcessID**e **ProcessName** sono relativi al processo del sistema operativo che esegue l'istanza del motore di database.  
  
    -   **ThreadID** e **ThreadName** sono relativi al thread del sistema operativo che esegue il batch, la procedura o la funzione [!INCLUDE[tsql](../../includes/tsql-md.md)] nell'istanza del motore di database.  
  
3.  Fare clic su **OK** per implementare le modifiche o su **Annulla** per uscire senza applicare le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostare una condizione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-condition.md)   
 [Specifica di un numero di passaggi](../../relational-databases/scripting/specify-a-hit-count.md)   
 [Specificare un'azione del punto di interruzione](../../relational-databases/scripting/specify-a-breakpoint-action.md)  
  
  
