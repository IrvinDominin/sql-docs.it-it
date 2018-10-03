---
title: Categoria di eventi Database | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2c68c5f735c494776c9e798b3786c6dcda048f7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078611"
---
# <a name="database-event-category"></a>Categoria di eventi Database
  La categoria di eventi **Database** include classi di evento per il monitoraggio del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
  
|Argomento|Description|  
|-----------|-----------------|  
|[Classe di evento Data File Auto Grow](data-file-auto-grow-event-class.md)|Indica che le dimensioni del file di dati sono aumentate automaticamente. Questo evento non viene generato se le dimensioni del file vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Data File Auto Shrink](data-file-auto-shrink-event-class.md)|Indica che il file di dati è stato compattato.|  
|[Classe di evento Database Mirroring Connection](database-mirroring-connection-event-class.md)|Evento generato per indicare lo stato di una connessione di trasporto per il mirroring del database.|  
|[Classe di evento Database Mirroring State Change](database-mirroring-state-change-event-class.md)|Indica quando lo stato di un database con mirroring cambia.|  
|[Classe di evento Database Suspect Data Page](database-suspect-data-page-event-class.md)|Indica quando una pagina viene aggiunta alla tabella **suspect_pages** nel database **msdb** .|  
|[Classe di evento Log File Auto Grow](log-file-auto-grow-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono incrementate in modo esplicito tramite ALTER DATABASE.|  
|[Classe di evento Log File Auto Shrink](log-file-auto-shrink-event-class.md)|Indica che le dimensioni del file di log sono aumentate automaticamente. L'evento non viene generato se le dimensioni del file di log vengono ridotte in modo esplicito tramite ALTER DATABASE.|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)  
  
  
