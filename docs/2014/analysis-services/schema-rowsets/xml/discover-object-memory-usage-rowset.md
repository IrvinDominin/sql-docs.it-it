---
title: Set di righe DISCOVER_OBJECT_MEMORY_USAGE | Microsoft Docs
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
- DISCOVER_OBJECT_MEMORY_USAGE rowset
ms.assetid: 211cfa04-7bd6-43fe-8bd5-bfbff78bdafb
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: afd5d5f612693150cc476c69c3fe0dcf16917d64
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37291517"
---
# <a name="discoverobjectmemoryusage-rowset"></a>Set di righe DISCOVER_OBJECT_MEMORY_USAGE
  Fornisce informazioni sulle risorse di memoria utilizzate dagli oggetti.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il `DISCOVER_OBJECT_MEMORY_USAGE` set di righe contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Length|Description|  
|-----------------|--------------------|------------|-----------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`||Percorso dell'elemento padre dell'oggetto corrente.|  
|`OBJECT_ID`|`DBTYPE_WSTR`||ID dell'oggetto come definito in fase di creazione.|  
|`OBJECT_MEMORY_SHRINKABLE`|`DBTYPE_I8`||Quantità totale di memoria (byte) utilizzata da tutti gli oggetti compattabili posseduti direttamente dall'oggetto corrente. Il valore corrente non include la memoria utilizzata da oggetti posseduti da oggetti denominati di proprietà dell'oggetto corrente.|  
|`OBJECT_MEMORY_NONSHRINKABLE`|`DBTYPE_I8`||Quantità totale di memoria (byte) di tutti gli oggetti non compattabili posseduti direttamente dall'oggetto corrente. Il valore corrente non include la memoria utilizzata da oggetti posseduti da oggetti denominati di proprietà dell'oggetto corrente.|  
|`OBJECT_VERSION`|`DBTYPE_I4`||Numero di versione dei metadati dell'oggetto. Questo numero cambia ad ogni modifica dell'oggetto.|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||Numero di derivazione dei dati nell'oggetto. Questo numero aumenta ad ogni elaborazione dell'oggetto.|  
|`OBJECT_TYPE_ID`|`DBTYPE_I4`||Riservato per utilizzo interno.|  
|`OBJECT_TIME_CREATED`|`DBTYPE_DBTIMESTAMP`||L'ora UTC del server al momento della creazione dell'oggetto.|  
  
 Questo set di righe dello schema non è ordinato.  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe `DISCOVER_OBJECT_MEMORY_USAGE` può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|Facoltativo.|  
|`OBJECT_ID`|`DBTYPE_WSTR`|Facoltativo|  
  
## <a name="see-also"></a>Vedere anche  
 [XML per set di righe dello schema di analisi](xml-for-analysis-schema-rowsets.md)  
  
  
