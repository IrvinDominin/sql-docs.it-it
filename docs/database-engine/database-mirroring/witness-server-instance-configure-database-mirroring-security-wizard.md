---
title: "Istanza server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.configdbmsecurwiz.witnsrvr.f1"
ms.assetid: b5763663-984a-473b-93a3-6cd3322ad41c
caps.latest.revision: 41
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 41
---
# Istanza server di controllo del mirroring (Configurazione guidata sicurezza mirroring del database)
  Utilizzare questa pagina per specificare informazioni sull'istanza del server che opera come istanza di controllo del mirroring per la sessione.  
  
> [!NOTE]  
>  L'istanza del server di controllo non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md).  
  
 **Per configurare il mirroring del database tramite SQL Server Management Studio**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
-   [Avviare la Configurazione guidata sicurezza mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start the configuring database mirroring security wizard.md)  
  
## Opzioni  
 **Istanza server di controllo del mirroring**  
 Se nella pagina **Mirroring** della finestra di dialogo **Proprietà database** è già stata specificata un'istanza del server di controllo, tale istanza viene visualizzata. Per altre informazioni, vedere [Proprietà database &#40;pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md).  
  
 In caso contrario, nella casella di riepilogo viene visualizzato il nome del server corrente. Si noti che l'istanza del server di controllo del mirroring non può essere uguale all'istanza del server principale o del server mirror.  
  
 **Connect**  
 Se non è stata specificata un'istanza del server di controllo, fare clic su **Connetti**. Verrà visualizzata la finestra di dialogo **Connetti al server** tramite la quale è possibile specificare l'istanza del server e stabilire una connessione.  
  
 Se è stata specificata l'istanza, ma non è disponibile una connessione con autorizzazioni sufficienti per il controllo dell'esistenza dell'endpoint, fare clic su **Connetti**. Verrà visualizzata la finestra di dialogo **Connetti al server** in cui l'istanza del server risulterà selezionata automaticamente e non sarà possibile modificarla. Specificare un account di dominio dotato di autorizzazioni sufficienti e connettersi all'istanza del server.  
  
> [!NOTE]  
>  Quando viene stabilita la connessione all'istanza del server, la Configurazione guidata sicurezza mirroring del database usa le credenziali della finestra di dialogo **Connetti al server**. Queste credenziali sono diverse da quelle di una sessione di mirroring, che utilizza le credenziali dell'account di avvio con il quale l'istanza del server è in esecuzione come servizio.  
  
 **Porta di attesa**  
 Il funzionamento di questa opzione dipende dalla presenza dell'endpoint di mirroring per l'istanza del server corrente, come illustrato di seguito:  
  
-   Se non esiste una porta di attesa per l'istanza del server, nella casella di testo **Porta** verrà visualizzato il numero di porta 5022. È possibile immettere qualsiasi numero di porta disponibile, ad esempio 7022.  
  
-   Se l'endpoint di mirroring esiste già, viene visualizzato il numero di porta ricevuto dall'endpoint. Se è necessario modificare la porta, utilizzare un'istruzione ALTER ENDPOINT. Per altre informazioni, vedere [ALTER ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-endpoint-transact-sql.md).  
  
    > [!NOTE]  
    >  È necessario un numero di porta.  
  
 **Nome endpoint**  
 Se l'endpoint di mirroring esiste per l'istanza del server, viene visualizzato il nome dell'endpoint. Se l'endpoint non esiste, è possibile specificare il nome dell'endpoint.  
  
 **Crittografa i dati inviati tramite questo endpoint**  
 La crittografia è abilitata per impostazione predefinita. Quando è abilitata, la crittografia non solo è supportata, ma è anche necessaria e utilizza i valori predefiniti per tutte le opzioni di crittografia. Per altre informazioni, vedere [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md).  
  
 Per disabilitare la crittografia, deselezionare la casella di controllo. Per abilitare di nuovo la crittografia, selezionare la casella di controllo.  
  
## Vedere anche  
 [Endpoint del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Proprietà database &#40;pagina Mirroring&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)   
 [Avviare Monitoraggio mirroring del database &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Server di controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)  
  
  