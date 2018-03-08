---
title: Tipi di blocchi | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AdLockBatchOptimistic [ADO]
- AdLockReadOnly [ADO]
- AdLockUnspecified [ADO]
- locks [ADO], types
- AdLockOptimistic [ADO]
- AdLockPessimistic [ADO]
ms.assetid: 12a978c0-b8a0-4ef0-87f0-a43c13659272
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9bec4523ea458998ff19481de467cc6493d03ed2
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="types-of-locks"></a>Tipi di blocchi
## <a name="adlockbatchoptimistic"></a>adLockBatchOptimistic  
 Indica gli aggiornamenti batch ottimistica. Obbligatorio per la modalità di aggiornamento batch.  
  
 Molte applicazioni di recuperano un numero di righe in una sola volta e quindi è necessario eseguire aggiornamenti coordinati che includono l'intero set di righe inserite, aggiornate o eliminate. Con i cursori di batch, un solo round trip al server è necessario, migliorando le prestazioni dell'aggiornamento e ridurre il traffico di rete. Utilizza una libreria di cursori di batch, è possibile creare un cursore statico e quindi disconnettersi dall'origine dati. A questo punto è possibile apportare modifiche alle righe e successivamente ristabilire la connessione e inviare le modifiche all'origine dati in un batch.  
  
## <a name="adlockoptimistic"></a>adLockOptimistic  
 Indica che il provider Usa blocco ottimistico: blocco dei record solo quando si chiama il **aggiornamento** metodo. Ciò significa che è probabile che un altro utente può modificare i dati tra il momento in cui si modifica il record e quando si chiama **aggiornamento**, che consente di creare conflitti. Utilizzare questo tipo di blocco nelle situazioni in cui la probabilità di un conflitto è insufficiente o in cui possono essere risolti immediatamente conflitti.  
  
## <a name="adlockpessimistic"></a>adLockPessimistic  
 Indica il blocco pessimistico, un record. Il provider non sia necessaria per garantire la corretta modifica dei record, in genere di blocco dei record nell'origine dati prima della modifica. Naturalmente, ciò significa che i record sono disponibili ad altri utenti dopo l'inizio di modifica, fino al rilascio del blocco chiamando **Update.** Utilizzare questo tipo di blocco in un sistema in cui ci si può permettere di modifiche simultanee ai dati, ad esempio in un sistema di prenotazione.  
  
## <a name="adlockreadonly"></a>adLockReadOnly  
 Indica i record di sola lettura. È possibile modificare i dati. Un blocco di sola lettura è il tipo di blocco "veloce" perché non richiede il server per mantenere un blocco di record.  
  
## <a name="adlockunspecified"></a>adLockUnspecified  
 Non specifica un tipo di blocco.
