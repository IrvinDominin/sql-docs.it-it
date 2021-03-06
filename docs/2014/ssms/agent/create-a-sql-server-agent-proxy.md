---
title: Creare un proxy di SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ef4a623dca8ecdc92753b80438682f12521bfe8f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108811"
---
# <a name="create-a-sql-server-agent-proxy"></a>Creazione di un proxy di SQL Server Agent
  In questo argomento viene descritto come creare un proxy SQL Server Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Un account proxy di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent definisce un contesto di sicurezza in cui è possibile l'esecuzione di un passaggio di processo. Ogni proxy corrisponde a una credenziale di sicurezza Per impostare le autorizzazioni per un particolare passaggio di processo, creare un proxy dotato delle autorizzazioni necessarie per un sottosistema di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e quindi assegnarlo al passaggio di processo.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per creare un proxy di SQL Server Agent utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Se non disponibili, prima di creare un proxy è necessario creare le credenziali.  
  
-   I proxy di[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent utilizzano le credenziali per archiviare le informazioni sugli account utente di Windows. L'utente specificato nella credenziale deve disporre dell'autorizzazione "accesso come processo batch" sul computer in cui è in esecuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent verifica l'accesso al sottosistema per un proxy e garantisce l'accesso al proxy ad ogni esecuzione del passaggio di processo. Se il proxy non dispone più di accesso al sottosistema, il passaggio di processo non viene eseguito correttamente. In caso contrario, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent rappresenta l'utente specificato nel proxy ed esegue il passaggio di processo.  
  
-   La creazione di un proxy non implica la modifica delle autorizzazioni per l'utente specificato nella credenziale del proxy. È possibile ad esempio creare un proxy per un utente che non dispone dell'autorizzazione per la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. In questo caso, i passaggi di processo che utilizzano il proxy non sono in grado di connettersi a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Se l'account di accesso per l'utente viene utilizzato per l'accesso al proxy oppure se l'utente appartiene a un qualsiasi ruolo che prevede l'accesso al proxy, l'utente potrà utilizzare il proxy in un passaggio di processo.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
  
-   Solo i membri del ruolo predefinito del server **sysadmin** sono autorizzati a creare, modificare o eliminare gli account proxy. Gli utenti che non sono membri del ruolo predefinito del server **sysadmin** devono essere aggiunti a uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nel database **msdb** per poter utilizzare i proxy: **SQLAgentUserRole**, **SQLAgentReaderRole**o **SQLAgentOperatorRole**.  
  
-   Richiede l'autorizzazione `ALTER ANY CREDENTIAL` se si creano le credenziali oltre al proxy.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Per creare un proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera creare un proxy SQL Server Agent.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Proxy** e scegliere **Nuovo proxy**.  
  
4.  Nella pagina **Generale** della finestra di dialogo **Nuovo account proxy** immettere il nome del nuovo account proxy nella casella **Nome proxy** .  
  
5.  Nella casella **Nome credenziali** immettere il nome delle credenziali di sicurezza che verranno utilizzate dall'account proxy.  
  
6.  Immettere una descrizione dell'account proxy nella casella **Descrizione** .  
  
7.  In **Attivo nei sottosistemi seguenti**, selezionare il sottosistema o i sottosistemi adatti per questo proxy.  
  
8.  Nella pagina **Entità** aggiungere o rimuovere account di accesso oppure ruoli per concedere o negare l'accesso all'account proxy.  
  
9. Al termine, fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>Per creare un proxy di SQL Server Agent  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
 Per altre informazioni, vedere:  
  
-   [CREATE CREDENTIAL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql)  
  
-   [sp_add_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-proxy-transact-sql)  
  
-   [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql)  
  
  
