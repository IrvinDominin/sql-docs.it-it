---
title: Set di righe DISCOVER_TRACES | Documenti Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 1be6a035-ffc9-489e-9d4d-7391b3e384e2
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b32ae25f17cded9f395b7d48e6ae0f9db4dde7b6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discovertraces-rowset"></a>Set di righe DISCOVER_TRACES
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Vengono fornite informazioni sulle tracce attualmente attive nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_TRACES** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Description|  
|-----------------|--------------------|-----------------|  
|**TraceID**|**DBTYPE_WSTR**|ID della traccia.|  
|**Nome traccia**|**DBTYPE_WSTR**|Nome della traccia.|  
|**LogFileName**|**DBTYPE_WSTR**|Nome del file di log di traccia.|  
|**LogFileSize**|**DBTYPE_I4**|Dimensioni del file di log di traccia.|  
|**LogFileRollover**|**DBTYPE_BOOL**|Se true, indica che il file di log deve essere sottoposto a rollover; in caso contrario false.|  
|**Riavvio automatico**|**DBTYPE_BOOL**|Se true, indica che l'opzione di riavvio automatico è abilitata; in caso contrario false.|  
|**CreationTime**|**DBTYPE_TIME**|Data e ora di creazione della traccia.|  
|**StopTime**|**DBTYPE_TIME**|Data e ora di arresto di una traccia.|  
|**Tipo**|**PF_DBTYPE_WSTR**|Tipo di traccia.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il **DISCOVER_TRACES** righe può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**TraceId**|**DBTYPE_I4**|Facoltativa.|  
|**Tipo**|WSTR|Facoltativa.|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|Valore|  
|--------------|-----------|  
|GUID|a07ccd1a-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRACES|  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
