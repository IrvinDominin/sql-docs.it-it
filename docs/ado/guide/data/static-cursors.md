---
title: I cursori statici | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a837ce0d285f24772be5a88e29c0929e398e6582
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="static-cursors"></a>Cursori statici
Un cursore statico Visualizza sempre il risultato impostato com'era quando il cursore è stato aperto. A seconda di implementazione, cursori statici sono di sola lettura o lettura/scrittura e consentono lo scorrimento in avanti e indietro. In genere un cursore statico non rileva le modifiche apportate per l'appartenenza, ordine o valori di set di risultati dopo l'apertura del cursore. I cursori statici possono rilevare i propri aggiornamenti, eliminazioni e inserimenti, anche non è necessario eseguire questa operazione.  
  
 I cursori statici rilevano mai altri Aggiorna, Elimina e inserisce. Si supponga, ad esempio, un cursore statico recupera una riga e un'altra applicazione, quindi aggiorna tale riga. Se l'applicazione recupera nuovamente la riga dalla posizione del cursore statico, i valori rilevati sono identiche, nonostante le modifiche apportate da altre applicazioni. Sono supportati tutti i tipi di scorrimento, ma i provider potrebbero non supportino i segnalibri.  
  
 Se l'applicazione non è necessario rilevare i dati vengono modificati e richiede lo scorrimento, il cursore statico è la scelta migliore. Utilizzare il **adOpenStatic CursorTypeEnum** per indicare che si desidera utilizzare un cursore statico in ADO.  
  
## <a name="see-also"></a>Vedere anche  
 [Cursori forward-Only](../../../ado/guide/data/forward-only-cursors.md)   
 [Cursori keyset](../../../ado/guide/data/keyset-cursors.md)   
 [Cursori dinamici](../../../ado/guide/data/dynamic-cursors.md)
