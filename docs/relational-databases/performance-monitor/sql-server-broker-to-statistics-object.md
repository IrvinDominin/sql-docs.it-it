---
title: Oggetto Broker TO Statistics di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e1307e2e47c2215aa7845114f58062b1770fe0ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47603123"
---
# <a name="sql-server-broker-to-statistics-object"></a>Oggetto Statistiche Broker TO di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'oggetto prestazione SQLServer:Broker TO Statistics contiene informazioni sul numero di volte in cui le finestre di dialogo di [!INCLUDE[ssSB](../../includes/sssb-md.md)] richiedono oggetti trasmissione e sulla frequenza di scrittura degli oggetti trasmissione in **tempdb**.  
  
 Gli oggetti di trasmissione registrano lo stato delle trasmissioni di messaggi per una finestra di dialogo [!INCLUDE[ssSB](../../includes/sssb-md.md)] . Poiché vengono archiviati in memoria, Per liberare memoria, [!INCLUDE[ssSB](../../includes/sssb-md.md)] scrive periodicamente batch di oggetti trasmissione inattivi nelle tabelle di lavoro di **tempdb**.  
  
 Nella tabella seguente sono elencati i contatori inclusi nell'oggetto.  
  
|Contatori dell'oggetto Statistiche Broker TO di SQL Server|Descrizione|  
|----------------------------------------------|-----------------|  
|**Lunghezza media scritture in batch**|La quantità media di oggetti di trasmissione salvati in un batch.|  
|**Tempo medio scrittura in batch (ms)**|Il tempo medio espresso in millisecondi richiesto per salvare un batch di oggetti di trasmissione.|  
|**Byte tempo medio scrittura batch**|Solo per uso interno.|
|**Byte medio tra batch (ms)**|Il tempo medio espresso in millisecondi tra le scritture di batch di oggetti di trasmissione.|  
|**Base tempo medio tra batch**|Solo per uso interno.| 
|**Get TO/sec**|Quante volte le finestre di dialogo richiedono oggetti di trasmissione in un secondo.|  
|**TO dirty/sec**|Quante volte gli oggetti di trasmissione sono stati contrassegnati come dirty in un secondo. Gli oggetti trasmissione sono contrassegnati come dirty dalla prima modifica che rende la copia in memoria diversa dalla copia archiviata in **tempdb**. Gli oggetti trasmissione vengono modificati quando [!INCLUDE[ssSB](../../includes/sssb-md.md)] deve registrare una modifica nello stato della trasmissione di messaggio per la finestra di dialogo.|  
|**Scritture TO/sec**|Il numero di volte al secondo in cui un batch di oggetti trasmissione viene scritto nelle tabelle di lavoro di **tempdb** . Un elevata quantità di scritture può indicare che quella memoria [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è sotto sforzo.|  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Metodi di accesso di SQL Server](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [Oggetto Memory Manager di SQL Server](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [Monitorare l'utilizzo delle risorse &#40;Monitor di sistema&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
