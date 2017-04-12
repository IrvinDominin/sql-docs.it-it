---
title: "Creare RSExecRole | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RSExecRole"
ms.assetid: 7ac17341-df7e-4401-870e-652caa2859c0
caps.latest.revision: 23
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 23
---
# Creare RSExecRole
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] viene utilizzato un ruolo del database predefinito denominato **RSExecRole** che consente di concedere autorizzazioni del server di report al database relativo. Il ruolo **RSExecRole** viene creato automaticamente con il database del server di report. Si consiglia di non modificare mai né di assegnare utenti a tale ruolo. Quando si sposta un database del server di report in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di [!INCLUDE[ssDE](../../includes/ssde-md.md)] nuovo o diverso, è necessario tuttavia creare nuovamente il ruolo nei database di sistema master e MSDB.  
  
 Utilizzando le istruzioni indicate di seguito, verranno effettuate le operazioni seguenti:  
  
-   Creazione ed esecuzione del provisioning di **RSExecRole** nel database di sistema master.  
  
-   Creazione ed esecuzione del provisioning di **RSExecRole** nel database di sistema MSDB.  
  
> [!NOTE]  
>  Le istruzioni contenute in questo argomento sono destinate agli utenti che non desiderano eseguire uno script o scrivere codice WMI per effettuare il provisioning del database del server di report. Se si gestisce una distribuzione di dimensioni elevate e i database verranno spostati regolarmente, è consigliabile scrivere uno script per automatizzare questi passaggi. Per altre informazioni, vedere [Accedere al provider WMI per Reporting Services](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
## Prima di iniziare  
  
-   Eseguire il backup delle chiavi di crittografia in modo che sia possibile ripristinarle dopo che il database è stato spostato. Questo passaggio non influisce direttamente sulla possibilità di creare e di effettuare il provisioning di **RSExecRole**, ma è necessario disporre di una copia di backup delle chiavi per verificare il proprio lavoro. Per altre informazioni, vedere [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md).  
  
-   Verificare di avere eseguito l'accesso con un account utente che dispone delle autorizzazioni **sysadmin** sull'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Verificare che il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sia installato e che sia in esecuzione nell'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] che si intende utilizzare.  
  
-   Collegare i database reportservertempdb e reportserver. Non è necessario collegare i database per creare il ruolo effettivo, ma è necessario che siano collegati prima che sia possibile eseguire il test del proprio lavoro.  
  
 Le istruzioni per la creazione manuale di **RSExecRole** devono essere utilizzate nel contesto dell'esecuzione della migrazione di un'installazione del server di report. Attività importanti come l'esecuzione del backup e lo spostamento del database del server di report non vengono descritte in questo argomento, ma nella documentazione del Motore di database.  
  
## Creazione di RSExecRole nel database master  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporti operazioni pianificate, in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono utilizzate stored procedure estese. I passaggi seguenti illustrano come concedere autorizzazioni di esecuzione per le procedure al ruolo **RSExecRole** .  
  
#### Per creare RSExecRole nel database di sistema master mediante Management Studio  
  
1.  Avviare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] , quindi connettersi all'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in cui è ospitato il database del server di report.  
  
2.  Aprire **Database**.  
  
3.  Aprire **Database di sistema**.  
  
4.  Aprire **Master**.  
  
5.  Aprire **Sicurezza**.  
  
6.  Aprire **Ruoli**.  
  
7.  Fare clic con il pulsante destro del mouse su **Ruoli del database**, quindi scegliere **Nuovo ruolo database**. Verrà visualizzata la pagina Generale.  
  
8.  In **Nome ruolo**digitare **RSExecRole**.  
  
9. In **Proprietario**digitare **DBO**.  
  
10. Fare clic su **Entità a sicurezza diretta**.  
  
11. Fare clic su **Cerca**. Verrà visualizzata la finestra di dialogo **Aggiungi oggetti** . L'opzione **Specifica oggetti** è selezionata per impostazione predefinita.  
  
12. Scegliere **OK**. Verrà visualizzata la finestra di dialogo **Seleziona oggetti** .  
  
13. Fare clic su **Tipi di oggetti**.  
  
14. Fare clic su **Stored procedure estese**.  
  
15. Scegliere **OK**.  
  
16. Fare clic su **Sfoglia**.  
  
17. Scorrere l'elenco delle stored procedure estese e selezionare gli elementi seguenti:  
  
    1.  xp_sqlagent_enum_jobs  
  
    2.  xp_sqlagent_is_starting  
  
    3.  xp_sqlagent_notify  
  
18. Fare clic su **OK**, quindi fare di nuovo clic su **OK** .  
  
19. Nella colonna **Concedi** della riga **Esegui** selezionare la casella di controllo, quindi fare clic su **OK**.  
  
20. Ripetere il passaggio per ognuna delle stored procedure rimanenti. A**RSExecRole** devono essere concesse le autorizzazioni di esecuzione per tutte le tre stored procedure.  
  
 ![Pagina Proprietà ruolo database](../../reporting-services/security/media/rsexecroledbproperties.gif "Pagina Proprietà ruolo database")  
  
## Creazione di RSExecRole nel database MSDB  
 Per supportare operazioni pianificate, in Reporting Services vengono utilizzate le stored procedure per il servizio SQL Server Agent e le informazioni sul processo vengono recuperate dalle tabelle di sistema. I passaggi seguenti illustrano come concedere autorizzazioni di esecuzione per le procedure e autorizzazioni di selezione sulle tabelle a RSExecRole.  
  
#### Per creare RSExecRole nel database di sistema MSDB  
  
