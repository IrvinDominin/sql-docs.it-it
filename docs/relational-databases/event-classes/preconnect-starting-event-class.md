---
title: "Classe di evento PreConnect:Starting | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe di evento PreConnect:Starting"
ms.assetid: d43ed0ad-3dbd-42e0-9cef-8320b8d87497
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Classe di evento PreConnect:Starting
  La classe di evento PreConnect:Starting indica l'avvio dell'esecuzione di un trigger LOGON o di una funzione di classificazione di Resource Governor.  
  
## Colonne di dati della classe di evento PreConnect:Starting  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|215|27|No|  
|SPID|**int**|ID del processo del server che genera l'evento.|12|Sì|  
|EventSubClass|**int**|1 per la funzione di classificazione definita dall'utente.|21|Sì|  
|StartTime|**datetime**|Ora di avvio della funzione di classificazione definita dall'utente.|14|Sì|  
|ObjectID|**int**|ID dell'oggetto di classificazione definito dall'utente.|22|Sì|  
|ObjectName|**nvarchar(256)**|Nome in due parti della funzione di classificazione definita dall'utente, ad esempio dbo.classifier.|34|Sì|  
  
## Vedere anche  
 [Eventi estesi](../../relational-databases/extended-events/extended-events.md)   
 [classe di evento PreConnect:Completed](../../relational-databases/event-classes/preconnect-completed-event-class.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  