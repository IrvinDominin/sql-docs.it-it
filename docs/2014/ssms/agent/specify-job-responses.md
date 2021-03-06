---
title: Specificare le risposte ai processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], responses
- SQL Server Agent jobs, responses
- actions [SQL Server Agent jobs]
- responding to jobs
ms.assetid: 050242e1-9b79-4ade-91a9-580707b9d2d9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0bc3b747e1dcb1c2d027eb2c1df39c3715c011a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48122881"
---
# <a name="specify-job-responses"></a>Specifica delle risposte ai processi
  Le risposte ai processi specificano azioni che verranno eseguite dal servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent al termine di un processo. Tramite le risposte ai processi gli amministratori del database vengono informati in merito al completamento e alla frequenza di esecuzione dei processi. Le risposte ai processi tipiche includono:  
  
-   Notifica all'operatore tramite posta elettronica, trasmissione di messaggi su cercapersone o messaggi **Net Send** .  
  
     Usare uno di questi metodi di risposta al processo se l'operatore dovrà eseguire operazioni basate sull'esito. Ad esempio, se un processo di backup viene completato, l'operatore dovrà ricevere una notifica per rimuovere il nastro di backup e riporlo in un luogo sicuro.  
  
-   Scrittura di un messaggio di evento nel registro delle applicazioni di Windows.  
  
     Questa risposta può essere usata esclusivamente per i processi non riusciti.  
  
-   Eliminazione automatica del processo.  
  
     Usare la risposta soltanto se si è certi che non sarà necessario rieseguire il processo.  
  
## <a name="related-tasks"></a>Attività correlate  
  
|||  
|-|-|  
|**Descrizione**|**Argomento**|  
|Viene descritto come notificare lo stato del processo a un operatore.|[Notify an Operator of Job Status](notify-an-operator-of-job-status.md)|  
|Viene descritto come scrivere lo stato del processo nel registro applicazioni di Windows.|[Registrare lo stato del processo nel registro applicazioni di Windows](../../reporting-services/report-server/windows-application-log.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Monitoraggio e risposta agli eventi](monitor-and-respond-to-events.md)  
  
  
