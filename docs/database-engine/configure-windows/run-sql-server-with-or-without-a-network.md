---
title: "Esecuzione di SQL Server in rete o non in rete | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "verifica dell'avvio del servizio di SQL Server"
  - "net start [SQL Server]"
  - "prompt dei comandi [SQL Server], connessioni"
  - "servizi di SQL Server, reti"
  - "informazioni sullo stato [SQL Server], servizio di SQL Server"
  - "esecuzione di SQL Server"
  - "rete [SQL Server], SQL Server in rete o non in rete"
  - "servizi [SQL Server], reti"
  - "avvio del servizio di SQL Server"
  - "SQL Server, esecuzione"
ms.assetid: 54eac961-5c7a-4481-982d-f93a64b5c2f4
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Esecuzione di SQL Server in rete o non in rete
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] può essere eseguito in rete o funziona anche senza una rete.  
  
## Esecuzione di SQL Server in rete  
 Affinché [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possa comunicare in rete, è necessario che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia in esecuzione. Per impostazione predefinita, il servizio [!INCLUDE[msCoName](../../includes/msconame-md.md)] viene avviato automaticamente tramite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows. Per verificare che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia stato avviato, al prompt dei comandi digitare il comando seguente:  
  
 **net start**  
  
 Se i servizi associati a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono stati avviati, nell'output di **net start** vengono visualizzati i servizi seguenti:  
  
-   Analysis Services (MSSQLSERVER)  
  
-   SQL Server (MSSQLSERVER)  
  
-   SQL Server Agent (MSSQLSERVER)  
  
## Esecuzione di SQL Server non in rete  
 Quando si esegue un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non in rete, non è necessario avviare il servizio predefinito [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], Gestione configurazione SQL Server e i comandi **net start** e **net stop** funzionano anche senza una rete, le procedure per l'avvio e l'arresto di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono identiche per operazioni in rete e in modalità autonoma.  
  
 Quando ci si connette a un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un client locale quale **sqlcmd**, la connessione alla rete viene ignorata e si accede direttamente all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite una pipe locale. La pipe locale e la pipe di rete vengono utilizzate rispettivamente quando non si utilizza e si utilizza la rete. Salvo diversa indicazione, le pipe locali e quelle di rete stabiliscono una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tramite la pipe standard (\\\\.\pipe\sql\query).  
  
 Quando si esegue la connessione a un'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] senza specificare il nome di un server, si utilizza una pipe locale. Quando si esegue la connessione a un'istanza locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e si specifica un nome di server, si utilizza una pipe di rete o un altro meccanismo IPC (InterProcess Communication) di rete, ad esempio IPX/SPX (Internetwork Packet Exchange/Sequenced Packet Exchange), a condizione che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sia stato configurato per l'utilizzo di più reti. Poiché un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non supporta le pipe di rete, è necessario omettere l'argomento non necessario **/***<nome_server>* quando ci si connette all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un client . Ad esempio, per connettersi a un'istanza autonoma di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da **osql**, digitare:  
  
 **osql /Usa /P** *\<saPassword>*  
  
  