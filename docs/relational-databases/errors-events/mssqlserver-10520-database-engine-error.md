---
title: MSSQLSERVER_10520 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10520 (Database Engine error)
ms.assetid: cc8799f1-5b90-4248-b209-e1d5087f9529
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3da0820c4c9ae4c09e7efaea09bf4b3d75657ad5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver10520"></a>MSSQLSERVER_10520
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|10520|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|PG_PARAM_NOT_ALLOWED|  
|Testo del messaggio|Impossibile creare la guida di piano '%.*ls' perché @type è stato specificato come '%ls' ed è stato specificato un valore non NULL per il parametro '%ls'. Questo tipo richiede un valore NULL per il parametro. Specificare NULL per il parametro oppure impostare un tipo che consenta un valore non NULL per il parametro.|  
  
## <a name="explanation"></a>Spiegazione  
Il tipo indicato in @type richiede un valore NULL per il parametro specificato, ma è stato fornito un valore non NULL.  
  
## <a name="user-action"></a>Azione dell'utente  
Specificare NULL per il parametro oppure impostare un tipo che consenta un valore non NULL per il parametro.  
  
## <a name="see-also"></a>Vedere anche  
[sp_create_plan_guide &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[Guide di piano](~/relational-databases/performance/plan-guides.md)  
  
