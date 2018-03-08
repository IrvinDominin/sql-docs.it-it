---
title: I cursori scorrevoli e isolamento delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- scrollable cursors [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: f0216f4a-46e3-48ae-be0a-e2625e8403a6
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6c9e38f4287a8832d8e794940093ce696ac0eaf7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="scrollable-cursors-and-transaction-isolation"></a>I cursori scorrevoli e isolamento delle transazioni
Nella tabella seguente elenca i fattori che controllano la visibilità delle modifiche.  
  
|Modifiche apportate da:|Visibilità dipende da:|  
|----------------------|----------------------------|  
|Cursore|Tipo di cursore, implementazione dei cursori|  
|Altre istruzioni nella stessa transazione|Tipo di cursore|  
|Istruzioni in altre transazioni|Tipo di cursore, il livello di isolamento delle transazioni|  
  
 Questi fattori vengono visualizzati nella figura seguente.  
  
 ![Fattori che controllano la visibilità delle modifiche](../../../odbc/reference/develop-app/media/pr23.gif "pr23")  
  
 Nella tabella seguente sono riepilogate le capacità di ogni tipo di cursore per rilevare le modifiche apportate da se stesso, da altre operazioni nella relativa transazione e da altre transazioni. La visibilità delle modifiche di quest'ultime varia a seconda del tipo di cursore e il livello di isolamento della transazione contenente il cursore.  
  
|Cursore type\action|Self|Proprietario<br /><br /> TXN|Othr<br /><br /> TXN<br /><br /> (RU[a])|Othr<br /><br /> TXN<br /><br /> (RC[a])|Othr<br /><br /> TXN<br /><br /> (RR[a])|Othr<br /><br /> TXN<br /><br /> (S[a])|  
|-------------------------|----------|-----------------|----------------------------------|----------------------------------|----------------------------------|---------------------------------|  
|Statico|||||||  
|Insert|Ad esempio [b]|no|no|no|no|no|  
|Update|Ad esempio [b]|no|no|no|no|no|  
|DELETE|Ad esempio [b]|no|no|no|no|no|  
|Gestito da keyset|||||||  
|Insert|Ad esempio [b]|no|no|no|no|no|  
|Update|Sì|Sì|Sì|Sì|no|no|  
|DELETE|Ad esempio [b]|Sì|Sì|Sì|no|no|  
|Dynamic|||||||  
|Insert|Sì|Sì|Sì|Sì|Sì|no|  
|Update|Sì|Sì|Sì|Sì|no|no|  
|DELETE|Sì|Sì|Sì|Sì|no|no|  
  
 [a] le lettere tra parentesi indicano il livello di isolamento della transazione contenente il cursore. il livello di isolamento della transazione (in cui è stata effettuata la modifica) è irrilevante.  
  
 RU: Read uncommitted  
  
 RC: Read commit  
  
 RR: Lettura ripetibile  
  
 S: serializzabile  
  
 [b] dipende dalla modalità di implementazione del cursore. Se il cursore è possibile rilevare le modifiche viene segnalato tramite l'opzione SQL_STATIC_SENSITIVITY in **SQLGetInfo**.
