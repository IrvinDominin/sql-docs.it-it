---
title: "Lezione 1: Connessione al Motore di database | Microsoft Docs"
ms.custom: ""
ms.date: "08/05/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: e8db82f0-50ed-4531-9209-940006ed34cb
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Lezione 1: Connessione al Motore di database
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Gli strumenti che vengono installati con [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] dipendono dall'edizione in uso e dalle opzioni di installazione selezionate. In questa lezione vengono illustrati gli strumenti principali e vengono descritte le procedure per la connessione e l'esecuzione di una funzione di base, ovvero la concessione di autorizzazione ad altri utenti.  
  
In questa lezione sono incluse le attività seguenti:  
  
-   [Strumenti per iniziare](#tools)  
  
-   [Connessione con Management Studio](#connect)  
  
-   [Autorizzazione di connessioni aggiuntive](#additional)  
  
## <a name="tools"></a>Strumenti per iniziare  
In [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] è disponibile un'ampia gamma di strumenti. In questo argomento vengono illustrati i primi strumenti necessari e vengono fornite indicazioni utili per selezionare lo strumento appropriato per le operazioni da eseguire. A tutti gli strumenti è possibile accedere dal menu **Start**. Alcuni strumenti, quali [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], non vengono installati per impostazione predefinita. ma devono essere selezionati tra i componenti client durante l'installazione. Per una descrizione completa degli strumenti illustrati di seguito, eseguire una ricerca nella documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] contiene solo un subset degli strumenti.  
  
### Strumenti di base  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) è lo strumento principale per l'amministrazione di [!INCLUDE[ssDE](../includes/ssde-md.md)] e la scrittura di codice [!INCLUDE[tsql](../includes/tsql-md.md)]. È ospitato nella shell di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. SSMS è disponibile gratuitamente per il download nell'[Area download Microsoft](https://msdn.microsoft.com/library/mt238290.aspx). La versione più recente può essere usata con le versioni precedenti di [!INCLUDE[ssDE_md](../includes/ssde-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Gestione configurazione viene installato sia con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] che con gli strumenti client. Consente di abilitare protocolli server, configurare le opzioni relative ai protocolli quali le porte TCP, configurare i servizi server per l'avvio automatico e configurare i computer client per la connessione con le modalità preferite. Questo strumento consente di configurare gli elementi di connettività più avanzati ma non le funzionalità.  
  
### Database di esempio  
I database di esempio e gli esempi non sono inclusi in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Nella maggior parte degli esempi descritti nella documentazione online di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] viene usato il database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)].  
  
##### Per avviare SQL Server Management Studio  
  
- Nelle versioni correnti di Windows, nella pagina **iniziale** digitare SSMS e fare clic su **Microsoft SQL Server Management Studio**.  
-   Se si usano versioni precedenti di Windows, dal menu **Start** scegliere **Tutti i programmi**, fare clic su [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], quindi su **SQL Server Management Studio**.  
  
##### Per avviare Gestione configurazione SQL Server  
  
- Nelle versioni correnti di Windows, nella pagina **iniziale** digitare **Gestione configurazione** e quindi fare clic su *Gestione configurazione** *SQL Server *versione*.   
-   Se si usano versioni precedenti di Windows, dal menu **Start** scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)], **Strumenti di configurazione** e quindi fare clic su **Gestione configurazione SQL Server**.  
  
