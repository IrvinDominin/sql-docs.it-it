---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 80b892c4627af5fd2db098c4e815f315d0bb85e1
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41365"></a>MSSQLSERVER_41365
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|41365|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|HK_MERGE_SCHEDULE_ERROR|  
|Testo del messaggio|La richiesta di unione per l'intervallo della transazioni [%ld, %ld) sul database %.*ls non è stata pianificata. I file del checkpoint che rappresentano l'intervallo non sono disponibili per unione o parte di un'unione in corso.|  
  
## <a name="explanation"></a>Spiegazione  
I file del checkpoint che rappresentano l'intervallo non sono disponibili per unione o parte di un'unione in corso.  
  
## <a name="user-action"></a>Azione dell'utente  
Fornire un migliore intervallo di transazioni per merge/attesa prima di eseguire la stessa richiesta. Per altre informazioni, vedere [OLTP in memoria &#40;ottimizzazione in memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Vedere anche  
[OLTP in memoria &#40;ottimizzazione per la memoria&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
