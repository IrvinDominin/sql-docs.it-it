---
title: Riproduzione di un cursore (SQL Server Profiler) | Documenti Microsoft
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
- replaying cursors
- traces [SQL Server], replaying
- replaying traces
ms.assetid: 89eadc41-4424-4a1c-ba61-0b52c851cdb1
caps.latest.revision: "22"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 723d3a47736b44dba88a50a2d24ed862c1f30507
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="replay-to-a-cursor-sql-server-profiler"></a>Riprodurre fino a un cursore (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]In questo argomento viene descritto come riprodurre i file di traccia o tabelle cui viene sospeso quando viene raggiunto un cursore utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. La sospensione della riproduzione delle tracce in corrispondenza dei cursori supporta il debug in quanto è possibile interrompere la riproduzione di script di traccia lunghi in segmenti più brevi per eseguirne l'analisi incrementale.  
  
### <a name="to-replay-to-the-cursor"></a>Per eseguire la riproduzione fino al cursore  
  
1.  Aprire il file o la tabella di traccia che si desidera riprodurre. Per altre informazioni, vedere [Aprire un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md) o [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md).  
  
     Verificare che il file o la tabella di traccia aperta contenga le classi di evento necessarie per la riproduzione. Per altre informazioni, vedere [Requisiti per la riproduzione](../../tools/sql-server-profiler/replay-requirements.md).  
  
2.  Nella finestra di traccia fare clic su un evento.  
  
3.  Scegliere **Esegui fino al cursore** dal menu **Riproduci**e quindi connettersi al server di cui si vuole riprodurre la traccia.  
  
4.  Nella finestra di dialogo **Configurazione riproduzione** verificare le impostazioni e quindi fare clic su **OK**.  
  
     La riproduzione viene avviata e quindi sospesa in corrispondenza del primo cursore.  
  
5.  Premere F5 per riprendere la riproduzione della traccia.  
  
6.  Ripetere l'operazione descritta al passaggio 5 fino alla fine della traccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Riprodurre fino a un punto di interruzione &#40; SQL Server Profiler &#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)   
 [Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
