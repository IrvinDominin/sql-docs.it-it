---
title: srv_rpcparams (API Stored procedure estesa) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_rpcparams
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcparams
ms.assetid: 96a5e6f6-d320-4623-b96e-0a856e3abebb
caps.latest.revision: 30
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e3910a9b26487b536761ade4835e30862d723261
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325971"
---
# <a name="srvrpcparams-extended-stored-procedure-api"></a>srv_rpcparams (API delle stored procedure estese)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Usare in alternativa l'integrazione CLR.  
  
 Restituisce il numero di parametri per la chiamata alla stored procedure remota corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
int srv_rpcparams ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *srvproc*  
 Puntatore alla struttura SRV_PROC che rappresenta l'handle di una determinata connessione client. In questo caso, l'handle che ha ricevuto la stored procedure remota. La struttura contiene informazioni utilizzate dalla libreria dell'API Stored procedure estesa per gestire le comunicazioni e i dati tra l'applicazione e il client.  
  
## <a name="returns"></a>Valori di codice restituiti  
 Numero di parametri nella stored procedure remota. Se nella stored procedure remota non sono inclusi parametri o se non è presente una stored procedure remota corrente, viene restituito -1 e viene generato un messaggio di errore informativo.  
  
## <a name="remarks"></a>Note  
 Questa funzione restituisce il numero di parametri nella stored procedure remota corrente. La funzione viene in genere chiamata dalla stored procedure remota.  
  
 Quando viene effettuata una chiamata a una stored procedure remota con parametri, tali parametri possono essere passati per nome o per posizione (senza nome). Se la chiamata alla stored procedure è stata eseguita con alcuni parametri passati per nome e alcuni passati per posizione, si verifica un errore. Quando si verifica questo errore, viene chiamato il gestore delle stored procedure remote, ma non vengono ricevuti i parametri e **srv_rpcparams** restituisce 0.  
  
> [!IMPORTANT]  
>  È necessario esaminare con attenzione il codice sorgente delle stored procedure estese e testare le DLL compilate prima di installarle in un server di produzione. Per informazioni sui test e sull'analisi della sicurezza, visitare questo [sito Web Microsoft](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
