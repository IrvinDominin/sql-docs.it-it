---
title: Installare SQL Server Machine Learning Services (In-Database) in Windows | Microsoft Docs
description: R in SQL Server o Python in SQL Server è disponibile quando si installa Servizi Machine Learning di SQL Server 2017 in Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 330c21e6eb256bfe398bc707852eb9a66a183fb7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142661"
---
# <a name="install-sql-server-machine-learning-services-on-windows"></a>Installare SQL Server Machine Learning Services in Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

A partire da SQL Server 2017, R e Python supportano per analitica nel database viene fornito in SQL Server Machine Learning Services, il successore [SQL Server R Services](../r/sql-server-r-services.md) introdotta in SQL Server 2016. Librerie di funzioni sono disponibili in R e Python ed eseguire come script esterni in un'istanza del motore di database. 

Questo articolo illustra come installare il componente di machine learning tramite l'esecuzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installazione guidata e segue il le istruzioni visualizzate.

## <a name="bkmk_prereqs"> </a> Elenco di controllo pre-installazione

+ Installazione SQL Server 2017 (o versione successiva) è obbligatorio se si desidera installare servizi di Machine Learning con supporto del linguaggio R, Python o Java. Se invece si dispone di supporto di installazione di SQL Server 2016, è possibile installare [SQL Server 2016 R Services (In-Database)](sql-r-services-windows-install.md) per ottenere supporto del linguaggio R.

+ È necessaria un'istanza di motore di database. È possibile installare solo le funzionalità R o Python, anche se è possibile aggiungerli in modo incrementale a un'istanza esistente.

- L'installazione di servizi di Machine Learning è *non è supportato* in un cluster di failover in SQL Server 2017. Tuttavia, si *è supportata* con SQL Server 2019. 
 
+ Non installare servizi di Machine Learning in un controller di dominio. La parte di servizi di Machine Learning del programma di installazione avrà esito negativo.

+ Non installare **funzionalità condivise** > **Machine Learning Server (Standalone)** nello stesso computer che esegue un'istanza nel database. Un server autonomo verrà si contendono le risorse stesse, compromettendo le prestazioni di entrambe le installazioni.

+ Installazione side-by-side con altre versioni di R e Python è supportata ma non consigliata. È supportata perché istanza di SQL Server Usa una proprio copie delle distribuzioni open source R e Anaconda. Ma non è consigliabile perché l'esecuzione del codice che usa R e Python nel computer SQL Server all'esterno di SQL Server può causare problemi diversi:
    
  + Si usa una libreria diversa e un diverso eseguibile e ottengano risultati diversi, rispetto a quando si eseguono in SQL Server.
  + Gli script R e Python in esecuzione nelle librerie esterne non possono essere gestiti da SQL Server, causando una contesa delle risorse.
  
> [!IMPORTANT]
> Al termine dell'installazione, assicurarsi di completare i passaggi di post-configurazione descritti in questo articolo. Tali passaggi includono l'abilitazione di SQL Server per usare gli script esterni e l'aggiunta di account necessari per SQL Server eseguire processi R e Python per tuo conto. Le modifiche alla configurazione in genere richiedono un riavvio dell'istanza o un riavvio del servizio Launchpad.

## <a name="get-the-installation-media"></a>Ottenere il supporto di installazione

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Esecuzione del programma di installazione

