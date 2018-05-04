---
title: Posizionamento di recordset | Documenti Microsoft
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
- record positioning [ADO]
- Recordset object [ADO]
- repositioning record [ADO]
- AbsolutePosition property [ADO]
ms.assetid: c8f6fbcb-6675-4133-b37e-430de43949c1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c65a8da00ea92feadc21d0fd1ce3a28967d9a259
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="recordset-positioning"></a>Posizionamento di recordset
Utilizzare il **AbsolutePosition** proprietà per passare a un record, in base alla posizione ordinale di **Recordset** oggetto, o per determinare la posizione ordinale del record corrente. Il provider deve supportare le funzionalità appropriate per questa proprietà sia disponibile.  
  
 **AbsolutePosition** è basato su 1 e uguale a 1 quando il record corrente è il primo record il **Recordset**. Come accennato in precedenza, è possibile ottenere il numero totale di record nel **Recordset** dall'oggetto di **RecordCount** proprietà.  
  
 Quando si imposta la **AbsolutePosition** proprietà, anche se a un record nella cache corrente, ADO ricarica la cache con un nuovo gruppo di record che iniziano con il record specificato. Il **CacheSize** proprietà determina le dimensioni di questo gruppo.  
  
> [!NOTE]
>  Non è consigliabile utilizzare il **AbsolutePosition** proprietà come numero di record sostitutivo. La posizione di un determinato record cambia quando si elimina un record precedente. Non vi è alcuna garanzia che un determinato record avrà lo stesso **AbsolutePosition** se il **Recordset** oggetto viene rieseguito o riaperto. I segnalibri rappresentano il modo consigliato per mantenere e tornare a una posizione specifica e sono l'unico modo il posizionamento in tutti i tipi di **Recordset** oggetti.
