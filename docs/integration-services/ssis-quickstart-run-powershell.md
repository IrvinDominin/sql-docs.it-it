---
title: Eseguire un pacchetto SSIS con PowerShell | Microsoft Docs
ms.date: 09/25/2017
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: quick-start
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e5d364ce66d866980bc015a864e26b0861268ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="run-an-ssis-package-with-powershell"></a>Eseguire un pacchetto SSIS con PowerShell
Questa esercitazione introduttiva illustra come usare uno script di PowerShell per connettersi a un server di database ed eseguire un pacchetto SSIS.

## <a name="powershell-script"></a>Script di PowerShell
Specificare i valori appropriati per le variabili nella parte superiore dello script seguente e quindi eseguire lo script per eseguire il pacchetto SSIS.

> [!NOTE]
> L'esempio seguente usa l'autenticazione di Windows. Per usare l'autenticazione di SQL Server, sostituire l'argomento `Integrated Security=SSPI;` con `User ID=<user name>;Password=<password>;`.

```powershell
# Variables
$SSISNamespace = "Microsoft.SqlServer.Management.IntegrationServices"
$TargetServerName = "localhost"
$TargetFolderName = "Project1Folder"
$ProjectName = "Integration Services Project1"
$PackageName = "Package.dtsx"

# Load the IntegrationServices assembly
$loadStatus = [System.Reflection.Assembly]::Load("Microsoft.SQLServer.Management.IntegrationServices, "+
    "Version=14.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91, processorArchitecture=MSIL")

# Create a connection to the server
$sqlConnectionString = `
    "Data Source=" + $TargetServerName + ";Initial Catalog=master;Integrated Security=SSPI;"
$sqlConnection = New-Object System.Data.SqlClient.SqlConnection $sqlConnectionString

# Create the Integration Services object
$integrationServices = New-Object $SSISNamespace".IntegrationServices" $sqlConnection

# Get the Integration Services catalog
$catalog = $integrationServices.Catalogs["SSISDB"]

# Get the folder
$folder = $catalog.Folders[$TargetFolderName]

# Get the project
$project = $folder.Projects[$ProjectName]

# Get the package
$package = $project.Packages[$PackageName]

Write-Host "Running " $PackageName "..."

$result = $package.Execute("false", $null)

Write-Host "Done."
```

## <a name="next-steps"></a>Passaggi successivi
- Prendere in considerazione altri modi per eseguire un pacchetto.
    - [Eseguire un pacchetto SSIS con SSMS](./ssis-quickstart-run-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (SSMS)](./ssis-quickstart-run-tsql-ssms.md)
    - [Eseguire un pacchetto SSIS con Transact-SQL (Visual Studio Code)](ssis-quickstart-run-tsql-vscode.md)
    - [Eseguire un pacchetto SSIS dal prompt dei comandi](./ssis-quickstart-run-cmdline.md)
    - [Eseguire un pacchetto SSIS con C#](./ssis-quickstart-run-dotnet.md) 
