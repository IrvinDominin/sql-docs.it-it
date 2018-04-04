---
title: Il programma di installazione e configurazione dei servizi di Python Machine Learning | Documenti Microsoft
ms.custom: 
ms.date: 12/20/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 9ecd54dcb1fe829c51e0e05346abf04d80af3cf9
ms.sourcegitcommit: 6bd21109abedf64445bdb3478eea5aaa7553fa46
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2018
---
# <a name="set-up-python-machine-learning-services-in-database"></a>Impostare Python Machine Learning Services (In-Database)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In questo articolo viene descritto come installare i componenti necessari per Python eseguendo il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata e seguendo le istruzioni interattive.

## <a name="machine-learning-options-in-sql-server-setup"></a>Apprendimento opzioni nel programma di installazione di SQL Server

Scegliere il **servizi di Machine Learning** funzionalità, quindi selezionare **Python** come linguaggio.

Il **Caratteristiche condivise** sezione contiene un'opzione di installazione separato, **Machine Learning Server (Standalone)**. Questa opzione supporta rendere operativo il codice Python in un server che non dispongono di SQL Server o che non richiede l'uso di contesti di calcolo di SQL Server. Di conseguenza, è consigliabile che si *non* installare questo nello stesso computer come un'istanza di SQL Server. In alternativa, installare Machine Learning Server (Standalone) in un computer separato.

Al termine dell'installazione, riconfigurare l'istanza per consentire l'esecuzione di script che usano un eseguibile esterno. Potrebbe essere necessario apportare ulteriori modifiche al server per supportare i carichi di lavoro di machine learning. Le modifiche alla configurazione in genere richiedono il riavvio dell'istanza o un riavvio del servizio Launchpad.

### <a name="prerequisites"></a>Prerequisiti

+ SQL Server 2017 è obbligatorio. Integrazione di Python non è supportata nelle versioni precedenti di SQL Server.
+ Assicurarsi di installare il motore di database. Per eseguire script Python nel database è necessaria un'istanza di SQL Server.
+ I prerequisiti vengono installati come parte dell'installazione componente Python.
+ Non è possibile installare apprendimento con i servizi di Python su un cluster di failover. Il meccanismo di sicurezza utilizzato per isolare i processi di Python non è compatibile con un ambiente cluster di failover di Windows Server.
   
  In alternativa, è possibile utilizzare la replica per copiare le tabelle necessarie a un'istanza di SQL Server autonomo che utilizza i servizi di Python. In alternativa, è possibile installare apprendimento con i servizi di Python su un computer autonomo che utilizza l'impostazione AlwaysOn e fa parte di un gruppo di disponibilità.

+ Installazione side-by-side con altre versioni di Python è possibile, perché l'istanza di SQL Server utilizza la propria copia della distribuzione Anaconda. Tuttavia, in esecuzione il codice che usa Python nel computer SQL Server all'esterno di SQL Server possono causare diversi problemi:
    
    - Si utilizza un diverso eseguibile e la libreria diversa e ottengano risultati diversi, rispetto a quando si eseguono in SQL Server.
    - Script Python in esecuzione in librerie esterne non può essere gestito da SQL Server, iniziali a una contesa di risorse.
  
> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare la procedura aggiuntiva di post-configurazione descritta in questo articolo. Tali passaggi includono l'abilitazione di SQL Server da usare gli script esterni e aggiungendo gli account necessari per SQL Server eseguire i processi di Python per proprio conto.

### <a name="unattended-installation"></a>Installazione automatica

Per eseguire un'installazione automatica, utilizzare le opzioni della riga di comando per l'installazione di SQL Server e gli argomenti specifici per Python. Per altre informazioni, vedere [Unattended installa di SQL Server con servizi di Python Machine Learning](unattended-installs-of-sql-server-python-services.md).

##  <a name="bkmk_installPythonInDatabase"></a> Passaggio 1: Installare di Machine Learning Services (In-Database) in SQL Server

1. Eseguire l'installazione guidata di SQL Server 2017.
  
