---
title: MSSQLSERVER_360 | Microsoft Docs
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 92bb186e7b9a790d39c5e2ed7df69e77cb618e5f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|360|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|DML_UPDATE_SPARSE_AND_COLSET|  
|Testo del messaggio|L'elenco delle colonne di destinazione di un'istruzione INSERT, UPDATE o MERGE non può includere sia una colonna di tipo sparse sia il set di colonne che contiene tale colonna. Riscrivere l'istruzione in modo che includa la colonna di tipo sparse o il set di colonne, ma non entrambi.|  
  
## <a name="explanation"></a>Spiegazione  
Un set di colonne è una rappresentazione XML non tipizzata che combina alcune colonne di una tabella in un output strutturato. È stato effettuato un tentativo di modificare sia il set di colonne che una colonna inclusa nel set, provocando due riferimenti alla stessa colonna.  
  
## <a name="user-action"></a>Azione dell'utente  
Riscrivere l'istruzione in modo che includa i riferimenti o alla colonna oppure al set di colonne, ma non a entrambi.  
  
