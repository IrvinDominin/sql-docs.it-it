---
title: Riepilogo dei gestori di eventi ADO | Documenti Microsoft
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
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9e182d5b1e1b8755250cbf620ac102a7eacde0f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="ado-connection-and-recordset-events"></a>Connessione di ADO e gli eventi di Recordset
Due oggetti ADO possono generare eventi: il [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto e [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto. Il **ConnectionEvent** famiglia relativa alle operazioni sul **connessione** oggetto e **RecordsetEvent** famiglia relativa alle operazioni sul  **Recordset** oggetto.

-   **Gli eventi di connessione**: vengono generati quando inizia una transazione su una connessione, viene eseguito il commit o nuovamente; quando viene eseguito il rollback un [comando](../../../ado/reference/ado-api/command-object-ado.md) esegue; quando un avviso si verifica durante un **evento connessione**operazione. o quando un **connessione** inizia o termina.

-   **Eventi recordset**: vengono generati intorno a operazioni di recupero asincrono, nonché quando si scorrono le righe di un **Recordset** oggetto, modificare un campo in una riga di un **Recordset**, modifica una riga in un **Recordset**, aprire un **Recordset** con un cursore sul lato server, chiudere un **Recordset**, o di apportare qualsiasi modifica nel  **Recordset**.

 La tabella seguente sono riepilogati gli eventi e le relative descrizioni.

|ConnectionEvent|Description|
|---------------------|-----------------|
|[BeginTransComplete, CommitTransComplete, RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Gestione delle transazioni** : notifica che è stata avviata la transazione corrente sulla connessione, il commit o rollback.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, Disconnect](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Gestione delle connessioni** : notifica che è possibile avviare la connessione corrente, è stata avviata o è stata terminata.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Gestione dell'esecuzione di comandi** : notifica che l'esecuzione del comando corrente per la connessione verrà avviato o è stata terminata.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Informativo** : notifica di informazioni aggiuntive relative all'operazione corrente.|

|RecordsetEvent|Description|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Stato di recupero** : notifica dello stato di avanzamento di un'operazione di recupero di dati o che l'operazione di recupero è stata completata. Questi eventi sono disponibili solo se il **Recordset** è stato aperto tramite un cursore sul lato client.|
|[WillChangeField, FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Gestione dei cambiamenti di campo** : notifica di modifica, il valore del campo corrente o è stato modificato.|
|[WillMove, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Gestione dello spostamento** : notifica che la riga corrente di posizionare in un **Recordset** verrà modificato, è stato modificato o ha raggiunto la fine del **Recordset**.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Gestione delle modifiche di riga** : notifica che si è nella riga corrente del **Recordset** verrà modificato o è stato modificato.|
|[WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Gestione dei cambiamenti di recordset** : notifica che si è nella classe corrente **Recordset** verrà modificato o è stato modificato.|

## <a name="see-also"></a>Vedere anche
 [Creazione di istanze di ADO evento dal linguaggio](../../../ado/guide/data/ado-event-instantiation-by-language.md) [eventi ADO](../../../ado/reference/ado-api/ado-events.md) [parametri evento](../../../ado/guide/data/event-parameters.md) [dell'interazione tra i gestori eventi](../../../ado/guide/data/how-event-handlers-work-together.md) [tipi di eventi](../../../ado/guide/data/types-of-events.md)
