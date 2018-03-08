---
title: Distribuire, eseguire e monitorare un pacchetto SSIS in Azure | Microsoft Docs
ms.date: 02/05/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: lift-shift
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bde92101af0b761df9f37171b35952fa3ab9d25b
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="deploy-run-and-monitor-an-ssis-package-on-azure"></a>Distribuire, eseguire e monitorare un pacchetto SSIS in Azure
Questa esercitazione illustra come distribuire un progetto di SQL Server Integration Services per il database del catalogo SSISDB nel database SQL di Azure, eseguire un pacchetto nel runtime di integrazione SSIS di Azure e monitorare il pacchetto in esecuzione.

## <a name="prerequisites"></a>Prerequisites

Prima di iniziare, verificare di avere la versione 17.2 o successiva di SQL Server Management Studio. Per scaricare la versione più recente di SSMS, vedere [Scaricare SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

Verificare inoltre se il database SSISDB è configurato e se è stato eseguito il provisioning del runtime di integrazione SSIS di Azure. Per informazioni su come eseguire il provisioning di SSIS in Azure, vedere [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal).

## <a name="connect-to-the-ssisdb-database"></a>Connettersi al database SSISDB

Usare SQL Server Management Studio per connettersi al catalogo SSIS nel server di database SQL di Azure. Per altre informazioni, vedere [Connettersi al database del catalogo SSISDB in Azure](ssis-azure-connect-to-catalog-database.md).

> [!IMPORTANT]
> Un server di database SQL di Azure è in ascolto sulla porta 1433. Se si tenta di connettersi a un server di database SQL di Azure dall'interno di un firewall aziendale, per stabilire correttamente la connessione questa porta deve essere aperta nel firewall aziendale.

1. Aprire SQL Server Management Studio.

2. **Connettersi al server**. Immettere le informazioni seguenti nella finestra di dialogo **Connetti al server**:

   | Impostazione       | Valore suggerito | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Nome completo del server | Il nome deve essere nel formato **mysqldbserver.database.windows.net**. Per sapere qual è il nome del server, vedere [Connettersi al database del catalogo SSISDB in Azure](ssis-azure-connect-to-catalog-database.md). |
   | **Autenticazione** | autenticazione di SQL Server | In questa guida rapida viene usata l'autenticazione SQL. |
   | **Account di accesso** | Account amministratore del server | Account specificato al momento della creazione del server. |
   | **Password** | Password per l'account amministratore del server | Password specificata al momento della creazione del server. |

3. **Connettersi al database SSISDB**. Selezionare **Opzioni** per espandere la finestra di dialogo **Connetti al server**. Nella finestra di dialogo **Connetti al server** espansa selezionare la scheda **Proprietà connessione**. Nel campo **Connetti al database** selezionare o immettere `SSISDB`.

4. Selezionare **Connetti**. In SSMS si apre la finestra Esplora oggetti. 

5. In Esplora oggetti espandere **Cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="deploy-a-project-with-the-deployment-wizard"></a>Distribuire un progetto con la procedura guidata

### <a name="start-the-integration-services-deployment-wizard"></a>Avviare la Distribuzione guidata Integration Services
1. In Esplora oggetti di SQL Server Management Studio, con il nodo **Cataloghi di Integration Services** e il nodo **SSISDB** espansi, espandere una cartella di progetto.

2.  Selezionare il nodo **Progetti**.

3.  Fare clic sul nodo **Progetti** e selezionare **Distribuzione progetto**. Si apre la Distribuzione guidata Integration Services. È possibile distribuire un progetto da un database del catalogo SSIS o dal file system.

### <a name="deploy-a-project-with-the-deployment-wizard"></a>Distribuire un progetto con la procedura guidata
1. Nella pagina **Introduzione** della distribuzione guidata leggere l'introduzione. Selezionare **Avanti** per aprire la pagina **Seleziona origine**.

2. Nella pagina **Seleziona origine** selezionare il progetto SSIS esistente da distribuire.
    -   Per distribuire un file di distribuzione del progetto creato, selezionare **File distribuzione progetto** e immettere il percorso al file con estensione ispac.
    -   Per distribuire un progetto che si trova in un catalogo SSIS, selezionare **Catalogo di Integration Services**, quindi immettere il nome del server e il percorso del progetto nel catalogo.
    -   Selezionare **Avanti** per visualizzare la pagina **Seleziona destinazione**.
  
3.  Nella pagina **Seleziona destinazione** selezionare la destinazione per il progetto.
    -   Immettere il nome completo del server nel formato `<server_name>.database.windows.net`.
    -   Selezionare **Sfoglia** per selezionare la cartella di destinazione in SSISDB.
    -   Selezionare **Avanti** per aprire la pagina **Verifica**.  
  
4.  Nella pagina **Verifica** rivedere le impostazioni selezionate.
    -   Per apportare modifiche alle impostazioni, selezionare **Indietro** o uno dei passaggi nel riquadro sinistro.
    -   Selezionare **Distribuisci** per avviare il processo di distribuzione.

    > ![NOTA] Se viene visualizzato il messaggio di errore **Nessun agente di lavoro attivo. (provider di dati SqlClient .Net)**, assicurarsi che il runtime di integrazione SSIS di Azure sia in esecuzione. Questo errore si verifica se si tenta di eseguire la distribuzione mentre il runtime di integrazione SSIS di Azure è arrestato.

5.  Al termine del processo di distribuzione viene visualizzata la pagina **Risultati**. Questa pagina consente di visualizzare l'esito positivo o negativo di ogni azione.
    -   Se l'azione ha avuto esito negativo, selezionare **Non riuscito** nella colonna **Risultato** per visualizzare una spiegazione dell'errore.
    -   In alternativa, selezionare **Salva report...** per salvare i risultati in un file XML.
    -   Per uscire dalla procedura guidata, fare clic su **Chiudi**.

## <a name="deploy-a-project-with-powershell"></a>Distribuire un progetto con PowerShell

Per distribuire un progetto con PowerShell in SSISDB nel database SQL di Azure, adattare lo script seguente secondo i propri requisiti. Lo script enumera le cartelle figlio in `$ProjectFilePath` e i progetti in ogni cartella figlio, quindi crea le stesse cartelle in SSISDB e distribuisce i progetti in tali cartelle.

Questo script richiede SQL Server Data Tools versione 17.x o SQL Server Management Studio installato nel computer in cui viene eseguito lo script.

```powershell
# Variables
$ProjectFilePath = "C:\<folder>"
$SSISDBServerEndpoint = "<servername>.database.windows.net"
$SSISDBServerAdminUserName = "<username>"
$SSISDBServerAdminPassword = "<password>"

# Load the IntegrationServices Assembly
[System.Reflection.Assembly]::LoadWithPartialName("Microsoft.SqlServer.Management.IntegrationServices") | Out-Null;

# Store the IntegrationServices Assembly namespace to avoid typing it every time
$ISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"

Write-Host "Connecting to server ..."

# Create a connection to the server
$sqlConnectionString = "Data Source=" + $SSISDBServerEndpoint + ";User ID="+ $SSISDBServerAdminUserName +";Password="+ $SSISDBServerAdminPassword + ";Initial Catalog=SSISDB"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $ISNamespace".IntegrationServices" $sqlConnection

# Get the catalog
$catalog = $integrationServices.Catalogs['SSISDB']

write-host "Enumerating all folders..."

$folders = ls -Path $ProjectFilePath -Directory

if ($folders.Count -gt 0)
{
    foreach ($filefolder in $folders)
    {
        Write-Host "Creating Folder " $filefolder.Name " ..."

        # Create a new folder
        $folder = New-Object $ISNamespace".CatalogFolder" ($catalog, $filefolder.Name, "Folder description")
        $folder.Create()

        $projects = ls -Path $filefolder.FullName -File -Filter *.ispac
        if ($projects.Count -gt 0)
        {
            foreach($projectfile in $projects)
            {
                $projectfilename = $projectfile.Name.Replace(".ispac", "")
                Write-Host "Deploying " $projectfilename " project ..."

                # Read the project file, and deploy it to the folder
                [byte[]] $projectFileContent = [System.IO.File]::ReadAllBytes($projectfile.FullName)
                $folder.DeployProject($projectfilename, $projectFileContent)
            }
        }
    }
}

Write-Host "All done." 
```

## <a name="run-a-package"></a>Eseguire un pacchetto

1. In Esplora oggetti di SQL Server Management Studio selezionare il pacchetto da eseguire.

2. Fare clic con il pulsante destro del mouse e selezionare **Esegui** per aprire la finestra di dialogo **Esegui pacchetto**.

3.  Nella finestra di dialogo **Esegui pacchetto** configurare l'esecuzione del pacchetto usando le impostazioni delle schede **Parametri**, **Gestioni connessioni** e **Avanzate**.

4.  Selezionare **OK** per eseguire il pacchetto.

## <a name="monitor-the-running-package-in-ssms"></a>Monitorare il pacchetto in esecuzione in SSMS

Per visualizzare lo stato delle operazioni di Integration Services attualmente in esecuzione nel server Integration Services, ad esempio distribuzione, convalida ed esecuzione dei pacchetti, usare la finestra di dialogo **Operazioni attive** di SSMS. Per aprire la finestra di dialogo **Operazioni attive**, fare clic con il pulsante destro del mouse su **SSISDB**, quindi selezionare **Operazioni attive**.

È anche possibile selezionare un pacchetto in Esplora oggetti, fare clic con il pulsante destro del mouse e selezionare **Report**, quindi **Report standard** e infine **Tutte le esecuzioni**.

Per altre informazioni su come monitorare i pacchetti in esecuzione in SQL Server Management Studio, vedere [Esecuzione di pacchetti e altre operazioni di monitoraggio](https://docs.microsoft.com/sql/integration-services/performance/monitor-running-packages-and-other-operations).

## <a name="monitor-the-azure-ssis-integration-runtime"></a>Monitorare il runtime di integrazione SSIS di Azure

Per ottenere informazioni sullo stato del runtime di integrazione SSIS di Azure in cui si eseguono i pacchetti, usare i seguenti comandi di PowerShell: per ognuno dei comandi, specificare i nomi della data factory, del runtime di integrazione di Azure SSIS e del gruppo di risorse.

### <a name="get-metadata-about-the-azure-ssis-integration-runtime"></a>Monitorare il runtime di integrazione SSIS di Azure

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

### <a name="get-the-status-of-the-azure-ssis-integration-runtime"></a>Ottenere lo stato del runtime di integrazione SSIS di Azure

```powershell
Get-AzureRmDataFactoryV2IntegrationRuntime -Status -DataFactoryName $DataFactoryName -Name $AzureSsisIRName -ResourceGroupName $ResourceGroupName
```

## <a name="next-steps"></a>Passaggi successivi
- Informazioni su come pianificare l'esecuzione dei pacchetti. Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md)