1.  Ripetere passaggi analoghi per concedere le autorizzazioni alle stored procedure e alle tabelle nel database MSDB. Per semplificare i passaggi, il provisioning delle stored procedure e delle tabelle verrà effettuato separatamente.  
  
2.  Aprire **MSDB**.  
  
3.  Aprire **Sicurezza**.  
  
4.  Aprire **Ruoli**.  
  
5.  Fare clic con il pulsante destro del mouse su **Ruoli del database**, quindi scegliere **Nuovo ruolo database**. Verrà visualizzata la pagina Generale.  
  
6.  In Nome ruolo digitare **RSExecRole**.  
  
7.  In Proprietario digitare **DBO**.  
  
8.  Fare clic su **Entità a sicurezza diretta**.  
  
9. Scegliere **Aggiungi**. Verrà visualizzata la finestra di dialogo **Aggiungi oggetti** . L'opzione **Specifica oggetti** è selezionata per impostazione predefinita.  
  
10. Scegliere **OK**.  
  
11. Fare clic su **Tipi di oggetti**.  
  
12. Fare clic su **Stored procedure**.  
  
13. Scegliere **OK**.  
  
14. Fare clic su **Sfoglia**.  
  
15. Scorrere l'elenco degli elementi e selezionare gli elementi seguenti:  
  
    1.  sp_add_category  
  
    2.  sp_add_job  
  
    3.  sp_add_jobschedule  
  
    4.  sp_add_jobserver  
  
    5.  sp_add_jobstep  
  
    6.  sp_delete_job  
  
    7.  sp_help_category  
  
    8.  sp_help_job  
  
    9. sp_help_jobschedule  
  
    10. sp_verify_job_identifiers  
  
16. Fare clic su **OK**, quindi fare di nuovo clic su **OK** .  
  
17. Selezionare la prima stored procedure, ovvero sp_add_category.  
  
18. Nella colonna **Concedi** della riga **Esegui** selezionare la casella di controllo, quindi fare clic su **OK**.  
  
19. Ripetere il passaggio per ognuna delle stored procedure rimanenti. A RSExecRole devono essere concesse le autorizzazioni di esecuzione per tutte le dieci stored procedure.  
  
20. Nella scheda Entità a sicurezza diretta fare clic nuovamente su **Aggiungi** . Verrà visualizzata la finestra di dialogo **Aggiungi oggetti** . L'opzione **Specifica oggetti** è selezionata per impostazione predefinita.  
  
21. Scegliere **OK**.  
  
22. Fare clic su **Tipi di oggetti**.  
  
23. Fare clic su **Tabelle**.  
  
24. Scegliere **OK**.  
  
25. Fare clic su **Sfoglia**.  
  
26. Scorrere l'elenco degli elementi e selezionare gli elementi seguenti:  
  
    1.  syscategories  
  
    2.  sysjobs  
  
27. Fare clic su **OK**, quindi fare di nuovo clic su **OK** .  
  
28. Selezionare la prima tabella, ovvero syscategories.  
  
29. Nella colonna **Concedi** della riga **Seleziona** selezionare la casella di controllo, quindi fare clic su **OK**.  
  
30. Ripetere il passaggio per la tabella sysjobs. A RSExecRole devono essere concesse le autorizzazioni di selezione per entrambe le tabelle.  
  
## Spostamento del database del server di report  
 Dopo avere creato i ruoli, è possibile spostare il database del server di report in una nuova istanza di SQL Server. Per altre informazioni, vedere [Spostamento di database del server di report in un altro computer &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md).  
  
 L'aggiornamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)] a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]può essere eseguito prima o dopo lo spostamento del database.  
  
 Il database del server di report verrà aggiornato automaticamente a [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] quando il server di report si connette al database stesso. Non sono necessari passaggi specifici per aggiornare il database.  
  
## Ripristino delle chiavi di crittografia e verifica del lavoro  
 Se i database del server di report sono stati collegati, è possibile completare i passaggi seguenti per verificare il lavoro.  
  
#### Per verificare il funzionamento del server di report dopo uno spostamento del database  
  
1.  Avviare lo strumento di configurazione di Reporting Services e connettersi al server di report.  
  
2.  Fare clic su **Database**.  
  
3.  Fare clic su **Cambia database**.  
  
4.  Fare clic su **Scegli un database del server di report esistente**.  
  
5.  Immettere il nome del server del Motore di database. Se i database del server di report sono stati collegati a un'istanza denominata, è necessario digitare il nome dell'istanza nel formato <nomeserver>\>\\<nomeistanza\>.  
  
6.  Fare clic su **Test connessione**.  
  
7.  Scegliere **Avanti**.  
  
8.  In Database selezionare il database del server di report.  
  
9. Fare clic su **Avanti** e completare la procedura guidata.  
  
10. Fare clic su **Chiavi di crittografia**.  
  
11. Fare clic su **Ripristina**.  
  
12. Selezionare il file con nome sicuro (con estensione snk) in cui è presente la copia di backup della chiave simmetrica utilizzata per decrittografare le credenziali e le informazioni di connessione archiviate nel database del server di report.  
  
13. Immettere la password, quindi fare clic su **OK**.  
  
14. Fare clic su **URL Gestione report**.  
  
15. Fare clic sul collegamento per aprire Gestione report. Gli elementi del server di report dovrebbero essere visualizzati dal database del server di report.  
  
## Vedere anche  
 [Spostamento di database del server di report in un altro computer &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Creare un database del server di report in modalità nativa &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/create-a-native-mode-report-server-database-ssrs-configuration-manager.md)   
 [Eseguire il backup e il ripristino delle chiavi di crittografia di Reporting Services](../../reporting-services/install-windows/back-up-and-restore-reporting-services-encryption-keys.md)  
  
  