---
title: "FILESTREAM e FileTable con i gruppi di disponibilità AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: availability-groups
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
caps.latest.revision: "15"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5319d8caeb5e8cfe2b77ae027e4de5fa34a28494
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="filestream-and-filetable-with-always-on-availability-groups-sql-server"></a>FILESTREAM e FileTable con i gruppi di disponibilità AlwaysOn (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  In questo argomento sono contenute informazioni su come utilizzare le funzionalità FILESTREAM e FileTable con [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 Tutte le funzionalità FILESTREAM sono supportate. Dopo un failover, i dati FILESTREAM sono accessibili sia nelle repliche secondarie leggibili sia nella nuova primaria.  
  
 La funzionalità FileTable è supportata parzialmente. Dopo un failover, i dati FileTable sono accessibili nella replica primaria, ma non nelle repliche secondarie leggibili.  
  
 **Contenuto dell'argomento**  
  
-   [Prerequisiti](#Prerequisites)  
  
-   [Utilizzo di nomi di rete virtuale per FILESTREAM e accesso a FileTable](#vnn)  
  
-   [Attività correlate](#RelatedTasks)  
  
-   [Contenuto correlato](#RelatedContent)  
  
##  <a name="Prerequisites"></a> Prerequisiti  
  
-   Prima di aggiungere un database in cui è utilizzato FILESTREAM, con o senza FileTable, a un gruppo di disponibilità, verificare che FILESTREAM sia abilitato su ogni istanza del server in cui è ospitata una replica di disponibilità per il gruppo di disponibilità. Per altre informazioni, vedere [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md).  
  
##  <a name="vnn"></a> Utilizzo di nomi di rete virtuale per FILESTREAM e accesso a FileTable  
 Quando si abilita FILESTREAM su un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], viene creata una condivisione del livello di istanza per fornire l'accesso ai dati FILESTREAM. Si accede a questa condivisione tramite il nome computer nel formato seguente:  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 In un gruppo di disponibilità AlwaysOn, tuttavia, il nome del computer è virtualizzato tramite un nome di rete virtuale o VNN. Quando il computer è la replica primaria in un gruppo di disponibilità, e i database nel gruppo di disponibilità contengono dati FILESTREAM, allora viene creata anche una condivisione con ambito VNN per fornire l'accesso ai dati FILESTREAM. Non influisce sull'accesso Transact-SQL ai dati FILESTREAM. Nondimeno le applicazioni che utilizzano le API del file system devono utilizzare la condivisione con ambito VNN che ha un percorso con il formato seguente:  
  
 `\\<VNN>\<filestream_share_name>`  
  
 Questa condivisione con ambito VNN viene creata quando si verifica uno degli eventi seguenti.  
  
-   Quando si aggiunge un database che contiene dati FILESTREAM a un gruppo di disponibilità AlwaysOn sulla replica primaria. In questo caso, la condivisione `\\<computer_name>\<filestream_share_name>` già esiste. Viene creata la condivisione `\\<VNN>\<filestream_share_name>` .  
  
-   Si abilita FILESTREAM per il file i/o o si trasmette l'accesso su una replica primaria che dispone di gruppi di disponibilità. Vengono create le seguenti condivisioni:  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  `\\<VNN1>\<filestream_share_name>` per il gruppo di disponibilità 1.  
  
    3.  `\\<VNN2>\<filestream_share_name>` per il gruppo di disponibilità 2.  
  
 Queste condivisioni con ambito VNN vengono propagate anche in tutte le repliche secondarie.  
  
 Quando il database che contiene dati FILESTREAM o FileTable appartiene a un gruppo di disponibilità AlwaysOn:  
  
-   Le funzioni FILESTREAM e FileTable accettano o restituiscono nomi di rete virtuale anziché nomi computer. Per altre informazioni su queste funzioni, vedere [Funzioni FileStream e FileTable &#40;Transact-SQL&#41;](../../../relational-databases/system-functions/filestream-and-filetable-functions-transact-sql.md).  
  
-   Ogni accesso a dati FILESTREAM o FileTable tramite le API del file system deve utilizzare VNN anziché nomi computer.  
  
 Se l'applicazione tenta di accedere alla condivisione tramite il nome computer in formato `\\<computer_name>\<filestream_share_name>` quando il database fa parte di un gruppo di disponibilità, allora viene generato un errore.  
  
 Se l'applicazione tenta di accedere alla condivisione tramite un percorso con ambito VNN quando il database non fa parte di un gruppo di disponibilità, allora la richiesta potrebbe avere esito positivo. In questo caso, il nome della rete virtuale viene risolto nel nome computer. Questo utilizzo è tuttavia sconsigliato vivamente, poiché il percorso con ambito VNN smetterà di funzionare se viene rilasciato il gruppo di disponibilità.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [Abilitazione dei prerequisiti per la tabella FileTable](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="RelatedContent"></a> Contenuto correlato  
 nessuna.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di Gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
