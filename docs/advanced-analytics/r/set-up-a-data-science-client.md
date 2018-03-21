---
title: Configurare un client di analisi scientifica dei dati per l'uso con SQL Server | Documenti Microsoft
ms.custom: 
ms.date: 10/31/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d15ee956-918f-40e0-b986-2bf929ef303a
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 160dae2d84c84aeaecaa07ec16be681fabde5534
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="set-up-a-data-science-client-for-use-with-sql-server"></a>Configurare un client di analisi scientifica dei dati per l'uso con SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dopo aver configurato un'istanza di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per supportare l'apprendimento automatico, è necessario impostare un ambiente di sviluppo in grado di connettersi al server per l'esecuzione remota e la distribuzione.

Questo articolo descrive alcuni scenari tipici del client, inclusa la configurazione dell'edizione gratuita Community di Visual Studio per eseguire codice R in SQL Server.

## <a name="install-r-libraries-on-the-client"></a>Installare le librerie di R nel client

L'ambiente client deve includere Microsoft R Open, oltre ai pacchetti RevoScaleR aggiuntivi che supportano l'esecuzione distribuita di R in SQL Server. Distribuzioni standard di R non dispone di pacchetti che supportano i contesti di calcolo remoto o l'esecuzione parallela delle attività di R.

Per ottenere queste librerie, installano una qualsiasi delle operazioni seguenti:
  
+ [Microsoft R Client](http://aka.ms/rclient/download)

+ Microsoft R Server (for SQL Server 2016)

    - Per installare dal programma di installazione di SQL Server, vedere [installazione di SQL Server 2016 R Server (Standalone)](../install/sql-r-standalone-windows-install.md)

    - Per usare il programma di installazione separato basati su Windows, vedere [installare Machine Learning per Windows ReportServer](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)

+ Machine Learning Server (per SQL Server 2017)

    - Per installare dal programma di installazione di SQL Server, vedere [installazione di SQL Server 2017 Machine Learning Server (Standalone)](../install/sql-machine-learning-standalone-windows-install.md)

    - Per usare il programma di installazione separato basati su Windows, vedere [installare R Server 9.1 per Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows)

## <a name="install-a-development-environment"></a>Installare un ambiente di sviluppo

Se si dispone già di un ambiente di sviluppo R preferito, è consigliabile una delle operazioni seguenti:

+ R Tools for Visual Studio

    Compatibile con Visual Studio 2015.

    Per informazioni sull'installazione, vedere [come installare gli strumenti R per Visual Studio](https://docs.microsoft.com/visualstudio/rtvs/installation).
 
    Per configurare RTVS usino le librerie client di Microsoft R, vedere [su Microsoft R Client](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client)

+ Visual Studio 2017

    Anche l'edizione gratuita Community include data science carico di lavoro, che installa i modelli di progetto per R, Python e F #.

    Scaricare Visual Studio dal [questo sito](https://www.visualstudio.com/vs/). 

+ RStudio

    Se si preferisce usare RStudio, sono necessari alcuni passaggi aggiuntivi per usare le librerie RevoScaleR:

    - Installare Microsoft R Client per ottenere i pacchetti richiesti e le librerie.
    - Aggiornare il percorso di R per utilizzare il runtime di Microsoft R.

    Per altre informazioni, vedere [Client R - configurare l'IDE](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client#step-2-configure-your-ide).

## <a name="configure-your-ide"></a>Configurare l'IDE

+ R Tools for Visual Studio

    Vedere [questo sito](https://docs.microsoft.com/visualstudio/rtvs/getting-started-with-r) per alcuni esempi di come compilare ed eseguire il debug R progetti mediante strumenti R per Visual Studio. 

+ Visual Studio 2017

    Se si installa Microsoft R Client o Server R **prima di** si installa Visual Studio, le librerie di R Server vengono automaticamente rilevate e utilizzate per il percorso della libreria. Se non è installato RevoScaleR raccolte dal **strumenti di R** dal menu **installa R Client**.

## <a name="run-r-in-sql-server"></a>Eseguire R in SQL Server

Questo esempio viene utilizzato Visual Studio 2017 Community Edition, con il carico di lavoro dell'analisi scientifica dei dati installato.

1. Dal **File** dal menu **New** e quindi selezionare **progetto**.

2. -L'icona della mano riquadro contiene un elenco di modelli preinstallati. Fare clic su **R**e selezionare **R progetto**. Nel **nome** , digitare `dbtest` e fare clic su **OK**.

3. Visual Studio crea una nuova cartella di progetto e un file di script predefinito, `Script.R`. 

4. Tipo `.libPaths()` nella prima riga dello script di file e quindi premere CTRL + INVIO.

5. Il percorso della libreria R corrente deve essere visualizzato nel **R interattivo** finestra. 

6. Fare clic sui **strumenti di R** dal menu **Windows** per visualizzare un elenco di altre finestre specifiche di R che è possibile visualizzare nell'area di lavoro.
 
    + Visualizzare la Guida per i pacchetti nella raccolta corrente premendo CTRL + 3.
    + Visualizzare le variabili di R nel **Explorer variabile**, premendo CTRL + 8.

7. Creare una stringa di connessione a un'istanza di SQL Server e utilizzare la stringa di connessione nel costruttore RxInSqlServer per creare un oggetto di origine dati di SQL Server. 

    ```r
    connStr <- "Driver=SQL Server;Server=MyServer;Database=MyTestDB;Uid=;Pwd="
    sqlShareDir <- paste("C:\\AllShare\\", Sys.getenv("USERNAME"), sep = "")
    sqlWait <- TRUE
    sqlConsoleOutput <- FALSE
    cc <- RxInSqlServer(connectionString = connStr, shareDir = sqlShareDir, wait = sqlWait, consoleOutput = sqlConsoleOutput)
    sampleDataQuery <- "SELECT TOP 100 * from [dbo].[MyTestTable]"
    inDataSource <- RxSqlServerData(sqlQuery = sampleDataQuery, connectionString = connStr, rowsPerRead = 500)
    ```

    > [!TIP]
    > Per eseguire un batch, selezionare le righe che si desidera eseguire, premere CTRL + INVIO.

8. Impostare il contesto di calcolo per il server e quindi eseguire il semplice codice R sui dati.

    ```r
    rxSetComputeContext(cc)
    rxGetVarInfo(data = inDataSource)
    ```

    I risultati vengono restituiti nel **R interattivo** finestra.
    
    Se si desidera assicurarsi che il codice è in esecuzione nell'istanza di SQL Server, è possibile utilizzare Profiler per creare una traccia.