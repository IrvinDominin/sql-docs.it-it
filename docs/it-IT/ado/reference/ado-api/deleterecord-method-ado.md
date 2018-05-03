---
title: Metodo DeleteRecord (ADO) | Documenti Microsoft
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
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d57efa09f964633ca3b6df35f0a1c3b919fcfb9b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="deleterecord-method-ado"></a>Metodo DeleteRecord (ADO)
Elimina un'entità rappresentata da un [Record](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parametri  
 *Origine*  
 Facoltativa. Oggetto **stringa** valore contenente un URL che identifica l'entità (ad esempio, il file o directory) da eliminare. Se *origine* viene omesso o è una stringa vuota, l'entità rappresentata dall'oggetto corrente specifica [Record](../../../ado/reference/ado-api/record-object-ado.md) viene eliminato. Se il Record è una raccolta ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) di **adCollectionRecord**, ad esempio una directory) verranno eliminati anche tutti gli elementi figlio (ad esempio, le sottodirectory).  
  
 *Async*  
 Facoltativa. Oggetto **booleano** valore che, quando **True**, specifica che l'operazione di eliminazione è asincrona.  
  
## <a name="remarks"></a>Osservazioni  
 Operazioni sull'oggetto rappresentato da questo **Record** potrebbe non riuscire dopo il completamento del metodo. Dopo la chiamata **DeleteRecord**, il **Record** deve essere chiusa perché il comportamento del **Record** potrebbe diventare imprevedibile in base quando viene aggiornato il provider di **Record** con l'origine dati.  
  
 Se questo **Record** ottenuto da un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), quindi i risultati di questa operazione non vengano riflesse immediatamente nel **Recordset**. Aggiornare il **Recordset** , chiudere e riaprire o eseguendo il **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) (metodo), il [aggiornamento](../../../ado/reference/ado-api/update-method.md) metodo, o [Resync](../../../ado/reference/ado-api/resync-method.md) metodo.  
  
> [!NOTE]
>  Gli URL che utilizzano lo schema http richiamerà automaticamente il [il Provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluti e relativi](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Record (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo Delete (insieme Fields ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Metodo Delete (insieme Parameters ADO)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Metodo Delete (recordset ADO)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
