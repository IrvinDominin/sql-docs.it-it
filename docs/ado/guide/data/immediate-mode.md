---
title: "Modalità immediata | Documenti Microsoft"
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
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f737d3b05e27eff7aae0aa95ee336a054c38f29f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="immediate-mode"></a>Modalità immediata
Modalità immediata è attiva quando il **LockType** è impostata su **adLockOptimistic** o **adLockPessimistic**. In questa modalità, le modifiche apportate a un record vengono propagate all'origine dati non appena si dichiara il lavoro in una riga completa chiamando il **aggiornamento** metodo.  
  
## <a name="calling-update"></a>La chiamata di aggiornamento  
 Se si sposta dal record si aggiunge o modifica prima di chiamare il **aggiornamento** metodo, verrà automaticamente chiamato **aggiornamento** per salvare le modifiche. È necessario chiamare il **CancelUpdate** metodo prima dello spostamento se si desidera annullare le modifiche apportate al record corrente oppure eliminare il record appena aggiunto.  
  
 Il record corrente rimane invariato dopo la chiamata di **aggiornamento** metodo.  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Utilizzare il **CancelUpdate** metodo per annullare le modifiche apportate alla riga corrente o per eliminare una riga appena aggiunta. Non è possibile annullare le modifiche apportate alla riga corrente o a una nuova riga dopo la chiamata di **aggiornamento** (metodo), a meno che le modifiche siano parte di una transazione di cui è possibile eseguire il rollback con il **RollbackTrans** metodo o in parte un aggiornamento batch. Nel caso di un aggiornamento batch, è possibile annullare il **aggiornare** con il **CancelUpdate** o **CancelBatch** metodo.  
  
 Se si aggiunge una nuova riga quando si chiama il **CancelUpdate** (metodo), la riga corrente diventa la riga corrente prima di **AddNew** chiamare.  
  
 Se non si hanno modificato la riga corrente o aggiunta una nuova riga, la chiamata di **CancelUpdate** metodo genera un errore.
