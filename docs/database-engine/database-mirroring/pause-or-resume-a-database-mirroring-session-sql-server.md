---
title: "Sospendere o riprendere una sessione di mirroring del database (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ripresa del mirroring del database"
  - "mirroring del database [SQL Server], sessioni"
  - "mirroring del database [SQL Server], sospensione"
  - "mirroring del database [SQL Server], ripresa"
  - "sospensione del mirroring del database"
ms.assetid: 05ede3b4-6abe-4442-abb7-9f5aee1d6bc0
caps.latest.revision: 34
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 34
---
# Sospendere o riprendere una sessione di mirroring del database (SQL Server)
  In questo argomento viene descritto come sospendere o riprendere il mirroring del database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per eseguire ReplaceThisText utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Completamento:**  [Dopo la sospensione o ripresa del mirroring del database](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
 È possibile sospendere una sessione di mirroring del database in qualsiasi momento. Questa operazione potrebbe migliorare le prestazioni in caso di colli di bottiglia. Inoltre, la sessione può essere ripresa in qualsiasi momento.  
  
> [!CAUTION]  
>  Dopo un servizio forzato, quando il server principale originale esegue nuovamente la connessione, il mirroring viene sospeso. Se si riprende il mirroring in questa situazione, è possibile che si verifichi una perdita di dati nel server principale originale. Per informazioni sulla gestione della potenziale perdita di dati, vedere [Cambio di ruolo durante una sessione di mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È richiesta l'autorizzazione ALTER per il database.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 Per sospendere o riprendere una sessione di mirroring del database, utilizzare la pagina **Proprietà database - Mirroring** .  
  
#### Per sospendere o riprendere il mirroring del database  
  
1.  Durante una sessione di mirroring del database, connettersi all'istanza del server principale e in Esplora oggetti fare clic sul nome del server per espanderne l'albero.  
  
2.  Espandere **Database**e selezionare il database.  
  
3.  Fare clic con il pulsante destro del mouse sul database, scegliere **Attività** e quindi fare clic su **Server mirror**. Viene visualizzata la pagina **Mirroring** della finestra di dialogo **Proprietà database** .  
  
4.  Per sospendere la sessione, scegliere **Sospendi**.  
  
     Verrà richiesta una conferma. Se si fa clic su **Sì**la sessione viene sospesa e il pulsante diventa **Riprendi**.  
  
     Per altre informazioni sull'impatto della sospensione di una sessione, vedere [Sospensione e ripresa del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/pausing-and-resuming-database-mirroring-sql-server.md).  
  
5.  Per riprendere la sessione fare clic su **Riprendi**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per sospendere il mirroring del database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)] per qualsiasi partner.  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Eseguire l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] riportata di seguito.  
  
     ALTER DATABASE *nome_database* SET PARTNER SUSPEND  
  
     dove *nome_database* è il database con mirroring di cui si vuole sospendere la sessione.  
  
     Nell'esempio seguente viene sospeso il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER SUSPEND;  
    ```  
  
##### Per riprendere il mirroring del database  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)] per qualsiasi partner.  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Eseguire l'istruzione Transact-SQL seguente:  
  
     ALTER DATABASE *nome_database* SET PARTNER RESUME  
  
     dove *nome_database* è il database con mirroring di cui si vuole riprendere la sessione.  
  
     Nell'esempio seguente viene sospeso il database di esempio [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET PARTNER RESUME;  
    ```  
  
##  <a name="FollowUp"></a> Completamento: Dopo la sospensione o ripresa del mirroring del database  
  
-   **Dopo la sospensione del mirroring del database**  
  
     Nel database primario adottare le precauzioni per evitare un log delle transazioni pieno. Per altre informazioni, vedere [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md).  
  
-   **Dopo la ripresa del mirroring del database**  
  
     Quando si riprende una sessione di mirroring del database, il database con mirroring viene posto in stato SYNCHRONIZING. Se il livello di sicurezza corrisponde a FULL, il database mirror viene aggiornato in base al database principale e lo stato del database mirror diventa SYNCHRONIZED. A questo punto è possibile che si verifichi un failover. Se il server di controllo del mirroring è presente e in stato ON, è possibile che si verifichi un failover automatico. Se invece tale server non è presente, è possibile che si verifichi un failover manuale.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
  
-   [Rimuovere il mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/remove-database-mirroring-sql-server.md)  
  
## Vedere anche  
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  