---
title: Riproduzione di un punto di interruzione (SQL Server Profiler) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: sql-server-profiler
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoints [SQL Server]
- traces [SQL Server], replaying
ms.assetid: 3caf751e-df3b-40c7-b5e8-4490ae178e0c
caps.latest.revision: "25"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2383eb3a226beb02c7a2060af5f07b8f97011dcd
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="replay-to-a-breakpoint-sql-server-profiler"></a>Riprodurre fino a un punto di interruzione (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In questo argomento viene illustrato come impostare i punti di interruzione in un file di traccia o una tabella che si desidera riprodurre tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. L'impostazione di punti di interruzione in un file o in una tabella di traccia prima dell'avvio della riproduzione della traccia consente di sospendere la traccia in corrispondenza di eventi specifici. L'utilizzo di punti di interruzione durante la riproduzione di una traccia supporta il debug, in quanto è possibile suddividere la riproduzione di script di traccia lunghi in segmenti più brevi che possono essere analizzati in modo incrementale.  
  
### <a name="to-replay-to-a-breakpoint"></a>Per eseguire la riproduzione fino a un punto di interruzione  
  
1.  Aprire il file o la tabella di traccia che si desidera riprodurre. Per altre informazioni, vedere [Aprire un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) o [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Verificare che il file o la tabella di traccia aperta contenga le classi di evento necessarie per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Nella finestra di traccia fare clic su un evento che si desidera utilizzare come punto di interruzione. Per impostare un punto di interruzione, utilizzare uno dei tre modi seguenti:  
  
    -   Premere F9.  
  
    -   Scegliere **Imposta/Rimuovi punto di interruzione** dal menu **Riproduci**.  
  
    -   Fare clic con il pulsante destro del mouse sull'evento e quindi scegliere **Imposta/Rimuovi punto di interruzione**.  
  
     Accanto all'evento di traccia selezionato verrà visualizzato un pallino rosso, per indicare che si tratta del punto di interruzione della traccia.  
  
     Ripetere il passaggio per impostare più punti di interruzione.  
  
3.  Scegliere **Avvia** dal menu **Riproduci**e quindi connettersi al server in cui si vuole riprodurre la traccia.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
     La riproduzione verrà avviata e quindi verrà sospesa in corrispondenza del punto di interruzione.  
  
5.  Premere F5 per riprendere la riproduzione e passare al punto di interruzione successivo.  
  
6.  Ripetere l'operazione descritta al passaggio 5 fino alla fine della traccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre fino a un cursore &#40; SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)   
 [Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
