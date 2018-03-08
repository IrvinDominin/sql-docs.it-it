---
title: "Gestire più passaggi di processo | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- job steps [SQL Server Agent]
- ordering job steps [SQL Server]
- multiple job steps
- SQL Server Agent jobs, job steps
- control of flow for jobs [SQL Server]
ms.assetid: 7aba19ff-72b3-45f6-8e54-23f4988d63a8
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d193665f6d46a1e21ed397e3fe33c22afa95cc8b
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="handle-multiple-job-steps"></a>Gestione di più passaggi di processo
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Se il processo è costituito da più passaggi, è necessario specificare l'ordine di esecuzione dei passaggi. Questa caratteristica è detta *controllo di flusso**.* È possibile aggiungere nuovi passaggi di processo e modificare il flusso dei passaggi esistenti in qualsiasi momento. Le modifiche verranno applicate alla successiva esecuzione del processo. Nella figura riportata di seguito è illustrato il controllo di flusso relativo a un processo di backup del database.  
  
![Controllo di flusso dei passaggi di processi di SQL Server Agent](../../ssms/agent/media/dbflow01.gif "Controllo di flusso dei passaggi di processi di SQL Server Agent")  
  
Il primo passaggio è rappresentato dal backup del database. Se questo passaggio non viene completato, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent segnala l'errore all'operatore specificato per la ricezione di notifiche. Se invece il backup del database viene completamente, il processo procede con il passaggio successivo, ovvero la ripulitura dei dati dei clienti. Se questo passaggio non viene eseguito correttamente, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent passa al ripristino del database. Se invece la ripulitura dei dati dei clienti viene completata, il processo procede con il passaggio successivo, ovvero l'aggiornamento delle statistiche, e così via fino al passaggio finale che può essere la segnalazione dell'avvenuto completamento o della mancata esecuzione.  
  
È necessario definire un'azione di controllo del flusso in corrispondenza dell'esecuzione o della mancata esecuzione di ogni passaggio di processo. È inoltre necessario specificare un'operazione da eseguire sia in caso di esecuzione che di mancata esecuzione di un passaggio di processo. È infine possibile definire il numero di tentativi di ripetizione di un passaggio di processo non eseguito correttamente, nonché l'intervallo tra i tentativi.  
  
> [!NOTE]  
> Quando si utilizza l'interfaccia utente grafica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent e si eliminano uno o più passaggi da un processo composto da più passaggi, tutti i passaggi del processo vengono rimossi e quindi vengono aggiunti nuovamente i passaggi restanti con i riferimenti corretti in caso di esito positivo o negativo. Ad esempio, si supponga di eseguire un processo con cinque passaggi e che il primo passaggio sia configurato in modo da rimandare direttamente al passaggio 4 se completato correttamente. Se si utilizza l'interfaccia utente grafica e si elimina il passaggio 3, vengono rimossi tutti i passaggi per questo processo e vengono aggiunti i quattro passaggi restanti (1, 2, 4 e 5) con i riferimenti corretti. In questo caso, il riferimento nel passaggio 1 verrebbe configurato per rimandare al passaggio 3 se il passaggio 1 viene completato correttamente.  
  
I passaggi di processo devono essere autonomi. Tra un passaggio di processo e l'altro non è pertanto consentito il trasferimento di valori booleani, dati o valori numerici. È tuttavia possibile passare valori da un passaggio di processo [!INCLUDE[tsql](../../includes/tsql_md.md)] a un altro utilizzando tabelle permanenti o tabelle temporanee globali. In particolare è possibile utilizzare file per passare valori di passaggi di processo che eseguono programmi eseguibili da un passaggio di processo a un altro. Ad esempio, l'eseguibile eseguito da un passaggio di processo scrive in un file, mentre quello eseguito da un passaggio di processo successivo legge il file.  
  
> [!NOTE]  
> Se si creano passaggi di processo ciclici (al passaggio 1 segue il passaggio 2, quindi dal passaggio 2 si torna al passaggio 1) e il processo viene creato tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], viene visualizzato un messaggio di avviso.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent registra i dati relativi al processo e ai passaggi di processo nella cronologia del processo.  
  
## <a name="see-also"></a>Vedere anche  
[sp_add_job](http://msdn.microsoft.com/en-us/6ca8fe2c-7b1c-4b59-b4c7-e3b7485df274)  
[sysjobhistory](http://msdn.microsoft.com/en-us/1b1fcdbb-2af2-45e6-bf3f-e8279432ce13)  
[sysjobs (Transact-SQL)](http://msdn.microsoft.com/en-us/e244a6a5-54c2-47a6-8039-dd1852b0ae59)  
[sysjobsteps](http://msdn.microsoft.com/en-us/978b8205-535b-461c-91f3-af9b08eca467)  
[Implementazione di processi](../../ssms/agent/implement-jobs.md)  
[Gestire passaggi di processo](../../ssms/agent/manage-job-steps.md)  
  
