---
title: "Utilizzo di AddNew nell'immediato e la modalità Batch | Documenti Microsoft"
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
- AddNew method [ADO]
- ADO, editing data
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f22ae3e595c68b52e7eca449557e647c3bedae78
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Utilizzo di AddNew nell'immediato e la modalità Batch
Il comportamento del **AddNew** metodo dipende dalla modalità di aggiornamento del **Recordset** oggetto e se si passa il *elenco campi* e *valori*argomenti.  
  
 In modalità di aggiornamento immediato (in cui il provider scrive le modifiche all'origine dati sottostante non appena viene chiamato il **aggiornare** metodo), la chiamata di **AddNew** metodo senza argomenti imposta la  **EditMode** proprietà **adEditAdd.** Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. La chiamata di **aggiornamento** metodo invia il nuovo record nel database e reimposta il **EditMode** proprietà **adEditNone.** Se si passa il *elenco campi* e *valori* argomenti, ADO invia immediatamente il nuovo record per il database (non **aggiornamento** è necessario chiamare); il **EditMode**  valore proprietà non viene modificato (**adEditNone**).  
  
 In modalità di aggiornamento batch, la chiamata di **AddNew** metodo senza argomenti imposta la **EditMode** proprietà **adEditAdd**. Il provider memorizza nella cache qualsiasi valore di campo modificato in locale. La chiamata di **aggiornamento** metodo aggiunge il nuovo record corrente **Recordset** e reimposta il **EditMode** proprietà **adEditNone**, ma il provider invia le modifiche al database sottostante fino a quando non si chiama il **UpdateBatch** metodo. Se si passa il *elenco campi* e *valori* argomenti, ADO invia il nuovo record per il provider di archiviazione in una cache, è necessario chiamare il **UpdateBatch** per registrare il nuovo (metodo) registrare il database sottostante. Per ulteriori informazioni su **aggiornamento** e **UpdateBatch**, vedere [aggiornamento e il mantenimento dati](../../../ado/guide/data/updating-and-persisting-data.md).
