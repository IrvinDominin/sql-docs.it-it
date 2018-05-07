---
title: Set di righe DISCOVER_COMMAND_OBJECTS | Documenti Microsoft
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 789f1bf7bb4ba9c85ecc1a09a69d1542255f184b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/04/2018
---
# <a name="discovercommandobjects-rowset"></a>Set di righe DISCOVER_COMMAND_OBJECTS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Fornisce informazioni sull'utilizzo delle risorse e sulle attività relative agli oggetti utilizzati dal comando a cui si fa riferimento.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe **DISCOVER_COMMAND_OBJECTS** contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**SESSION_SPID**|**DBTYPE_I4**|Sì|ID della sessione.|  
|**SESSION_ID**|**DBTYPE_WSTR**|Sì|Identificatore univoco della sessione espresso come GUID.|  
|**SESSION_COMMAND_COUNT**|**DBTYPE_I4**||Numero di sequenza del comando.|  
|**OBJECT_PARENT_PATH**|**DBTYPE_WSTR**|Sì|Percorso dell'elemento padre dell'oggetto corrente.|  
|**OBJECT_ID**|**DBTYPE_WSTR**|Sì|ID dell'oggetto come definito al momento della creazione.|  
|**OBJECT_VERSION**|**DBTYPE_I4**||Numero di versione dei metadati dell'oggetto. Questo numero cambia ad ogni modifica dell'oggetto.|  
|**OBJECT_DATA_VERSION**|**DBTYPE_I4**||Numero di derivazione dei dati nell'oggetto. Questo numero aumenta ad ogni elaborazione dell'oggetto.|  
|**OBJECT_CPU_TIME_MS**|**DBTYPE_I8**||Tempo di CPU, in millisecondi, utilizzato dall'oggetto dopo l'avvio del comando.|  
|**OBJECT_READ_KB**|**DBTYPE_I8**||Valore accumulato dei dati letti dall'oggetto, in KB, dopo l'avvio del comando.|  
|**OBJECT_READS**|**DBTYPE_I8**||Numero accumulato delle operazioni di lettura eseguite dall'oggetto dopo l'avvio del comando.|  
|**OBJECT_WRITE_KB**|**DBTYPE_I8**||Valore accumulato dei dati scritti dall'oggetto, in KB, dopo l'avvio del comando.|  
|**OBJECT_WRITES**|**DBTYPE_I8**||Numero accumulato delle operazioni di scrittura eseguite dall'oggetto dopo l'avvio del comando.|  
|**OBJECT_ROWS_RETURNED**|**DBTYPE_I8**||Numero di righe restituite dall'oggetto al chiamante dopo l'avvio del comando.|  
|**OBJECT_ROWS_SCANNED**|**DBTYPE_I8**||Numero di righe sottoposte ad analisi dall'oggetto dopo l'avvio del comando.|  
  
 Questo set di righe dello schema non è ordinato.  
  
> [!IMPORTANT]  
>  Il set di righe dello schema DISCOVER_COMMAND_OBJECTS non segnala l'attività tramite le query DMV.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
