---
title: ConnectModeEnum | Documenti Microsoft
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
- ConnectModeEnum
helpviewer_keywords:
- ConnectModeEnum enumeration [ADO]
ms.assetid: 3792c294-5161-4538-a908-22a5fc50b85f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f524d7d0385de331abed8d857296c55fcdbdc64
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="connectmodeenum"></a>ConnectModeEnum
Specifica le autorizzazioni disponibili per la modifica dei dati in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md), aprire un [Record](../../../ado/reference/ado-api/record-object-ado.md), o specificando i valori per il [modalità](../../../ado/reference/ado-api/mode-property-ado.md) proprietà del  **Record** e [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetti.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adModeRead**|1|Indica le autorizzazioni di sola lettura.|  
|**adModeReadWrite**|3|Indica le autorizzazioni di lettura/scrittura.|  
|**adModeRecursive**|0x400000|Usato in combinazione con le altre  *\*ShareDeny\**  valori (**adModeShareDenyNone**, **adModeShareDenyWrite**, o **adModeShareDenyRead**) per propagare le limitazioni di condivisione per tutti i corrente **Record**. Non produce alcun effetto se la **Record** non dispone di alcun elemento figlio. Viene generato un errore di run-time se utilizzato con **adModeShareDenyNone** solo. Tuttavia, può essere utilizzato con **adModeShareDenyNone** quando combinato con altri valori. Ad esempio, è possibile utilizzare "**adModeRead** o **adModeShareDenyNone** o **adModeRecursive**".|  
|**adModeShareDenyNone**|16|Consente ad altri utenti di aprire una connessione con le autorizzazioni. Impossibile negare l'accesso in lettura e in scrittura ad altri.|  
|**adModeShareDenyRead**|4|Impedisce ad altri l'apertura di una connessione con autorizzazioni di lettura.|  
|**adModeShareDenyWrite**|8|Impedisce ad altri l'apertura di una connessione con autorizzazioni di scrittura.|  
|**adModeShareExclusive**|12|Impedisce ad altri l'apertura di una connessione.|  
|**adModeUnknown**|0|Valore predefinito. Indica che le autorizzazioni non sono ancora state impostate o non possono essere determinate.|  
|**adModeWrite**|2|Indica le autorizzazioni di sola scrittura.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.ConnectMode.READ|  
|AdoEnums.ConnectMode.READWRITE|  
|(È disponibile un equivalente di AdoEnums.ConnectMode.RECURSIVE)|  
|AdoEnums.ConnectMode.SHAREDENYNONE|  
|AdoEnums.ConnectMode.SHAREDENYREAD|  
|AdoEnums.ConnectMode.SHAREDENYWRITE|  
|AdoEnums.ConnectMode.SHAREEXCLUSIVE|  
|AdoEnums.ConnectMode.UNKNOWN|  
|AdoEnums.ConnectMode.WRITE|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Proprietà Mode (ADO)](../../../ado/reference/ado-api/mode-property-ado.md)|[Metodo Open (record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)|  
|[Metodo Open (flusso ADO)](../../../ado/reference/ado-api/open-method-ado-stream.md)|[Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|