Per le installazioni locali è necessario eseguire il programma di installazione come amministratore. Se si installa [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da una condivisione remota, è necessario utilizzare un account di dominio con autorizzazioni di lettura ed esecuzione relative a tale condivisione.

1. Avviare l'installazione guidata di SQL Server 2017. È possibile scaricare 
  
2. Nel **installazione** scheda, seleziona **nuova installazione SQL Server autonomo o aggiungere caratteristiche a un'installazione esistente**.

   ![Installazione di Machine Learning Services nel database](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Nella pagina **Selezione funzionalità** selezionare queste opzioni:
  
    -   **Servizi motore di database**
  
         Per usare R e Python con SQL Server, è necessario installare un'istanza del motore di database. È possibile usare un valore predefinito o un'istanza denominata.
  
    -   **Machine Learning Services (In-Database)**
  
         Questa opzione per installare i servizi di database che supportano R e l'esecuzione di script Python.

    -   **R**

        Selezionare questa opzione per aggiungere i pacchetti Microsoft R, interprete e open source R. 

    -   **Python**

        Selezionare questa opzione per aggiungere i pacchetti Python di Microsoft, il file eseguibile Python 3.5 e selezionare la distribuzione Anaconda librerie.
        
        ![Opzioni per R e Python delle funzionalità](media/2017setup-features-page-mls-rpy.png "opzioni di installazione per Python")

        > [!NOTE]
        > 
        > Non selezionare l'opzione **Machine Learning Server (Standalone)**. L'opzione di installazione di Machine Learning Server sotto **Caratteristiche condivise** è destinato all'uso in un computer separato.

4. Nel **fornire il consenso per installare R** pagina, selezionare **Accept**. Il contratto di licenza include Microsoft R Open, che include una distribuzione di pacchetti R open source di base e strumenti, insieme a pacchetti R avanzati e provider di connettività dal team di sviluppo Microsoft.

5. Nel **fornire il consenso per installare Python** pagina, selezionare **Accept**. Il contratto di licenza open source di Python include inoltre Anaconda e strumenti correlati, nonché alcune nuove librerie Python dal team di sviluppo Microsoft.
     
     ![Contratto di licenza di Python](media/2017setup-python-license.png "licenza contratto per Python")
  
    > [!NOTE]
    >  Se il computer in che uso non ha accesso a internet, è possibile sospendere il programma di installazione in questo momento per scaricare i programmi di installazione separatamente. Per altre informazioni, vedere [installa i componenti di apprendimento automatico senza accesso a internet](../install/sql-ml-component-install-without-internet-access.md).
  
     Selezionare **Accept**, attendere finché il **successiva** pulsante diventa attivo e quindi selezionare **Avanti**.
  
6. Nel **pronto per l'installazione** pagina, verificare che queste selezioni sono incluse e selezionare **installare**.
  
    + Servizi motore di database
    + Machine Learning Services (In-Database)
    + R o Python oppure entrambi

    Nota del percorso della cartella nel percorso `..\Setup Bootstrap\Log` in cui sono archiviati i file di configurazione. Una volta completato il programma di installazione, è possibile esaminare i componenti installati nel file di riepilogo.

7. Al termine dell'installazione, se viene richiesto di riavviare il computer, farlo ora. È importante leggere il messaggio visualizzato nell'Installazione guidata al termine dell'installazione. Per altre informazioni, vedere [Visualizzare e leggere i file di log del programma di installazione di SQL Server](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

<a name="bkmk_enableFeature"></a>

## <a name="enable-script-execution"></a>Abilitare l'esecuzione di script

1. Aprire [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > È possibile scaricare e installare la versione appropriata da questa pagina: [scaricare SQL Server Management Studio (SQL Server Management Studio)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > È anche possibile provare la versione di anteprima dei [Studio di Azure Data](../../azure-data-studio/what-is.md), che supporta le attività amministrative e query su SQL Server.
  
2. Connettersi all'istanza in cui è installato Servizi di Machine Learning, fare clic su **nuova Query** per aprire una finestra query ed eseguire il comando seguente:

   ```SQL
   sp_configure
   ```

    A questo punto, il valore della proprietà `external scripts enabled` deve essere **0**. Ciò avviene perché la funzionalità è disattivata per impostazione predefinita. La funzionalità deve essere abilitata in modo esplicito da un amministratore prima di poter eseguire script R o Python.
    
3.  Per abilitare la funzionalità di script esterne, eseguire l'istruzione seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Se è già stata abilitata la funzionalità per il linguaggio R, non vengono eseguiti riconfigurare una seconda volta per Python. La piattaforma di estendibilità sottostante supporta entrambi i linguaggi.

## <a name="restart-the-service"></a>Riavviare il servizio.

Una volta completata l'installazione, riavviare il motore di database prima di procedere al successivo, consentendo l'esecuzione dello script.

Riavviare automaticamente anche il servizio viene riavviato correlato [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

È possibile riavviare il servizio utilizzando il pulsante destro del mouse **riavviare** comando per l'istanza di SQL Server Management Studio o tramite il **Services** pannello nel Pannello di controllo oppure usando [Gestione configurazione SQL Server ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Verificare l'installazione

Controllare lo stato di installazione dell'istanza nel [report personalizzati](../r/monitor-r-services-using-custom-reports-in-management-studio.md) o log di installazione.

Utilizzare la procedura seguente per verificare che tutti i componenti usati per avviare script esterni siano in esecuzione.

1. In SQL Server Management Studio, aprire una nuova finestra query ed eseguire il comando seguente:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Il valore di **run_value** dovrebbe ora essere impostato su 1.
    
2. Aprire il **Services** pannello o Gestione configurazione SQL Server e verificare **Launchpad di SQL Server service** è in esecuzione. È necessario un servizio per ogni istanza di motore di database con R o Python installato. Per altre informazioni sul servizio, vedere [framework di estendibilità](../concepts/extensibility-framework.md). 
   
3. Se Launchpad è in esecuzione, è necessario essere in grado di eseguire semplici script R e Python per verificare che il runtime di scripting esterno possa comunicare con SQL Server.

   Aprire una nuova **Query** finestra in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi eseguire uno script simile al seguente:
    
    + Per R
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Per Python
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

 **Risultati**

    Lo script può richiedere del tempo per l'esecuzione, la prima volta che viene caricato il runtime dello script esterno. I risultati dovrebbero essere simile al seguente:

    | hello |
    |----|
    | 1|


> [!NOTE]
> Le colonne o le intestazioni usate nello script di Python non vengono restituite, per impostazione predefinita. Per aggiungere nomi di colonna per l'output, è necessario specificare lo schema per il set di dati restituito. Eseguire questa operazione usando il parametro con risultati della stored procedure, le colonne di denominazione e specificando il tipo di dati SQL.
> 
> Ad esempio, è possibile aggiungere la riga seguente per generare un nome di colonna arbitrario: `WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Applicare gli aggiornamenti

È consigliabile applicare l'aggiornamento cumulativo più recente per il motore di database e i componenti di apprendimento automatico.

Sui dispositivi connessi a internet, gli aggiornamenti cumulativi vengono in genere applicati tramite Windows Update, ma è anche possibile usare i passaggi seguenti per gli aggiornamenti controllati. Quando si applica l'aggiornamento del motore di database, il programma di installazione esegue il pull gli aggiornamenti cumulativi per qualsiasi funzionalità di R o Python che è installato nella stessa istanza. 

Nei server disconnesso, sono necessarie operazioni aggiuntive. Per altre informazioni, vedere [installare nei computer senza accesso a internet > applicare aggiornamenti cumulativi](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Per iniziare è già installata un'istanza di linea di base: la versione iniziale di SQL Server 2017

2. Passare all'elenco di aggiornamenti cumulativi: [degli aggiornamenti di SQL Server 2017](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Selezionare l'aggiornamento cumulativo più recente. Un file eseguibile viene scaricato ed estratto automaticamente.

4. Eseguire il programma di installazione. Accettare le condizioni di licenza, quindi nella pagina Selezione funzionalità, esaminare le funzionalità per il quale vengono applicati aggiornamenti cumulativi. Verrà visualizzata ogni funzionalità installata per l'istanza corrente, incluse le funzionalità di machine learning. Programma di installazione scaricherà i file CAB necessari per aggiornare tutte le funzionalità.

  ![](media/cumulative-update-feature-selection.png)

5. Continuare la procedura guidata, accettando le condizioni di licenza per le distribuzioni R e Python. 

## <a name="additional-configuration"></a>Configurazione aggiuntiva

Se il passaggio di verifica dello script esterno ha esito positivo, è possibile eseguire comandi R o Python da SQL Server Management Studio, Visual Studio Code o qualsiasi altro client che può inviare istruzioni T-SQL al server.

Se è stato visualizzato un errore quando si esegue il comando, rivedere i passaggi di configurazione aggiuntive in questa sezione. Si potrebbe essere necessario effettuare altre configurazioni appropriate per il servizio o il database.

A livello di istanza, potrebbe includere un'ulteriore configurazione:

* [Configurare Windows firewall per le connessioni in ingresso](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Abilitare i protocolli di rete aggiuntivi](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Abilitare le connessioni remote](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)

Il database, potrebbe essere necessario gli aggiornamenti di configurazione seguenti:

* [Estendere le autorizzazioni predefinite per gli utenti remoti](#bkmk_configureAccounts)
* [Concedere l'autorizzazione per eseguire gli script esterni](#permissions-external-script)
* [Concedere l'accesso ai singoli database](#permissions-db)

> [!NOTE]
> Se è necessaria una configurazione aggiuntiva dipende dallo schema di sicurezza, in cui è installato SQL Server e come si prevede che gli utenti per connettersi al database ed eseguire gli script esterni. 

<a name="bkmk_configureAccounts"></a> 

###  <a name="enable-implied-authentication-for-sql-restricted-user-group-sqlrusergroup-account-group"></a>Abilitare l'autenticazione implicita per gruppo di account di gruppo di utenti limitati SQL (SQLRUserGroup)

Se è necessario eseguire gli script da un client di analisi scientifica dei dati remoti e si usa l'autenticazione di Windows, è necessaria per concedere agli account di lavoro in esecuzione R configurazione aggiuntiva e l'autorizzazione per accedere a processi Python il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza per tuo conto. Questo comportamento viene definito *l'autenticazione implicita*e viene implementata dal motore di database per supportare l'esecuzione sicura degli script esterni in SQL Server 2016 e SQL Server 2017.

> [!NOTE]
> Se si usa un' **account di accesso SQL** per l'esecuzione degli script in un contesto di calcolo di SQL Server, questo passaggio aggiuntivo non è obbligatorio.

1. Nelle [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], in Esplora oggetti, espandere **sicurezza**. Quindi fare doppio clic su **gli account di accesso**e selezionare **nuovo account di accesso**.
2. Nel **account di accesso - nuovo** finestra di dialogo **ricerca**.
3. Selezionare **tipi di oggetti**e selezionare **gruppi**. Cancellare tutto il resto.
4. Nelle **immettere il nome dell'oggetto da selezionare**, digitare *SQLRUserGroup*e selezionare **Controlla nomi**.
5. Il nome del gruppo locale associato al servizio Launchpad dell'istanza deve essere risolto in un nome simile a *nomeistanza\SQLRUserGroup*. Fare clic su **OK**.
6. Per impostazione predefinita, il gruppo viene assegnato per il **pubblica** ruolo, e dispone dell'autorizzazione per connettersi al motore di database.
7. Fare clic su **OK**.

In SQL Server 2017 e versioni precedenti, un numero di account utente di Windows locali viene creato allo scopo di eseguire attività con il token di sicurezza del [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] servizio. È possibile visualizzare questi account nel gruppo di utenti Windows **SQLRUserGroup**. Per impostazione predefinita, vengono creati 20 account di lavoro, che corrisponde in genere i processi più che sufficienti per l'esecuzione di script esterni. 

Questi account vengono usati come indicato di seguito. Quando un utente invia uno script Python o R da un client esterno, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attiva un account di lavoro disponibili, viene eseguito il mapping all'identità dell'utente chiamante ed esegue lo script per conto dell'utente. Lo script, che è in esecuzione esterna a SQL Server, è necessario recuperare dati o le risorse da SQL Server, la connessione a SQL Server richiede una procedura di accesso. Creazione di un accesso al database per **SQLRUserGroup** anche la connessione abbia esito positivo.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
In SQL Server 2019, account di lavoro vengono sostituiti con AppContainers, con i processi in esecuzione nel servizio Launchpad di SQL Server. Anche se gli account di lavoro non vengono più utilizzati, sono ancora necessari per aggiungere un account di accesso di database per **SQLRUsergroup** se è necessaria l'autenticazione in cui è inclusa. Proprio come gli account di lavoro non dispone di autorizzazioni di accesso, l'identità del servizio Launchpad non non entrambi. Creazione di un account di accesso per **SQLRUserGroup**, che è costituito il servizio Launchpad in questa versione, consente l'autenticazione implicita lavorare.
::: moniker-end

<a name="permissions-external-script"></a> 

### <a name="give-users-permission-to-run-external-scripts"></a>Concedere agli utenti l'autorizzazione per eseguire gli script esterni

Se è stato installato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] manualmente, mentre si eseguono gli script R o Python nella tua istanza di, è in genere eseguire gli script come amministratore. In questo modo, si dispone dell'autorizzazione implicita su varie operazioni e tutti i dati nel database.

La maggior parte degli utenti, tuttavia, si dispone di tali autorizzazioni con privilegi elevati. Ad esempio, gli utenti in un'organizzazione che usano account di accesso SQL per accedere al database in genere non è le autorizzazioni con privilegi elevate. Pertanto, per ogni utente che usa R o Python, è necessario concedere agli utenti di servizi di Machine Learning l'autorizzazione per eseguire gli script esterni in ogni database in cui viene utilizzata la lingua. Ecco come:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Autorizzazioni non sono specifiche del linguaggio di script supportato. In altre parole, non esistono livelli di autorizzazione separati per lo script R e lo script Python. Se è necessario mantenere separate le autorizzazioni per queste lingue, installare R e Python in istanze separate.

<a name="permissions-db"></a> 

### <a name="give-your-users-read-write-or-data-definition-language-ddl-permissions-to-databases"></a>Assegnare la definizione di lettura, scrittura o dati agli utenti le autorizzazioni di language (DDL) per database

Mentre un utente è in esecuzione gli script, l'utente potrebbe essere necessario leggere i dati da altri database. L'utente potrebbe essere necessario anche creare nuove tabelle per archiviare i risultati e scrivere dati nelle tabelle.

Per ogni account utente di Windows o account di accesso SQL che esegue gli script R o Python, verificare che abbia le autorizzazioni appropriate sul database specifico: `db_datareader`, `db_datawriter`, o `db_ddladmin`.

Ad esempio, il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] istruzione offre l'accesso SQL *MySQLLogin* i diritti per eseguire query T-SQL *ML_Samples* database. Per eseguire questa istruzione, l'account di accesso SQL deve essere già presente nel contesto di sicurezza del server.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Per altre informazioni sulle autorizzazioni incluse in ogni ruolo, vedere [ruoli a livello di Database](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Creare un'origine dati ODBC per l'istanza del client per l'analisi scientifica dei dati

È possibile creare una soluzione di machine learning in un computer client di analisi scientifica dei dati. Se è necessario eseguire il codice usando il computer SQL Server come contesto di calcolo, sono disponibili due opzioni: accedere all'istanza con un account di accesso SQL o utilizzando un Windows dell'account.

+ Per gli account di accesso SQL: assicurarsi che l'account di accesso disponga delle autorizzazioni appropriate per il database in cui si esegue la lettura dei dati. Questo scopo, è possibile aggiungere *connettersi a* e *seleziona* autorizzazioni, o aggiungendo l'account di accesso per il `db_datareader` ruolo. Per creare oggetti, assegnare `DDL_admin` diritti. Se è necessario salvare i dati in tabelle, aggiungere il `db_datawriter` ruolo.

+ Per l'autenticazione di Windows: si potrebbe essere necessario creare un'origine dati ODBC nel client di data science che specifica il nome dell'istanza e altre informazioni sulla connessione. Per altre informazioni, vedere [Amministrazione origine dati ODBC](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Delle ottimizzazioni suggerite

Ora che avete accertato il corretto funzionamento, si potrebbe anche voler ottimizzare il server per supportare l'apprendimento automatico o installazione pretrained modelli.

### <a name="add-more-worker-accounts"></a>Aggiungere altri account di lavoro

Se si prevede che molti utenti sia in esecuzione gli script contemporaneamente, è possibile aumentare il numero di account di lavoro assegnati al servizio Launchpad. Per altre informazioni, vedere [modificare il pool di account utente per SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Ottimizzare il server per l'esecuzione di script

Le impostazioni predefinite per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] il programma di installazione consentono di ottimizzare l'equilibrio tra il server per un'ampia gamma di servizi che sono supportati dal motore di database, che potrebbe includere estrazione, trasformazione e caricamento (ETL) dei processi, creazione di report, il controllo, e le applicazioni che usano [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei dati. Di conseguenza, le impostazioni predefinite, si noterà che le risorse per machine learning vengono talvolta limitate o limitate, in particolare nelle operazioni a elevato utilizzo di memoria.

Per garantire che i processi di machine learning sono la priorità e risorse assegnati in modo appropriato, è consigliabile utilizzare SQL Server Resource Governor per configurare un pool di risorse esterne. Potrebbe anche voler modificare la quantità di memoria allocata per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database o aumentare il numero di account che vengono eseguiti nel [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] servizio.

- Per configurare un pool di risorse per la gestione delle risorse esterne, vedere [creare un pool di risorse esterne](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Per modificare la quantità di memoria riservata per il database, vedere [opzioni di configurazione memoria Server](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- Per modificare il numero di account R che può essere avviata dal [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], vedere [modificare il pool di account utente per l'apprendimento](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Se si usa l'edizione Standard e sono privi di Resource Governor, è possibile utilizzare viste a gestione dinamica (DMV) e degli eventi estesi, nonché eventi di Windows, che consente di gestire le risorse del server di monitoraggio. Per altre informazioni, vedere [monitoraggio e gestione dei servizi R](../r/managing-and-monitoring-r-solutions.md) e [monitoraggio e gestione dei servizi Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installare pacchetti R aggiuntivi

Le soluzioni R create per SQL Server, è possono chiamare funzioni R di base, funzioni dai pacchetti proprietari installati con SQL Server e i pacchetti R di terze parti compatibile con la versione di R open source installati tramite SQL Server.

I pacchetti di SQL Server da usare devono essere installati nella libreria predefinita usata dall'istanza. Se si dispone di un'installazione separata di R nel computer, o se si installano pacchetti nelle librerie utente, sarà possibile usare questi pacchetti da T-SQL.

Il processo per l'installazione e la gestione dei pacchetti di R è diverso in SQL Server 2016 e SQL Server 2017. In SQL Server 2016, un amministratore del database è necessario installare pacchetti R che gli utenti devono avere. In SQL Server 2017, è possibile configurare i gruppi di utenti di condividere i pacchetti in un livello di database, o configurare i ruoli di database per consentire agli utenti di installare i propri pacchetti. Per altre informazioni, vedere [installare nuovi pacchetti R in SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="next-steps"></a>Passaggi successivi

Gli sviluppatori di R possono iniziare a usare alcuni semplici esempi e informazioni di base del funzionamento di R con SQL Server. Per il passaggio successivo, vedere i collegamenti seguenti:

+ [Esercitazione: Eseguire R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Esercitazione: Nel database analitica per gli sviluppatori di R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Gli sviluppatori di Python è possono imparare a usare Python con SQL Server seguendo queste esercitazioni:

+ [Esercitazione: Eseguire Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Esercitazione: Nel database analitica per sviluppatori Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Per visualizzare esempi di machine learning basate su scenari reali, vedere [di Machine learning esercitazioni](../tutorials/machine-learning-services-tutorials.md).
