---
title: Determinazione della modalità di modifica | Documenti Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], edit mode
- ADO, editing data
ms.assetid: 4c7e010d-08cd-4e22-9b32-23c36f02f88c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8557d0d514e37491a7d0952afcc14ae60d03d1ae
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="determining-edit-mode"></a>Determinazione della modalità di modifica
ADO gestisce un buffer di modifica associato al record corrente. Il **EditMode** proprietà indica se sono state apportate modifiche a questo buffer o se è stato creato un nuovo record. Utilizzare **EditMode** per determinare lo stato di modifica del record corrente. È possibile verificare le modifiche in sospeso se è stato interrotto un processo di modifica e determinare se è necessario utilizzare il **aggiornamento** o **CancelUpdate** metodo.  
  
 **EditMode** restituisce uno tra il **EditModeEnum** costanti che sono elencate nella tabella seguente.  
  
|Costante|Description|  
|--------------|-----------------|  
|**adEditNone**|Indica che nessuna operazione di modifica è in corso.|  
|**adEditInProgress**|Indica che i dati del record corrente sono stati modificati ma non salvati.|  
|**adEditAdd**|Indica che il **AddNew** metodo è stato chiamato e il record corrente nel buffer di copia è un nuovo record che non è stato salvato nel database.|  
|**adEditDelete**|Indica che il record corrente è stato eliminato.|  
  
 **EditMode** può restituire un valore valido solo se viene rilevato un record corrente. **EditMode** restituirà un errore se **BOF** o **EOF** è **True** o se è stato eliminato il record corrente.