## <a name="connect"></a>Connessione con Management Studio  
La connessione a [!INCLUDE[ssDE](../includes/ssde-md.md)] dagli strumenti in esecuzione nello stesso computer risulta semplice se si conosce il nome dell'istanza e se si esegue la connessione con un account membro del gruppo Administrators locale nel computer. Le procedure illustrate di seguito devono essere eseguite nello stesso computer che ospita [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
> Questo argomento descrive la connessione a SQL Server locale. Per connettersi al database SQL di Azure, vedere [Connettersi al database SQL con SQL Server Management Studio ed eseguire una query T-SQL di esempio](https://azure.microsoft.com/documentation/articles/sql-database-connect-query-ssms/).  
  
##### Per determinare il nome dell'istanza del Motore di database  
  
1.  Accedere a Windows come membro del gruppo Administrators e aprire [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Nella finestra di dialogo **Connetti al server** fare clic su **Annulla**.  
  
3.  Se Server registrati non è visualizzato, scegliere **Server registrati** dal menu **Visualizza**.  
  
4.  Dopo avere selezionato **Motore di database** nella barra degli strumenti Server registrati, espandere **Motore di database**, fare clic con il pulsante destro del mouse su **Gruppi di server locali**, scegliere **Attività** e quindi fare clic su **Registra server locali**. Verranno visualizzate tutte le istanze di [!INCLUDE[ssDE](../includes/ssde-md.md)] installate nel computer, L'istanza predefinita non è denominata e viene visualizzata come nome del computer. Un'istanza denominata viene visualizzata come nome del computer seguito da una barra rovesciata (\\) e dal nome dell'istanza. Per [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], l'istanza è denominata *<nome_computer>*\sqlexpress, se non è stato specificato un nome diverso durante l'installazione.  
  
##### Per verificare che il Motore di database sia in esecuzione  
  
1.  In Server registrati, se accanto al nome dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è presente un punto verde con una freccia bianca, [!INCLUDE[ssDE](../includes/ssde-md.md)] è in esecuzione e non sono necessarie ulteriori operazioni.  
  
2.  Se accanto al nome dell'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] è presente un punto rosso con un quadrato bianco, [!INCLUDE[ssDE](../includes/ssde-md.md)] non è in esecuzione. Fare clic con il pulsante destro del mouse sul nome del [!INCLUDE[ssDE](../includes/ssde-md.md)], selezionare **Controllo servizi** e quindi fare clic su **Avvia**. Dopo la visualizzazione di una finestra di conferma, dovrebbe venir avviato il [!INCLUDE[ssDE](../includes/ssde-md.md)] e il cerchio dovrebbe diventare verde con una freccia bianca.  
  
##### Per connettersi al Motore di database  

È stato selezionato almeno un account Administrator durante l'installazione di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)]. Attenersi alla seguente procedura mentre si è connessi a Windows come amministratore.
  
1.  In [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] scegliere **Connetti Esplora oggetti** dal menu **File**.  
  
    Viene visualizzata la finestra di dialogo **Connetti al server**. Nella casella **Tipo di server** viene visualizzato l'ultimo tipo di componente usato.  
  
2.  Selezionare **Motore di database**.  

    ![object-explorer](../relational-databases/media/object-explorer.png)
  
3.  Nella casella **Nome server** digitare il nome dell'istanza del [!INCLUDE[ssDE](../includes/ssde-md.md)]. Per l'istanza predefinita di SQL Server il nome del server è il nome del computer. Per un'istanza denominata di SQL Server, il nome del server è *<nome_computer>***\\***<nome_istanza>,* ad esempio **ACCTG_SRVR\SQLEXPRESS**. La schermata seguente mostra la connessione all'istanza predefinita (non denominata) di [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] in un computer denominato 'PracticeComputer'. L'utente attualmente connesso a Windows è Mary dal dominio Contoso. Quando si usa l'autenticazione di Windows non è possibile modificare il nome utente. 

    ![connect-to-server](../relational-databases/media/connect-to-server.png)
  
4.  Fare clic su **Connetti**.  

> [!NOTE]
> In questa esercitazioni si presuppone che non si abbia familiarità con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e che non si abbiano particolari problemi di connessione. Questa esercitazione è semplice e dovrebbe essere sufficiente per la maggior parte degli utenti. Per istruzioni dettagliate per la risoluzione dei problemi, vedere [Risolvere i problemi di connessione al motore di database di SQL Server](../database-engine/configure-windows/troubleshoot-connecting-to-the-sql-server-database-engine.md). 
  
## <a name="additional"></a>Autorizzazione di connessioni aggiuntive  
Dopo avere stabilito la connessione a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] come amministratore, una delle prime attività da svolgere consiste nell'autorizzare altri utenti a connettersi. A questo scopo è necessario creare un account di accesso e autorizzare tale account ad accedere a un database come utente. È possibile configurare account di accesso con autenticazione di Windows, che utilizzano le credenziali di Windows, o account di accesso con autenticazione di SQL Server, che archiviano le informazioni autenticate in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e sono indipendenti dalle credenziali di Windows. Se possibile, utilizzare l'autenticazione di Windows.

> [!TIP]
> La maggior parte delle organizzazioni include utenti di dominio e usa l'autenticazione di Windows. È possibile provare per conto proprio creando altri utenti locali nel computer in uso. Poiché l'autenticazione degli utenti locali verrà eseguita dal computer, il dominio corrisponde al nome del computer. Ad esempio, se il nome del computer è `MyComputer` e si crea un utente denominato `Test`, la descrizione di Windows dell'utente è `Mycomputer\Test`.  
  
##### Creazione di un account di accesso con autenticazione di Windows  
  
1.  Nell'attività precedente è stata eseguita la connessione a [!INCLUDE[ssDE](../includes/ssde-md.md)] utilizzando [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]. In Esplora oggetti espandere l'istanza del server, espandere **Sicurezza**, fare clic con il pulsante destro del mouse su **Account di accesso** e quindi scegliere **Nuovo account di accesso**.  
  
    Viene visualizzata la finestra di dialogo **Account di accesso - Nuovo**.  
  
2.  Nella casella **Nome account di accesso** della pagina **Generale** digitare un account di accesso di Windows nel formato: `<domain>\\<login>`
  
    ![new-login](../relational-databases/media/new-login.png)
  
3.  Nella casella **Database predefinito** selezionare [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)], se disponibile. In caso contrario, selezionare **master**.  
  
4.  Se il nuovo account di accesso sarà un account di amministrazione, selezionare **sysadmin** nella pagina **Ruoli del server**, altrimenti lasciare vuota la casella.  
  
5.  Nella pagina **Mapping utenti** selezionare **Mapping** per il database [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)], se disponibile. In caso contrario, selezionare **master**. Si noti che la casella **Utente** viene popolata con l'account di accesso. Alla chiusura della finestra di dialogo, nel database verrà creato questo utente.  
  
6.  Nella casella **Schema predefinito** digitare **dbo** per eseguire il mapping dell'account di accesso allo schema del proprietario del database.  
  
7.  Accettare le impostazioni predefinite delle caselle **Entità a protezione diretta** e **Stato** e fare clic su **OK** per creare l'account di accesso.  
  
> [!IMPORTANT]  
> Si tratta delle informazioni di base necessarie per iniziare. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] offre un ambiente di sicurezza avanzato e la sicurezza rappresenta un aspetto certamente importante nell'uso dei database.  
  
## Lezione successiva  
[Lezione 2: Connessione da un altro computer](../relational-databases/lesson-2-connecting-from-another-computer.md)  
  
  
  