---
title: Metodo CopyRecord (ADO) | Documenti Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_CopyRecord
- _Record::CopyRecord
helpviewer_keywords:
- CopyRecord method [ADO]
ms.assetid: b9bcf272-3c74-479f-95dd-0229a32e98fc
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7da84b8922306f5aa7c51fa10fe023eec06a5414
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277310"
---
# <a name="copyrecord-method-ado"></a>Metodo CopyRecord (ADO)
Copia di un'entità rappresentata da un [record](../../../ado/reference/ado-api/record-object-ado.md) in un'altra posizione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Record.CopyRecord (Source, Destination, UserName, Password, Options, Async)  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativo. Oggetto **stringa** valore che contiene un URL che specifica l'entità da copiare (ad esempio, un file o directory). Se *origine* viene omesso o specifica una stringa vuota, il file o directory rappresentata dall'oggetto corrente [Record](../../../ado/reference/ado-api/record-object-ado.md) verranno copiati.  
  
 *Destinazione*  
 Facoltativo. Oggetto **stringa** valore contenente un URL che specifica la posizione in cui *origine* verranno copiati.  
  
 *UserName*  
 Facoltativo. Oggetto **stringa** valore che contiene l'ID utente, se necessario, si autorizza l'accesso a *destinazione*.  
  
 *Password*  
 Facoltativo. Oggetto **stringa** valore contenente la password, se necessario, verifica *UserName*.  
  
 *Opzioni*  
 Facoltativo. Oggetto [CopyRecordOptionsEnum uguale al](../../../ado/reference/ado-api/copyrecordoptionsenum.md) valore con un valore predefinito di **adCopyUnspecified**. Specifica il comportamento di questo metodo.  
  
 *Async*  
 Facoltativo. Oggetto **booleano** valore che, quando **True**, specifica che questa operazione deve essere asincrona.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto **stringa** valore restituito in genere il valore di *destinazione*. Tuttavia, il valore esatto restituito è dipende dal provider.  
  
## <a name="remarks"></a>Remarks  
 I valori di *origine* e *destinazione* non deve essere identica; in caso contrario, si verifica un errore di run-time. Almeno uno dei nomi di server, percorso o risorsa deve essere diverso.  
  
 Tutti gli elementi figlio (ad esempio, le sottodirectory) di *origine* vengono copiati in modo ricorsivo, a meno che non **adCopyNonRecursive** specificato. In un'operazione ricorsiva, *destinazione* non deve essere una sottodirectory di *origine*; in caso contrario, l'operazione non verrà completata.  
  
 Questo metodo ha esito negativo se *destinazione* identifica un'entità esistente (ad esempio, un file o una directory), a meno che non **adCopyOverWrite** specificato.  
  
> [!IMPORTANT]
>  Utilizzare il **adCopyOverWrite** opzione con cautela. Ad esempio, se si specifica questa opzione quando si copia un file in una directory verrà *eliminare* la directory e sostituirlo con il file.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)
