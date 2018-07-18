---
title: Determinazione delle funzionalità supportate | Documenti Microsoft
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
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd86d96489e59926935567a0f8aa7cb23bf9f3ae
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="determining-what-is-supported"></a>Determinazione delle funzionalità supportate
Il **supporta** metodo viene utilizzato per determinare se un oggetto **Recordset** oggetto supporta un determinato tipo di funzionalità. Contiene la sintassi seguente:  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Osservazioni  
 Il **supporta** metodo restituisce un valore booleano che indica se il provider supporta tutte le funzionalità identificate dall'argomento CursorOptions. È possibile utilizzare il **supporta** metodo per determinare i tipi di funzionalità un **Recordset** supporta dell'oggetto. Se il **Recordset** oggetto supporta le funzionalità la cui costanti corrispondenti sono *CursorOptions*, **supporta** restituisce **True**. In caso contrario, restituisce **False**.  
  
 Utilizzando il **supporta** (metodo), è possibile cercare la capacità del **Recordset** oggetto per aggiungere nuovi record, utilizzare i segnalibri, utilizzare il **trovare** metodo, utilizzare lo scorrimento, utilizzare il  **Indice** , proprietà ed eseguire gli aggiornamenti in batch. Per un elenco completo delle costanti e i relativi significati, vedere [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Sebbene il **supporta** metodo può restituire **True** per una determinata funzionalità non garantisce che il provider può rendere la funzionalità disponibile in tutte le circostanze. Il **supporta** metodo restituisce semplicemente se il provider supporta la funzionalità specificata, presupponendo che vengano soddisfatte determinate condizioni. Ad esempio, il **supporta** metodo può indicare che un **Recordset** oggetto supporta gli aggiornamenti, anche se il cursore è basato su un join tra più tabelle, alcune colonne di cui non sono aggiornabili.
