---
title: Abilitare e disabilitare la funzionalità Gruppi di disponibilità Always On (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bcd22dedf4d70734098f0fac9886e99c89169eba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806868"
---
# <a name="enable-and-disable-always-on-availability-groups-sql-server"></a>Abilitare e disabilitare la funzionalità Gruppi di disponibilità Always On (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  L'abilitazione di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] è un prerequisito per l'utilizzo di gruppi di disponibilità in un'istanza del server. Prima di poter creare e configurare un qualsiasi gruppo di disponibilità, la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] deve essere stata abilitata in ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui sarà ospitata una replica di disponibilità per uno o più gruppi di disponibilità.  
  
> [!IMPORTANT]  
>  Se si elimina e si ricrea un cluster WSFC, è necessario disabilitare e riabilitare la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in ogni istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è ospitata una replica di disponibilità nel cluster WSFC originale.  
  
-   **Prima di iniziare:**  
  
     [Prerequisiti](#Prerequisites)  
  
     [Security](#Security)  
  
-   **Procedura:**  
  
    -   [Determinare se la funzionalità Gruppi di disponibilità Always On è abilitata](#IsEnabled)  
  
    -   [Abilitare Gruppi di disponibilità Always On](#EnableAOAG)  
  
    -   [Disabilitare Gruppi di disponibilità Always On](#DisableAOAG)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Prerequisites"></a> Prerequisiti per l'abilitazione di Gruppi di disponibilità Always On  
  
-   L'istanza del server deve trovarsi in un nodo WSFC (Windows Server Failover Clustering).  
  
-   Nell'istanza del server deve essere in esecuzione un'edizione di SQL Server che supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Per altre informazioni, vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
-   Abilitare Gruppi di disponibilità Always On in una sola istanza del server per volta. Dopo aver abilitato Gruppi di disponibilità Always On, attendere il riavvio del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di continuare con un'altra istanza del server.  
  
 Per informazioni sui prerequisiti, vedere[Prerequisiti, restrizioni e consigli per i gruppi di disponibilità Always On &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
###  <a name="Security"></a> Sicurezza  
 Mentre la funzionalità Gruppi di disponibilità Always On è abilitata in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'istanza del server ha il controllo completo sul cluster WSFC.  
  
####  <a name="Permissions"></a> Permissions  
 È richiesta l'appartenenza al gruppo degli **amministratori** nel computer locale, nonché il controllo totale nel cluster WSCF. Quando si abilita Always On usando PowerShell, aprire la finestra del prompt dei comandi con l'opzione **Esegui come amministratore** .  
  
 Richiede le autorizzazioni per la gestione e la creazione degli oggetti di Active Directory.  
  
##  <a name="IsEnabled"></a> Determinare se la funzionalità Gruppi di disponibilità Always On è abilitata  
  
-   [SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="SSMS1Procedure"></a> Utilizzo di SQL Server Management Studio  
 **Per determinare se la funzionalità Gruppi di disponibilità Always On è abilitata**  
  
1.  In Esplora oggetti fare clic con il pulsante destro del mouse sull'istanza del server e scegliere **Proprietà**.  
  
2.  Nella finestra di dialogo **Proprietà server** scegliere la pagina **Generale** . Per la proprietà **Is HADR Enabled** è visualizzato uno dei valori seguenti:  
  
    -   **True**, se la funzionalità Gruppi di disponibilità Always On è abilitata.  
  
    -   **False**, se la funzionalità Gruppi di disponibilità Always On è disabilitata.  
  
###  <a name="Tsql1Procedure"></a> Utilizzo di Transact-SQL  
 **Per determinare se la funzionalità Gruppi di disponibilità Always On è abilitata**  
  
1.  Utilizzare l'istruzione [SERVERPROPERTY](../../../t-sql/functions/serverproperty-transact-sql.md) seguente:  
  
    ```  
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     L'impostazione della proprietà del server **IsHadrEnabled** indica se un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è abilitata per Gruppi di disponibilità Always On, come indicato di seguito:  
  
    -   Se **IsHadrEnabled** = 1, la funzionalità Gruppi di disponibilità Always On è abilitata.  
  
    -   Se **IsHadrEnabled** = 0, la funzionalità Gruppi di disponibilità Always On è disabilitata.  
  
    > [!NOTE]  
    >  Per altre informazioni sulla proprietà del server **IsHadrEnabled** , vedere [SERVERPROPERTY &#40;Transact-SQL&#41;](../../../t-sql/functions/serverproperty-transact-sql.md).  
  
###  <a name="PowerShell1Procedure"></a> Utilizzo di PowerShell  
 **Per determinare se la funzionalità Gruppi di disponibilità Always On è abilitata**  
  
1.  Impostare il valore predefinito (**cd**) sull'istanza del server in cui determinare se la funzionalità [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] è abilitata.  
  
2.  Immettere il comando di PowerShell **Get-Item** seguente:  
  
    ```  
    PS SQLSERVER:\SQL\NODE1\DEFAULT> get-item . | select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente PowerShell di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
##  <a name="EnableAOAG"></a> Abilitare Gruppi di disponibilità Always On  
 **Per abilitare Always On usando:**  
  
-   [Gestione configurazione SQL Server](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="SQLCM2Procedure"></a> Utilizzo di Gestione configurazione SQL Server  
 **Per abilitare Gruppi di disponibilità Always On**  
  
1.  Connettersi al nodo WSCF (Windows Server Failover Clustering) in cui è ospitata l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nella quale si vuole abilitare Gruppi di disponibilità Always On.  
  
2.  Nel menu **Start** scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**.  
  
3.  In **Gestione configurazione SQL Server** fare clic su **Servizi di SQL Server**, fare clic con il pulsante destro del mouse su SQL Server (**\<***nome istanza***>)**, dove **\<***nome istanza***>** è il nome di un'istanza locale per cui si vuole abilitare Gruppi di disponibilità Always On, quindi scegliere **Proprietà**.  
  
4.  Selezionare la scheda **Disponibilità elevata Always On**.  
  
5.  Verificare che nel campo **Nome cluster di failover Windows** sia incluso il nome del cluster di failover locale. Se il campo è vuoto, questa istanza del server non supporta attualmente [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Il computer locale non è un nodo del cluster, il cluster WSFC è stato chiuso, oppure si tratta di un'edizione di [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] che non supporta [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
6.  Selezionare la casella di controllo **Abilita gruppi di disponibilità Always On** e scegliere **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Successivamente, è necessario riavviare manualmente il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . In questo modo è possibile scegliere un'ora per il riavvio che meglio soddisfa le esigenze aziendali. Al riavvio del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Always On sarà abilitato e la proprietà del server **IsHadrEnabled** sarà impostata su 1.  
  
###  <a name="PScmd2Procedure"></a> Utilizzo di SQL Server PowerShell  
 **Per abilitare Always On**  
  
1.  Spostarsi nella directory (**cd**) dell'istanza del server che si vuole abilitare per Gruppi di disponibilità Always On.  
  
2.  Per abilitare Gruppi di disponibilità AlwaysOn, usare il cmdlet **Enable-SqlAlwaysOn**.  
  
     Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente PowerShell di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
    > [!NOTE]  
    >  Per informazioni su come controllare se il cmdlet **Enable-SqlAlwaysOn** riavvia il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [Situazioni in cui un cmdlet comporta il riavvio del servizio SQL Server](#WhenCmdletRestartsSQL), più avanti in questo argomento.  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
####  <a name="ExmplEnable-SqlHadrServic"></a> Esempio: Enable-SqlAlwaysOn  
 Il comando di PowerShell seguente abilita [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in un'istanza di SQL Server (*Computer*\\*Istanza*).  
  
```  
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="DisableAOAG"></a> Disabilitare Gruppi di disponibilità Always On  
  
-   **Prima di disabilitare Always On:**  
  
     [Indicazioni](#Recommendations)  
  
-   **Per disabilitare Always On usando:**  
  
    -   [Gestione configurazione SQL Server](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **Completamento**  [Dopo la disabilitazione di Always On](#FollowUp)  
  
> [!IMPORTANT]  
>  Disabilitare Always On in una sola istanza del server per volta. Dopo aver disabilitato Gruppi di disponibilità Always On, attendere il riavvio del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prima di continuare con un'altra istanza del server.  
  
###  <a name="Recommendations"></a> Indicazioni  
 Prima di disabilitare Always On su un'istanza del server, è consigliabile eseguire queste operazioni:  
  
1.  Se l'istanza del server sta attualmente ospitando la replica primaria di un gruppo di disponibilità che si desidera tenere, si consiglia di eseguire manualmente un failover sul gruppo di disponibilità a una replica secondaria sincronizzata, se possibile. Per altre informazioni, vedere [Eseguire un failover manuale pianificato di un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
2.  Rimuovere tutte le repliche secondarie locali. Per altre informazioni, vedere [Rimuovere una replica secondaria da un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md).  
  
###  <a name="SQLCM3Procedure"></a> Utilizzo di Gestione configurazione SQL Server  
 **Per disabilitare Always On**  
  
1.  Connettersi al nodo WSCF (Windows Server Failover Clustering) nel quale è ospitata l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui si vuole disabilitare Gruppi di disponibilità Always On.  
  
2.  Nel menu **Start** scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)], **Strumenti di configurazione**, quindi fare clic su **Gestione configurazione SQL Server**.  
  
3.  In **Gestione configurazione SQL Server** fare clic su **Servizi di SQL Server**, fare clic con il pulsante destro del mouse su SQL Server (**\<***nome istanza***>)**, dove **\<***nome istanza***>** è il nome di un'istanza locale per cui si vuole disabilitare Gruppi di disponibilità Always On, quindi scegliere **Proprietà**.  
  
4.  Deselezionare la casella di controllo**Abilita gruppi di disponibilità Always On**nella scheda **Disponibilità elevata Always On** e scegliere **OK**.  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] è possibile salvare la modifica e riavviare il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Al riavvio del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , Always On sarà disabilitato e la proprietà del server **IsHadrEnabled** sarà impostata su 0, per indicare che la funzionalità Gruppi di disponibilità Always On è disabilitata.  
  
5.  È consigliabile leggere le informazioni fornite in [Completamento: Dopo la disabilitazione di Always On](#FollowUp), più avanti in questo argomento.  
  
###  <a name="PScmd3Procedure"></a> Utilizzo di SQL Server PowerShell  
 **Per disabilitare Always On**  
  
1.  Spostarsi nella directory (**cd**) dell'istanza del server attualmente abilitata che si vuole disabilitare per Gruppi di disponibilità Always On.  
  
2.  Per disabilitare Gruppi di disponibilità Always On, usare il cmdlet **Disable-SqlAlwaysOn**.  
  
     Ad esempio, il comando seguente disabilita la funzionalità Gruppi di disponibilità Always On in un'istanza di SQL Server (*Computer*\\*Istanza*).  Il comando richiede il riavvio dell'istanza per cui verrà richiesta la conferma all'utente.  
  
    ```  
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  Per informazioni su come controllare se il cmdlet **Disable-SqlAlwaysOn** riavvia il servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vedere [Situazioni in cui un cmdlet comporta il riavvio del servizio SQL Server](#WhenCmdletRestartsSQL), più avanti in questo argomento.  
  
     Per visualizzare la sintassi di un cmdlet, usare il cmdlet **Get-Help** nell'ambiente PowerShell di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Per altre informazioni, vedere [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md).  
  
 **Per impostare e utilizzare il provider PowerShell per SQL Server**  
  
-   [Provider PowerShell per SQL Server](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
###  <a name="FollowUp"></a> Completamento: Dopo la disabilitazione di Always On  
 Dopo avere disabilitato Gruppi di disponibilità Always On, è necessario riavviare l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Gestione configurazione SQL Server riavvia l'istanza del server automaticamente. Tuttavia, se è stato usato il cmdlet **Disable-SqlAlwaysOn** , sarà necessario riavviare manualmente l'istanza del server. Per altre informazioni, vedere [sqlservr Application](../../../tools/sqlservr-application.md).  
  
 Nell'istanza del server riavviata:  
  
-   Poiché i database di disponibilità non vengono avviati insieme a SQL Server, non saranno accessibili.  
  
-   L'unica istruzione Always On [!INCLUDE[tsql](../../../includes/tsql-md.md)] supportata è [DROP AVAILABILITY GROUP](../../../t-sql/statements/drop-availability-group-transact-sql.md). CREATE AVAILABILITY GROUP, ALTER AVAILABILITY GROUP e le opzioni SET HADR di ALTER DATABASE non sono supportate.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] I metadati e i dati di configurazione di [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in WSFC non sono interessati dalla disabilitazione di Gruppi di disponibilità Always On.  
  
 Se si disabilita in modo permanente Gruppi di disponibilità Always On su ogni istanza del server che ospita una replica di disponibilità per uno o più gruppi di disponibilità, si consiglia di completare i passaggi seguenti:  
  
1.  Se le repliche di disponibilità locali non sono state rimosse prima di disabilitare Always On, eliminare ogni gruppo di disponibilità per il quale l'istanza del server ospita una replica di disponibilità. Per informazioni sull'eliminazione di un gruppo di disponibilità, vedere [Rimuovere un gruppo di disponibilità &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-an-availability-group-sql-server.md).  
  
2.  Per rimuovere i metadati rimanenti, eliminare ogni gruppo di disponibilità interessato su un'istanza del server che fa parte del cluster WSFC originale.  
  
3.  Tutti i database primari continuano a essere accessibili a tutte le connessioni, ma la sincronizzazione dei dati tra i database primario e secondario viene arrestata.  
  
4.  Per i database secondari viene impostato lo stato RESTORING. È possibile eliminare i database o ripristinarli tramite RESTORE WITH RECOVERY. Tuttavia, i database ripristinati non fanno più parte della sincronizzazione dei dati del gruppo di disponibilità.  
  
##  <a name="WhenCmdletRestartsSQL"></a> Situazioni in cui un cmdlet comporta il riavvio del servizio SQL Server  
 In un'istanza del server attualmente in esecuzione, l'uso di **Enable-SqlAlwaysOn** o **Disable-SqlAlwaysOn** per modificare l'impostazione Always On corrente può causare il riavvio del servizio SQL Server. Il comportamento del riavvio dipende dalle condizioni seguenti:  
  
|Specifica del parametro -NoServiceRestart|Specifica del parametro -Force|Riavvio del servizio [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|no|no|Per impostazione predefinita. Tuttavia dal cmdlet è richiesto quanto segue:<br /><br /> **Per completare l'azione, è necessario riavviare il servizio SQL Server per l'istanza del server '<nome_istanza>'. Continuare?**<br /><br /> **[Y] Sì [N] No [S] Sospendi [?] Guida (l'impostazione predefinita è "Y"):**<br /><br /> Se si specifica **N** o **S**, il servizio non viene riavviato.|  
|no|Sì|Servizio riavviato.|  
|Sì|no|Servizio non riavviato.|  
|Sì|Sì|Servizio non riavviato.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

