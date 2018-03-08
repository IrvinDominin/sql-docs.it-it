---
title: Metodo LoadFromFile (ADO) | Documenti Microsoft
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
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 071ba2d6a2aa5af96af07274455a7495a9650dea
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="loadfromfile-method-ado"></a>Metodo LoadFromFile (ADO)
Carica il contenuto di un file esistente in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Parametri  
 *FileName*  
 Oggetto **stringa** valore contenente il nome di un file da caricare nella **flusso**. *Nome del file* può contenere qualsiasi percorso valido e un nome in formato UNC. Se il file specificato non esiste, si verifica un errore di run-time.  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo può essere utilizzato per caricare il contenuto di un file locale in un **flusso** oggetto. Ciò consente di caricare il contenuto di un file locale in un server.  
  
 Il **flusso** oggetto deve essere già aperto prima di chiamare **LoadFromFile**. Questo metodo non modifica l'associazione del **flusso** ; dell'oggetto verrà comunque associata all'oggetto specificato dall'URL o **Record** con cui il **flusso** originariamente aprire.  
  
 **LoadFromFile** sovrascrive il contenuto corrente del **flusso** oggetto con i dati letti dal file. I byte esistenti nel **flusso** vengono sovrascritti dal contenuto del file. I byte esistenti in precedenza e rimanenti dopo il [fine del flusso](../../../ado/reference/ado-api/eos-property.md) creato da **LoadFromFile**, vengono troncati.  
  
 Dopo una chiamata a **LoadFromFile**, la posizione corrente viene impostata all'inizio del **flusso** ([posizione](../../../ado/reference/ado-api/position-property-ado.md) è 0).  
  
 Poiché i 2 byte possono essere aggiunti all'inizio del flusso per la codifica, la dimensione del flusso potrebbe non corrispondere esattamente le dimensioni del file da cui è stato caricato.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
