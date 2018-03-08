---
title: Set di righe DISCOVER_CONNECTIONS | Documenti Microsoft
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
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_CONNECTIONS rowset
ms.assetid: e4703970-c31d-448c-ab68-503303c91aa4
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d9d56f64f0b4cb1912e9eaaa7e644c6cbc29ad44
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="discoverconnections-rowset"></a>Set di righe DISCOVER_CONNECTIONS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Fornisce informazioni sulle risorse di utilizzo e l'attività sulle connessioni attualmente aperte nel server.  
  
 **Si applica a:** modelli tabulari, modelli multidimensionali  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il **DISCOVER_CONNECTIONS** set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Restrictions|Description|  
|-----------------|--------------------|------------------|-----------------|  
|**CONNECTION_ID**|**DBTYPE_I4**|Sì|Numero univoco che identifica la connessione.|  
|**CONNECTION_USER_NAME**|**DBTYPE_WSTR**|Sì|Nome utente della connessione.|  
|**CONNECTION_IMPERSONATED_USER_NAME**|**DBTYPE_WSTR**|Sì|Riservato per utilizzi futuri. In Analysis Services viene sempre restituito NULL per il valore di CONNECTION_IMPERSONATED_USER_NAME.|  
|**CONNECTION_HOST_NAME**|**DBTYPE_WSTR**|Sì|Nome del computer che ha iniziato la connessione.|  
|**CONNECTION_HOST_APPLICATION**|**DBTYPE_WSTR**||Nome dell'applicazione che ha iniziato la connessione.|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata la connessione.|  
|**CONNECTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|Sì|Tempo trascorso, in millisecondi, dopo l'avvio della connessione.|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è iniziata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||Data e ora UTC del server in cui è terminata l'esecuzione dell'ultimo comando.|  
|**CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**|Sì|Tempo trascorso, in millisecondi, dopo la fine dell'esecuzione dell'ultimo comando.|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**|Sì|Tempo di inattività, in millisecondi, dopo l'avvio della connessione.|  
|**CONNECTION_BYTES_SENT**|**DBTYPE_I8**||Numero accumulato dei byte inviati dalla connessione dopo l'avvio della connessione.|  
|**CONNECTION_DATA_BYTES_SENT**|**DBTYPE_I8**||Numero accumulato dei byte di dati inviati dalla connessione dopo l'avvio della connessione.<br /><br /> I dati vengono trasmessi compressi sulla connessione. Questo valore rappresenta i dati espansi inviati.|  
|**CONNECTION_BYTES_RECEIVED**|**DBTYPE_I8**||Numero accumulato dei byte ricevuti dalla connessione dopo l'avvio della connessione.|  
|**CONNECTION_DATA_BYTES_RECEIVED**|**DBTYPE_I8**||Numero accumulato dei byte di dati ricevuti dalla connessione dopo l'avvio della connessione.<br /><br /> I dati vengono trasmessi compressi sulla connessione. Questo valore rappresenta i dati espansi ricevuti.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>Utilizzo di ADOMD.NET per restituire il set di righe  
 Quando si utilizzano ADOMD.NET e il set di righe dello schema per recuperare metadati, è possibile utilizzare il GUID o la stringa per fare riferimento a un oggetto set di righe dello schema nel metodo GetSchemaDataSet. Per altre informazioni, vedere [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md).  
  
 Nella tabella seguente vengono forniti i GUID e i valori stringa che identificano questo set di righe.  
  
|Argomento|valore|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|Connessioni|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
