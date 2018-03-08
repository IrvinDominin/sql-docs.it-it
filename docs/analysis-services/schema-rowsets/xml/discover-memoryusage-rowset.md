---
title: Set di righe DISCOVER_MEMORYUSAGE | Documenti Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e416ea61-9615-468c-a96f-bbf731f803b1
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bd97d1b2eb02dda3f8add861e6767b7a495a821d
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="discovermemoryusage-rowset"></a>Set di righe DISCOVER_MEMORYUSAGE
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
Restituisce le statistiche di DISCOVER_MEMORYUSAGE per vari oggetti allocati dal server.  
  
> [!WARNING]  
>  Questo set di righe può produrre set di risultati molto grandi. Se non è possibile visualizzare i risultati perché richiedono una quantità di memoria di visualizzazione maggiore di quella consentita da SQL Server Management Studio, i risultati vengono scritti in un file temporaneo, nel percorso predefinito seguente:  
>   
>  '\<drive>:\Users\\<username\>\AppData\Local\Temp\\<fileID\>.xml'.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_MEMORYUSAGE** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrizione|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**MemoryID**|**DBTYPE_UI8**||numero che identifica la memoria.|  
|**MemoryName**|**DBTYPE_WSTR**||Nome dell'oggetto proprietario della memoria.|  
|**SPID**|**DBTYPE_UI4**|Sì|Sessione da cui è stata allocata la memoria. Zero indica che la memoria non è collegata a una sessione specifica.|  
|**CreationTime**|**DBTYPE_DBTIMESTAMP**||"Ora di creazione dell'oggetto" oppure "ora di allocazione della memoria".|  
|**BaseObjectType**|**DBTYPE_UI4**|Sì|Numero che descrive il tipo dell'oggetto. Gli oggetti con lo stesso BaseObjectType sono dello stesso tipo.|  
|**MemoryUsed**|**DBTYPE_UI8**|Sì|Dimensione corrente dell'oggetto, che può essere inferiore rispetto alla memoria allocata per l'utilizzo da parte dell'oggetto.|  
|**MemoryAllocated**|**DBTYPE_UI8**||Quantità di memoria allocata per l'utilizzo da parte dell'oggetto, che può essere maggiore rispetto alla quantità di memoria effettivamente utilizzata dall'oggetto.|  
|**MemoryAllocBase**|**DBTYPE_UI8**||Byte allocati inizialmente per l'oggetto stesso (escluse allocazioni aggiuntive per il contenuto dell'oggetto).|  
|**MemoryAllocFromAlloc**|**DBTYPE_UI8**||Memoria allocata per il contenuto di questo oggetto.|  
|**Valore ElementCount**|**DBTYPE_UI4**||Per un oggetto contenitore, questo è il numero di oggetti contenuti da tale oggetto.|  
|**Compattabile**|**DBTYPE_BOOL**|Sì|Valore booleano che indica se la memoria è compattabile (è possibile dedurlo a causa del numero di richieste di memoria). Se true, la memoria è compattabile; se false, la memoria non è compattabile.|  
|**ObjectParentPath**|**DBTYPE_WSTR**||Stringa che identifica il percorso completo dell'oggetto.|  
|**ObjectID**|**DBTYPE_WSTR**||Stringa che identifica l'oggetto. Il percorso completo di questo oggetto è rappresentato dalla stringa: (ObjectParentPath + '.' + ObjectId).|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|A07CCD21-8148-11D0-87BB-00C04FC33942|  
|ADOMDNAME|MemoryUsage|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
