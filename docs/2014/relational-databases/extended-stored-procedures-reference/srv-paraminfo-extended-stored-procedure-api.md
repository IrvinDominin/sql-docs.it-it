---
title: srv_paraminfo (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_paraminfo
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36498f29727107e5289ee63db1e58f3035c0feca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316301"
---
# <a name="srvparaminfo-extended-stored-procedure-api"></a>srv_paraminfo (API Stored procedure estesa)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce informazioni su un parametro. Questa funzione sostituisce le funzioni seguenti: [srv_paramtype](srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](srv-parammaxlen-extended-stored-procedure-api.md) e [srv_paramdata](srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** supporta i tipi di dati in [Tipi di dati](data-types-extended-stored-procedure-api.md) e i dati di lunghezza zero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Handle per una connessione client.  
  
 *n*  
 Numero ordinale del parametro da impostare. Il primo parametro è 1.  
  
 *pbType*  
 Tipo di dati del parametro.  
  
 *pcbMaxLen*  
 Indicatore di misura relativo alla lunghezza massima del parametro.  
  
 *pcbActualLen*  
 Indicatore di misura relativo alla lunghezza effettiva del parametro. Il valore 0 (\**pcbActualLen* == 0) indica dati di lunghezza zero se **pfNull* è impostato su FALSE.  
  
 *pbData*  
 Puntatore al buffer per i dati di parametro. Se *pbData* non è NULL, l'API Stored procedure estesa scrive \**pcbActualLen* byte di dati in \**pbData*. Se *pbData* è NULL, non viene scritto alcun dato in \**pbData* ma la funzione restituisce \**pbType*, \**pcbMaxLen*, \**pcbActualLen* e **pfNull*. La memoria per questo buffer deve essere gestita dall'applicazione.  
  
 *pfNull*  
 Puntatore a un flag null. **pfNull* viene impostato su TRUE se il valore del parametro è NULL.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Se le informazioni sul parametro vengono ottenute correttamente, viene restituito SUCCEED; in caso contrario, FAIL. Restituisce FAIL se non esiste una stored procedure remota corrente o se non è presente nessun parametro *n* della stored procedure remota.  
  
## <a name="remarks"></a>Note  
 **Nota sulla sicurezza** È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento per i programmatori delle stored procedure estese](database-engine-extended-stored-procedures-reference.md)  
  
  
