---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a80a7910d387e31efd48e487761a133c9598dfbd
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|3413|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|MARKDB|  
|Testo del messaggio|ID di database %d. Impossibile contrassegnare il database come sospetto. Analisi Getnext per NC su sys.databases.database_id non riuscita. Per identificare la causa e correggere gli eventuali problemi associati, fare riferimento agli errori precedenti nel log degli errori.|  
  
## <a name="explanation"></a>Spiegazione  
Si è verificato un errore imprevisto durante il tentativo di contrassegnare un database utente come SUSPECT nel catalogo. Lo stato SUSPECT non sarà persistente.  
  
## <a name="user-action"></a>Azione dell'utente  
Vedere gli errori precedenti e risolvere il problema.  
  
