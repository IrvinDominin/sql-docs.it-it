---
title: "Completare i passaggi successivi all&#39;installazione | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
caps.latest.revision: 8
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 8
---
# Completare i passaggi successivi all&#39;installazione
  Dopo aver installato il componente Riesecuzione distribuita, è necessario modificare gli account del controller e del servizio client relativi.  
  
### Per completare i passaggi di post-installazione  
  
1.  **Creare regole del firewall**: nei computer controller e client è necessario consentire il traffico in ingresso attraverso il firewall per il servizio corrispondente. Specificare le regole del firewall per i file eseguibili del servizio, all'interno delle cartelle di installazione.  
  
    1.  Per il servizio controller, creare una regola per **DReplayController.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  Per il servizio client, in ogni computer client creare una regola per **DReplayClient.exe**, che si trova nella cartella di installazione. Il comando seguente, ad esempio, abilita questa regola, dove `%InstallPath%` è la cartella di installazione del servizio:  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  **Concedere a ogni client le autorizzazioni per il server di destinazione**: al termine dell'installazione del servizio client nei computer client, è necessario aggiungere manualmente gli account del servizio client al ruolo sysadmin nell'istanza di destinazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Sicurezza di .NET Framework  
 Per installare qualsiasi funzionalità di Riesecuzione distribuita, è necessario disporre di autorizzazioni di amministratore. Solo un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con autorizzazioni sysadmin può aggiungere gli account del servizio client al ruolo del server sysadmin del server di prova. Per alcune considerazioni relative alla sicurezza di Riesecuzione distribuita, vedere [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
  