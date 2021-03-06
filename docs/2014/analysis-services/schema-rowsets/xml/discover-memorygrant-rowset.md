---
title: Set di righe DISCOVER_MEMORYGRANT | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21e24d1a7ab727eeb2c014870adb9928aed989dd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154261"
---
# <a name="discovermemorygrant-rowset"></a>Set di righe DISCOVER_MEMORYGRANT
  Restituisce un elenco di concessioni di quote di memoria interna recuperate da processi attualmente in esecuzione nel server. Per verificare se un processo è in esecuzione nel server, utilizzare `Select * from $System.Discover_Jobs`.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_MEMORYGRANT` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|`MEMORY_ID`|**DBTYPE_I8**||Numero che identifica la concessione della quota di memoria. Univoco all'interno del contesto di una singola richiesta DISCOVER_MEMORYGRANT.|  
|`SPID`|`DBTYPE_I4`|Obbligatorio|SPID che è possibile ottenere eseguendo `Select * from $System.Discover_Sessions`.|  
|`CreationTime`|`DBTYPE_I8 DBTYPE_DBTIMESTAMP`||Ora di concessione della quota.|  
|`LastRequestTime`|**DBTYPE_DBTIMESTAMP**||Ora dell'ultima modifica della richiesta di quota.|  
|`MemoryUsed`|`DBTYPE_I4`||Quantità di memoria utilizzata insieme alla quota.|  
|`MemoryGranted`|`DBTYPE_I4`||Quantità di memoria concessa per l'utilizzo da parte del processo che ottiene la quota di memoria.|  
|`Blocked`|`DBTYPE_BOOL`||Valore booleano che indica lo stato di blocco del processo. True indica che il processo è bloccato in attesa che un altro processo rilasci quota sufficiente per concedere la relativa richiesta di quota. False indica che il processo ha ricevuto la relativa quota e può procedere all'esecuzione.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
