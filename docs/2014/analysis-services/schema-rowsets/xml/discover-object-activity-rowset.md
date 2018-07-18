---
title: Set di righe DISCOVER_OBJECT_ACTIVITY | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- DISCOVER_OBJECT_ACTIVITY rowset
ms.assetid: 100f7de1-ad5c-4973-b863-3c10df1245c4
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 09aec1da2c7e9001585b0793b12f0faf89feaf27
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37235701"
---
# <a name="discoverobjectactivity-rowset"></a>Set di righe DISCOVER_OBJECT_ACTIVITY
  Fornisce l'utilizzo delle risorse per oggetto dopo l'avvio del servizio.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_OBJECT_ACTIVITY` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_AGGREGATION_HIT`|`DBTYPE_I8`||Numero di volte in cui un'aggregazione dell'oggetto è stata raggiunta dopo l'avvio del servizio.|  
|`OBJECT_AGGREGATION_MISS`|`DBTYPE_I8`||Numero di volte in cui un'aggregazione esistente dell'oggetto non è stata raggiunta, ovvero non è stata utilizzata, dopo l'avvio del servizio.|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||Tempo di CPU, in millisecondi, utilizzato dall'oggetto dopo l'avvio del servizio.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Numero di derivazione dei dati nell'oggetto. Questo numero aumenta ad ogni elaborazione dell'oggetto.|  
|`OBJECT_HIT`|`DBTYPE_I8`||Numero di volte in cui l'oggetto è stato raggiunto nella cache dopo l'avvio del servizio.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||ID dell'oggetto come definito in fase di creazione.|  
|`OBJECT_MISS`|`DBTYPE_I8`||Numero di volte in cui l'oggetto non è stato raggiunto nella cache dopo l'avvio del servizio.|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Percorso dell'elemento padre dell'oggetto corrente.|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||Valore accumulato dei dati letti dall'oggetto, in KB, dopo l'avvio del servizio.|  
|`OBJECT_READS`|`DBTYPE_I8`||Numero accumulato delle operazioni di lettura eseguite dall'oggetto dopo l'avvio del servizio.|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||Numero di righe restituite dall'oggetto al chiamante dopo l'avvio del servizio.|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||Numero di righe sottoposte ad analisi dall'oggetto dopo l'avvio del servizio.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Numero di versione dei metadati dell'oggetto. Questo numero cambia ad ogni modifica dell'oggetto.|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||Valore accumulato dei dati scritti dall'oggetto, in KB, dopo l'avvio del servizio.|  
|`OBJECT_WRITES`|`DBTYPE_I8`||Numero accumulato delle operazioni di scrittura eseguite dall'oggetto dopo l'avvio del servizio.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_OBJECT_ACTIVTY` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|OBJECT_PARENT_PATH|DBTYPE_WSTR|Facoltativo.|  
|OBJECT_ID|DBTYPE_WSTR|Facoltativo.|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
