---
title: "Creazione di una stringa di connessione valida mediante il protocollo di memoria condivisa | Microsoft Docs"
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
  - "stringhe di connessione [Motore di database], memoria condivisa"
  - "alias [SQL Server], memoria condivisa"
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Creazione di una stringa di connessione valida mediante il protocollo di memoria condivisa
  Le connessioni a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da un client in esecuzione nello stesso computer utilizzano il protocollo Shared Memory. La memoria condivisa non dispone di proprietà configurabili. Viene sempre utilizzata al primo tentativo di connessione e non può essere spostata dalla posizione iniziale nell'elenco **Protocolli abilitati** in **Proprietà protocolli client** . È possibile disabilitare il protocollo di memoria condivisa, operazione utile durante la risoluzione dei problemi relativi a uno degli altri protocolli.  
  
 Non è possibile creare un alias utilizzando il protocollo di memoria condivisa, ma, se si abilita la memoria condivisa e quindi ci si connette a [!INCLUDE[ssDE](../../includes/ssde-md.md)] tramite un nome, viene creata una connessione di memoria condivisa. Una stringa di connessione di memoria condivisa utilizza il formato `lpc:<servername>[\instancename]`.  
  
## Connessione al server locale  
 Quando si stabilisce una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione sullo stesso computer del client, è possibile usare **(locale)** come nome del server. Non si tratta di un'operazione consigliabile, in quanto genera ambiguità, ma può risultare utile se si è sicuri che il client viene eseguito nello stesso computer del server. Se, ad esempio, si crea un'applicazione per utenti mobili non connessi, ad esempio il personale di vendita, e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene eseguito su computer portatili e usato per archiviare dati di progetto, un client che si connette al server **(locale)** si connetterà sempre all'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in esecuzione sul portatile. In sostituzione di **(locale)**. è possibile usare la parola **localhost** o un punto (**.**).  
  
## Verifica del protocollo di connessione  
 La query seguente restituisce il protocollo utilizzato per la connessione corrente.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## Esempi:  
 I nomi seguenti consentono di connettersi al computer locale con il protocollo di memoria condivisa, se abilitato:  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 Non è possibile creare un alias per una connessione di memoria condivisa.  
  
> [!NOTE]  
>  Se si specifica un indirizzo IP nella casella **Server**, verrà stabilita una connessione TCP/IP.  
  
## Vedere anche  
 [Creazione di una stringa di connessione valida con TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Creazione di una stringa di connessione valida tramite named pipe](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)   
 [Scelta di un protocollo di rete](../Topic/Choosing%20a%20Network%20Protocol.md)  
  
  