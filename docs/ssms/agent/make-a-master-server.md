---
title: Configurare un server master | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.msxwiz.operator.f1
- sql13.ag.msxwiz.login.f1
- sql13.ag.msxwiz.target.f1
- sql13.ag.msxwiz.complete.f1
- sql13.ag.msxwiz.cover.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 41f940d5e871c862cf7d5d9b4a322f42dd98e83d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774069"
---
# <a name="make-a-master-server"></a>Make a Master Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

In questo argomento viene descritto come configurare un server master [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
**Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per configurare un server master tramite:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
I processi distribuiti con passaggi associati a un proxy vengono eseguiti nel contesto dell'account proxy nel server di destinazione. Verificare che siano soddisfatte le condizioni seguenti, per assicurare che i passaggi di processo associati a un proxy vengano scaricati dal server master a quello di destinazione:  
  
-   La sottochiave del Registro di sistema del server master **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<&#42;nome_istanza&#42;>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) è impostata su 1 (true). Per impostazione predefinita, questa sottochiave è impostata su 0 (False).  
  
-   Nel server di destinazione deve esistere un account proxy con lo stesso nome dell'account proxy del server master utilizzato per l'esecuzione del passaggio del processo.  
  
Se si verificano errori nel download dei passaggi dei processi che usano account proxy dal server master a quello di destinazione, è possibile controllare se nella colonna **error_message** della tabella **sysdownloadlist** nel database **msdb** sono presenti i messaggi di errore seguenti:  
  
-   "Per questo passaggio del processo è necessario un account proxy, ma l'individuazione dei proxy è disabilitata nel server di destinazione."  
  
    Per risolvere il problema, impostare la sottochiave del Registro di sistema **AllowDownloadedJobsToMatchProxyName** su 1.  
  
-   "Impossibile trovare il proxy."  
  
    Per risolvere il problema, verificare che nel server di destinazione sia disponibile un account proxy con lo stesso nome dell'account proxy del server master utilizzato per l'esecuzione del passaggio di processo.  
  
#### <a name="Permissions"></a>Permissions  
Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-make-a-master-server"></a>Per configurare un server master  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], quindi espanderla.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, scegliere **Amministrazione multiserver**e quindi fare clic su **Imposta come server master**. **Configurazione guidata server master** consente di eseguire in modo semplificato i passaggi necessari per configurare un server master e aggiungere server di destinazione.  
  
3.  Nella pagina **Operatore server master** configurare un operatore per il server master. Per l'invio di notifiche agli operatori via posta elettronica o cercapersone, è necessario che [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia configurato per l'invio di posta elettronica. Per inviare notifiche agli operatori con **net send**, il servizio Messenger deve essere in esecuzione nel server in cui si trova [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
    **Indirizzo posta elettronica**  
    Imposta l'indirizzo di posta elettronica dell'operatore.  
  
    **Indirizzo cercapersone**  
    Imposta l'indirizzo di posta elettronica del cercapersone dell'operatore.  
  
    **Indirizzo Net Send**  
    Imposta l'indirizzo **net send** dell'operatore.  
  
4.  Nella pagina **Server di destinazione** selezionare i server di destinazione per il server master.  
  
    **Server registrati**  
    Elenca i server registrati in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] che non sono già server di destinazione.  
  
    **Server di destinazione**  
    Elenca i server di destinazione.  
  
    **>**  
    Consente di spostare il server selezionato nell'elenco dei server di destinazione.  
  
    **>>**  
    Consente di spostare tutti i server nell'elenco dei server di destinazione.  
  
    **<**  
    Consente di eliminare il server selezionato dall'elenco dei server di destinazione.  
  
    **<<**  
    Consente di eliminare tutti i server dall'elenco dei server di destinazione.  
  
    **Aggiungi connessione**  
    Consente di aggiungere un server all'elenco dei server di destinazione senza registrarlo.  
  
    **Connessione**  
    Modificare le proprietà di connessione per il server selezionato.  
  
5.  Nella pagina **Credenziali account di accesso al server master** specificare se si desidera creare un nuovo account di accesso per il server di destinazione, se necessario, e assegnare a tale account di accesso i diritti per il server di destinazione.  
  
    **Crea un nuovo account di accesso se necessario e assegna i diritti per il server MSX**  
    Tramite questa opzione è possibile creare un nuovo account di accesso nel server di destinazione se l'account di accesso specificato non esiste già.  
  
## <a name="TsqlProcedure"></a>Utilizzo di Transact-SQL  
  
#### <a name="to-make-a-master-server"></a>Per configurare un server master  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio il server corrente viene integrato nel server master AdventureWorks1. L'ubicazione del server corrente è Building 21, Room 309, Rack 5.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
Per altre informazioni, vedere [sp_msx_enlist (Transact-SQL)](http://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>Vedere anche  
[Creazione di un ambiente multiserver](../../ssms/agent/create-a-multiserver-environment.md)  
[Amministrazione automatizzata in un'organizzazione](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
