---
title: Report di valutazione (OracleToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 168b7465-a6d6-4329-b46e-fc6c5a3f2d9d
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 1265951a20285556f3b020767d5b5214d879bc30
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="assessment-report-oracletosql"></a>Report di valutazione (OracleToSQL)
Nella finestra di Report di valutazione vengono visualizzati i risultati della conversione di oggetti di database per [!INCLUDE[tsql](../../includes/tsql_md.md)] , sintassi e possibile stimare la complessità e costi dei progetti di migrazione.  
  
Per accedere al Report di valutazione, selezionare gli oggetti da convertire in Visualizzatore metadati di origine, fare doppio clic su **schemi** o **sinonimi**, quindi selezionare **crea Report**.  
  
## <a name="options"></a>Opzioni  
  
|||  
|-|-|  
|Nome|Definizione|  
|**Statistiche di conversione**|Mostra le statistiche di conversione dal tipo di istruzione. Questo riquadro è visualizzato quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.|  
|**Oggetti in base a categorie**|Mostra il numero di oggetti in base alla categoria. In questo riquadro è visibile solo quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.|  
|**Statistiche**|Mostra le statistiche di conversione per l'oggetto selezionato. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra. Potrebbe essere necessario espandere **statistiche**, disponibile immediatamente sopra la **origine** riquadro per visualizzare questo riquadro.|  
|**Origine**|Viene illustrato il codice di Oracle per l'oggetto selezionato ed evidenzia il codice che non è stato convertito in [!INCLUDE[tsql](../../includes/tsql_md.md)]. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.<br /><br />Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.|  
|**Destinazione**|Mostra la conversione del risultante [!INCLUDE[tsql](../../includes/tsql_md.md)] codice per l'oggetto selezionato e i messaggi di errore per il codice che non è stato convertito. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.<br /><br />Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.|  
|**Riquadro messaggi**|Viene illustrato l'errori, avvisi e messaggi informativi che sono stati generati durante la creazione di report di valutazione. I messaggi vengono raggruppati per numero. Per visualizzare il codice che ha causato l'errore, fare clic su **errori**, **avvisi**, o **Info**, espandere la categoria di messaggi e quindi fare clic su un messaggio.|  
  
