---
title: Report di valutazione (DB2ToSQL) | Documenti Microsoft
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-db2
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 9e13eba0-e3cf-4205-974f-c00f982061de
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f33d360727df0ce9af5498ffaf26d049af8bf462
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="assessment-report-db2tosql"></a>Report di valutazione (DB2ToSQL)
Nella finestra di Report di valutazione vengono visualizzati i risultati della conversione di oggetti di database per [!INCLUDE[tsql](../../includes/tsql_md.md)] , sintassi e possibile stimare la complessità e costi dei progetti di migrazione.  
  
Per accedere al Report di valutazione, selezionare gli oggetti da convertire in Visualizzatore metadati di origine, fare doppio clic su **schemi** o **sinonimi**, quindi selezionare **crea Report**.  
  
## <a name="options"></a>Opzioni  
  
|||  
|-|-|  
|Nome|Definizione|  
|**Statistiche di conversione**|Mostra le statistiche di conversione dal tipo di istruzione. Questo riquadro è visualizzato quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.|  
|**Oggetti in base a categorie**|Mostra il numero di oggetti in base alla categoria. In questo riquadro è visibile solo quando un oggetto di gruppo, ad esempio uno schema, o un oggetto senza codice è stato selezionato nel riquadro a sinistra.|  
|**Statistiche**|Mostra le statistiche di conversione per l'oggetto selezionato. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra. Potrebbe essere necessario espandere **statistiche**, disponibile immediatamente sopra la **origine** riquadro per visualizzare questo riquadro.|  
|**Origine**|Viene illustrato il codice di DB2 per l'oggetto selezionato ed evidenzia il codice che non è stato convertito in [!INCLUDE[tsql](../../includes/tsql_md.md)]. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.<br /><br />Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.|  
|**Destinazione**|Mostra la conversione del risultante [!INCLUDE[tsql](../../includes/tsql_md.md)] codice per l'oggetto selezionato e i messaggi di errore per il codice che non è stato convertito. In questo riquadro è visibile solo quando è selezionato un singolo oggetto con il codice nel riquadro a sinistra.<br /><br />Fare clic sui numeri di riga per impostare o cancellare i segnalibri. Utilizzare i pulsanti nella parte superiore del riquadro per esplorare il codice.|  
|**Riquadro messaggi**|Viene illustrato l'errori, avvisi e messaggi informativi che sono stati generati durante la creazione di report di valutazione. I messaggi vengono raggruppati per numero. Per visualizzare il codice che ha causato l'errore, fare clic su **errori**, **avvisi**, o **Info**, espandere la categoria di messaggi e quindi fare clic su un messaggio.|  
  