2. Nel **installazione** , selezionare **nuova installazione SQL Server autonomo o aggiungere funzionalità a un'installazione esistente**.

    ![Installare Python nel database](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Nella pagina **Selezione funzionalità** selezionare queste opzioni:
  
    -   **Servizi motore di database**
  
         Per usare Python con SQL Server, è necessario installare un'istanza del motore di database. È possibile utilizzare un valore predefinito o un'istanza denominata.
  
    -   **Machine Learning Services (In-Database)**
  
         Questa opzione consente di installare servizi di database che supportano l'esecuzione di script Python.

    -   **Python** selezionare questa opzione per ottenere il file eseguibile 3.5 Python e selezionare le raccolte dalla distribuzione Anaconda. Installare un solo linguaggio per ogni istanza.
        
        ![Funzionalità di opzioni per Python](media/ml-svcs-features-python-highlight.png "opzioni di installazione per Python")

        > [!NOTE]
        > 
        > Non si seleziona l'opzione per **Machine Learning Server (Standalone)**. L'opzione per installare Virtual Server Learning sotto **Caratteristiche condivise di** è destinata all'utilizzo in un computer separato. Ad esempio, si potrebbero voler installare la stessa versione di machine learning componenti in un computer diverso che viene utilizzato per lo sviluppo di progetti, ad esempio portatili dell'esperto di dati.

4. Nel **fornire il consenso per installare Python** pagina, selezionare **Accept**.
  
     Per scaricare l'eseguibile, Python pacchetti Python da Anaconda, è necessario il contratto di licenza.
     
     ![Contratto di licenza di Python](media/ml-svcs-license-python.png "contratto per Python di licenza")
  
    > [!NOTE]
    >  Se il computer in che uso non ha accesso a internet, è possibile sospendere l'installazione a questo punto per scaricare i programmi di installazione separatamente. Per altre informazioni, vedere [installazione dei componenti senza accesso a internet](../r/installing-ml-components-without-internet-access.md).
  
     Selezionare **Accept**, attendere finché il **successivo** pulsante diventa attiva e quindi selezionare **Avanti**.
  
5. Nel **pronto per l'installazione** verificare che le selezioni sono incluse e selezionare **installare**.
  
     + Servizi motore di database
     + Machine Learning Services (In-Database)
     + Python
  
    Queste selezioni rappresentano la configurazione minima necessaria per usare Python con [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)].
    
    ![Pronto per l'installazione di Python](media/ready-to-install-python.png "componenti obbligatori per l'installazione di Python")

    Facoltativamente, prendere nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completata l'installazione, è possibile esaminare i componenti installati nel file di riepilogo.

6. Al termine l'installazione, riavviare il computer.

##  <a name="bkmk_enableFeature"></a> Passaggio 2: Abilitare l'esecuzione di script Python

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima del [Studio operazioni SQL](https://docs.microsoft.com/sql/sql-operations-studio/what-is), che supporta le query su SQL Server e le attività amministrative.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito dall'amministratore prima di poter eseguire script R o Python.
    
3.  Per abilitare la funzionalità di scripting esterna che supporta Python, eseguire l'istruzione seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Se è già stata abilitata la funzionalità per il linguaggio R, non vengono eseguiti riconfigurare una seconda volta per Python. La piattaforma di estendibilità sottostante supporti entrambi i linguaggi.

4. Riavviare il servizio SQL Server per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Riavviare automaticamente anche il servizio SQL Server viene riavviato la correlate [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

    È possibile riavviare il servizio utilizzando il **Services** pannello nel Pannello di controllo oppure utilizzando [Gestione configurazione SQL Server](../../relational-databases/sql-server-configuration-manager.md).

## <a name="step-3-verify-that-the-external-script-execution-feature-is-running"></a>Passaggio 3: Verificare che la funzionalità di esecuzione dello script esterno sia in esecuzione

Richiedere qualche istante per verificare che tutti i componenti utilizzati per avviare lo script Python siano in esecuzione.

1. In SQL Server Management Studio, aprire una nuova finestra query ed eseguire il comando seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Il valore di **run_value** dovrebbe ora essere impostato su 1.
    
2. Aprire la **Services** pannello o Gestione configurazione SQL Server e verificare che il servizio Launchpad per l'istanza sia in esecuzione. Se la finestra di avvio non è in esecuzione, riavviare il servizio.
  
    Se è stato installato più istanze di SQL Server, qualsiasi istanza che ha R o Python abilitato ha il proprio servizio Launchpad.

    Se si installa R sia Python in una singola istanza, viene installato solo una finestra di avvio. Viene aggiunto un separato, specifici della lingua di visualizzazione della DLL per ogni lingua. Per altre informazioni, vedere [componenti per supportare l'integrazione di Python](new-components-in-sql-server-to-support-python-integration.md). 
   
3. Se è in esecuzione Launchpad, dovrebbe essere in grado di eseguire script Python semplici simile al seguente nelle [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'OutputDataSet = InputDataSet',
    @input_data_1 = N'SELECT 1 AS col'
    ```
    
    **Risultati**
    
    *<code>&nbsp;&nbsp;</code>* *1*

> [!NOTE]
> Le colonne o intestazioni utilizzate nello script Python non vengono restituite, per impostazione predefinita. Per aggiungere i nomi delle colonne per l'output, è necessario specificare lo schema per il set di dati restituito. Eseguire questa operazione usando il parametro con risultati della stored procedure, le colonne di denominazione e specificare il tipo di dati SQL.
> 
> Ad esempio, è possibile aggiungere la riga seguente per generare un nome di colonna arbitrario: `WITH RESULT SETS ((Col1 AS int))`

## <a name="step-4-additional-configuration"></a>Passaggio 4: Configurazione aggiuntiva

Se il comando precedente ha esito positivo, è possibile eseguire i comandi di Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL per il server.

Se si ha ricevuto un errore quando si esegue il comando, esaminare l'elenco seguente. Può accadere di dover creare configurazioni aggiuntive appropriate per il servizio o il database.

> [!NOTE]
> 
> Non tutte le modifiche elencate sono necessari e nessuno potrebbero essere necessarie. I requisiti dipendono lo schema di sicurezza, in cui è installato SQL Server e come si prevede che gli utenti per connettersi al database ed eseguire gli script esterni.

###  <a name="bkmk_configureAccounts"></a> Abilitare l'autenticazione implicita per gruppo di account di avvio

Durante l'installazione, vengono creati diversi nuovi account utente di Windows allo scopo di eseguire attività in base al token di sicurezza del servizio [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Quando un utente invia uno script Python o R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili. Quindi viene eseguito il mapping per l'identità dell'utente chiamante e viene eseguito lo script per conto dell'utente.

Questa operazione viene definita *l'autenticazione implicita*, senza che sia un servizio del motore di database. Questo servizio supporta l'esecuzione sicura di script esterni in SQL Server 2016 e SQL Server 2017.

È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione dello script esterno.

> [!IMPORTANT]
> Il gruppo di lavoro è denominato **SQLRUserGroup** anche se è installato R o Python. È un singolo gruppo per ogni istanza.

Se è necessario eseguire gli script da un client di analisi scientifica dei dati remoti e si utilizza l'autenticazione di Windows, esistono ulteriori considerazioni. Questi account di lavoro devono essere concessa l'autorizzazione per accedere al [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per proprio conto.

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Esplora oggetti, espandere **protezione**. Quindi fare doppio clic su **account di accesso**e selezionare **nuovo account di accesso**.
2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**.
3. Selezionare **tipi di oggetti**e selezionare **gruppi**. Cancellare tutto il resto.
4. In **immettere il nome dell'oggetto da selezionare**, tipo *SQLRUserGroup*e selezionare **Controlla nomi**.
5. Il nome del gruppo locale associato al servizio Launchpad dell'istanza deve essere risolto in un nome simile a *nomeistanza\SQLRUserGroup*. Fare clic su **OK**.
6. Per impostazione predefinita, il gruppo viene assegnato per il **pubblica** ruolo, e dispone dell'autorizzazione per connettersi al motore di database.
7. Fare clic su **OK**.

> [!NOTE]
> Se si usa un **account di accesso SQL** per l'esecuzione di script in un contesto di calcolo di SQL Server, questo passaggio aggiuntivo non è necessario.

### <a name="give-users-permission-to-run-external-scripts"></a>Consentire agli utenti di eseguire gli script esterni

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente, mentre si eseguono script Python in un'istanza personalizzata, è in genere eseguire gli script come amministratore. Pertanto, si dispone dell'autorizzazione implicita su varie operazioni e tutti i dati nel database.

La maggior parte degli utenti, sono necessario, tuttavia, tali autorizzazioni con privilegi elevati. Ad esempio, gli utenti in un'organizzazione che utilizzano account di accesso SQL per accedere al database in genere non dispone delle autorizzazioni con privilegi elevate. Pertanto, per ogni utente che sta utilizzando Python, è necessario concedere agli utenti di Machine Learning Services l'autorizzazione all'esecuzione di script esterni in ogni database in cui viene usato Python. Ecco come:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorizzazioni non sono specifiche del linguaggio di script supportato. In altre parole, non esistono livelli di autorizzazione separati per lo script R e script Python. Se è necessario mantenere separate le autorizzazioni per queste lingue, installare R e Python in istanze separate.

### <a name="give-your-users-read-write-or-data-definition-language-ddl-permissions-to-databases"></a>Assegnare la definizione di lettura, scrittura o dati agli utenti le autorizzazioni di language (DDL) per database

Mentre un utente è in esecuzione degli script, l'utente potrebbe essere necessario leggere i dati da altri database. L'utente potrebbe essere necessario anche creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente di Windows o account di accesso SQL che esegue gli script R o Python, verificare che abbia le autorizzazioni appropriate sul database specifico: `db_datareader`, `db_datawriter`, o `db_ddladmin`.

Ad esempio, il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione fornisce l'account di accesso SQL *MySQLLogin* i diritti per eseguire query T-SQL *ML_Samples* database. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per ulteriori informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).

### <a name="ensure-that-the-sql-server-installation-supports-remote-connections"></a>Verificare che l'installazione di SQL Server supporta le connessioni remote

Se non è possibile connettersi da un computer remoto, verificare se il firewall consenta l'accesso a SQL Server. In un'installazione predefinita, le connessioni remote potrebbero essere disabilitate o la porta utilizzata da SQL Server potrebbe essere bloccata dal firewall. Per altre informazioni, vedere [configurare Windows Firewall per l'accesso al motore di database](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).

### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

È possibile creare una soluzione in un computer client di analisi scientifica dei dati di apprendimento. Se è necessario eseguire il codice utilizzando il computer SQL Server come contesto di calcolo, sono disponibili due opzioni: accedere all'istanza utilizzando un account di accesso SQL, oppure utilizzando un account.

+ Per gli account di accesso SQL: verificare che l'account di accesso dispone delle autorizzazioni appropriate per il database in cui vengono letti i dati. Questo scopo, è possibile aggiungere *connettersi a* e *seleziona* autorizzazioni, o aggiungendo l'account di accesso per il `db_datareader` ruolo. Per creare oggetti, assegnare `DDL_admin` diritti. Se è necessario salvare i dati in tabelle, aggiungere il `db_datawriter` ruolo.

+ Per l'autenticazione di Windows: È necessario creare un'origine dati ODBC nel client di analisi scientifica dei dati che specifica il nome dell'istanza e altre informazioni di connessione. Per altre informazioni, vedere [Amministratore origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="additional-optimizations"></a>Ulteriori ottimizzazioni

Ora che si dispone di tutto, è inoltre possibile ottimizzare il server per supportare l'apprendimento automatico oppure installare pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si prevede che molti utenti sia in esecuzione script contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati per il servizio Launchpad. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Ottimizzare il server per l'esecuzione di script

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] programma di installazione di ottimizzare il bilanciamento del server per un'ampia gamma di servizi. Questi servizi includono ETL processi, creazione di report, il controllo e le applicazioni che utilizzano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dati.

Se si utilizzano le impostazioni predefinite, si noterà che le risorse per l'esecuzione di script esterni con restrizioni o limitate, in particolare nelle operazioni con utilizzo elevato della memoria. Se machine learning è una priorità, modificare le impostazioni di database predefinito per assicurarsi che i processi di script esterni sono priorità e assegnare in modo appropriato. Queste modifiche possono includere:

+ Riducendo la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database.
+ Aumentando il numero di account in esecuzione sotto il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio. Non aumentare il numero di risorse, ma determinano l'aumento del numero di script che possono essere eseguiti contemporaneamente.

Se si dispone di SQL Server Enterprise Edition, utilizzo di resource governor per configurare un pool di risorse esterne per Python. Per ulteriori informazioni, vedere gli articoli seguenti:

-   Configurare un pool di risorse per la gestione di risorse esterne
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)
  
-   Modificare la quantità di memoria riservata per il motore di database
  
     [Opzioni di configurazione server server memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md)
  
-   Modificare il numero di account di lavoro che può essere avviato [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
     [Modificare il pool di account utente per SQL Server R Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md)

Se si utilizza SQL Server Standard Edition e non dispongono di risorse, è possibile utilizzare viste a gestione dinamica e gli eventi estesi per gestire le risorse del server. È inoltre possibile utilizzare il monitoraggio degli eventi di Windows per questo scopo. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md).

### <a name="upgrade-the-machine-learning-components"></a>Eseguire l'aggiornamento di machine learning componenti

Quando si installa Servizi di Machine Learning tramite SQL Server 2017, ottenere la versione dei componenti al momento che la versione è stata pubblicata. Ogni volta che si patch o aggiornare l'istanza di SQL Server, i componenti di machine learning vengono aggiornati anche.

È possibile eseguire l'aggiornamento di machine learning componenti in una pianificazione più veloce rispetto a quelle supportate da versioni di SQL Server, installando Microsoft Machine Learning Server. Quando si esegue questa operazione, è anche possibile ottenere tutte le nuove funzionalità supportate nella versione più recente di Machine Learning Server, ad esempio:

+ Gli aggiornamenti ai pacchetti Python per [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package) e [microsoftml per Python](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package).
+ [Pretrained modelli](https://docs.microsoft.com/r-server/install/microsoftml-install-pretrained-models) per analisi di testo e classificazione delle immagini.

Per informazioni su come aggiornare un'istanza, vedere [i componenti di R aggiornamento tramite l'associazione](..\r\use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md).

### <a name="tutorials"></a>Esercitazioni

Vedere le esercitazioni seguenti per alcuni esempi di come è possibile utilizzare Python con SQL Server per compilare e distribuire soluzioni di machine learning:

[Utilizzo di Python in T-SQL](../tutorials/run-python-using-t-sql.md)

[Creare un modello di Python usando revoscalepy](../tutorials/use-python-revoscalepy-to-create-model.md)
