---
title: Filtrare gli eventi in una traccia (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], traces
- traces [SQL Server], filters
- traces [SQL Server], events
ms.assetid: 0fd63573-3b35-4f67-9e1e-ed9aabee11a8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b4273d1af6f4f740c7b6527359957abf447cc2a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47765399"
---
# <a name="filter-events-in-a-trace-sql-server-profiler"></a>Filtrare eventi in una traccia (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  I filtri consentono di limitare gli eventi raccolti in una traccia. Se non si imposta un filtro, tutti gli eventi delle classi di evento selezionate vengono restituiti nell'output di traccia. L'impostazione di un filtro per una traccia non è obbligatoria. Un filtro consente, tuttavia, di ridurre l'overhead che si verifica durante una traccia,  
  
 Per aggiungere filtri alle definizioni della traccia, usare la scheda **Selezione eventi** della finestra di dialogo **Proprietà traccia** o **Proprietà modello di traccia** .  
  
### <a name="to-filter-events-in-a-trace"></a>Per filtrare gli eventi in una traccia  
  
1.  Nella finestra di dialogo **Proprietà traccia** o **Proprietà modello di traccia** fare clic sulla scheda **Selezione eventi** .  
  
     La scheda **Selezione eventi** contiene un controllo griglia, ovvero una tabella che include tutte le classi di evento tracciabili. La tabella contiene una riga per ogni classe di evento. Le classi di evento possono differire leggermente a seconda del tipo e della versione del server cui si è connessi. Le classi di eventi sono identificate nella colonna **Eventi**della griglia e sono raggruppate per categoria di eventi. Nelle altre colonne sono elencate le colonne di dati che possono essere restituite per ogni classe di evento.  
  
2.  Fare clic su **Filtri colonne**.  
  
     Viene visualizzata la finestra di dialogo **Modifica filtro**. Nella finestra di dialogo **Modifica filtro**è disponibile un elenco di operatori di confronto che consentono di filtrare gli eventi in una traccia.  
  
3.  Per applicare un filtro, fare clic sull'operatore di confronto e immettere il valore da utilizzare per il filtro.  
  
4.  Fare clic su **OK**.  
  
 **Considerazioni:**  
  
-   Se si impostano condizioni di filtro sulle colonne di dati **StartTime** ed **EndTime** della scheda Selezione eventi, assicurarsi che:  
  
    -   Il formato della data immessa sia uguale al seguente: `YYYY/MM/DD HH:mm:sec`.  
  
         oppure  
  
    -   L'opzione**Visualizza valori di data e ora in base alle impostazioni internazionali** sia selezionata nella finestra di dialogo **Opzioni generali** . Per visualizzare la finestra di dialogo **Opzioni generali** , in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **Tools** menu, click **Option**.  
  
         -e-  
  
    -   La data immessa sia compresa tra 1 gennaio 1753 e 31 dicembre 9999.  
  
-   Se si tracciano eventi con l'utilità **osql** o **sqlcmd** , aggiungere sempre **%** ai filtri nella colonna di dati **TextData** .  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
