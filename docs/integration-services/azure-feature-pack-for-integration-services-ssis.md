---
title: Feature Pack di Integration Services (SSIS) per Azure | Microsoft Docs
ms.custom: ''
ms.date: 07/09/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.SSIS.AZURE.F1
- SQL14.SSIS.AZURE.F1
ms.assetid: 31de555f-ae62-4f2f-a6a6-77fea1fa8189
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cb19d30afa0f1f1a8f5c9a7db6aaa060d7c92f5a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47686239"
---
# <a name="azure-feature-pack-for-integration-services-ssis"></a>Feature Pack di Integration Services (SSIS) per Azure
Il Feature Pack di SQL Server Integration Services (SSIS) per Azure è un'estensione che fornisce i componenti elencati in questa pagina per consentire a SSIS di connettersi ai servizi Azure, trasferire i dati tra Azure e le origini dati locali ed elaborare i dati archiviati in Azure.

[![Scaricare il Feature Pack di SSIS per Azure](../analysis-services/media/download.png)](https://www.microsoft.com/download/details.aspx?id=54798) **Scarica**

- Per SQL Server 2017 - [Microsoft SQL Server 2017 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=54798)
- Per SQL Server 2016 - [Microsoft SQL Server 2016 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=49492)
- Per SQL Server 2014 - [Microsoft SQL Server 2014 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=47366)
- Per SQL Server 2012 - [Microsoft SQL Server 2012 Integration Services Feature Pack per Azure](https://www.microsoft.com/download/details.aspx?id=47367)

Le pagine di download includono anche informazioni sui prerequisiti. Assicurarsi di installare SQL Server prima di installare il Feature Pack di Azure in un server. In caso contrario i componenti del Feature Pack potrebbero non essere disponibili quando si distribuiscono pacchetti al database del catalogo SSIS (SSISDB) nel server.

## <a name="components-in-the-feature-pack"></a>Componenti del Feature Pack
-   Gestioni connessioni

    -   [Gestione connessioni di Azure Data Lake Analytics](connection-manager/azure-data-lake-analytics-connection-manager.md)

    -   [Gestione connessioni di Azure Data Lake Store](../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)
    
    -   [Gestione connessione Azure HDInsight](../integration-services/connection-manager/azure-hdinsight-connection-manager.md)

    -   [Gestione connessione Azure Resource Manager](../integration-services/connection-manager/azure-resource-manager-connection-manager.md)
    
    -   [Gestione connessione dell'archiviazione di Azure](../integration-services/connection-manager/azure-storage-connection-manager.md)

    -   [Gestione connessione della sottoscrizione di Azure](../integration-services/connection-manager/azure-subscription-connection-manager.md)
    
-   Attività

    -   [Attività di download BLOB di Azure](../integration-services/control-flow/azure-blob-download-task.md)

    -   [Attività di caricamento BLOB di Azure](../integration-services/control-flow/azure-blob-upload-task.md)

    -   [Attività Azure Data Lake Analytics](control-flow/azure-data-lake-analytics-task.md)

    -   [Attività File system di Azure Data Lake Store](../integration-services/control-flow/azure-data-lake-store-file-system-task.md)

    -   [Attività di creazione cluster di Azure HDInsight](../integration-services/control-flow/azure-hdinsight-create-cluster-task.md)

    -   [Attività di eliminazione cluster di Azure HDInsight](../integration-services/control-flow/azure-hdinsight-delete-cluster-task.md)
    
    -   [Attività Hive di Azure HDInsight](../integration-services/control-flow/azure-hdinsight-hive-task.md)

    -   [Attività Pig di Azure HDInsight](../integration-services/control-flow/azure-hdinsight-pig-task.md)

    -   [Attività di caricamento di Azure SQL DW](../integration-services/control-flow/azure-sql-dw-upload-task.md)

-   Componenti del flusso di dati

    -   [Origine BLOB di Azure](../integration-services/data-flow/azure-blob-source.md)

    -   [Destinazione BLOB di Azure](../integration-services/data-flow/azure-blob-destination.md)
    
    -   [Origine di Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-source.md)
    
    -   [Destinazione di Azure Data Lake Store](../integration-services/data-flow/azure-data-lake-store-destination.md)

-   Enumeratore file di Azure Data Lake Store e BLOB di Azure. Vedere [Contenitore Ciclo Foreach](http://msdn.microsoft.com/library/95a19dde-61ca-4d9b-aa3d-131fa4264296).

## <a name="scenario-processing-big-data"></a>Scenario: Elaborazione di Big data
 Usare il connettore di Azure per completare l'elaborazione di Big Data:

1.  Usare l'attività di caricamento BLOB di Azure per caricare i dati di input nell'archivio BLOB di Azure.

2.  Usare l'attività di creazione cluster di Azure HDInsight per creare un cluster di Azure HDInsight. Questo passaggio è facoltativo se si vuole usare un cluster personale.

3.  Usare l'attività Hive o Pig di Azure HDInsight per richiamare un processo Pig o Hive nel cluster di Azure HDInsight.

4.  Usare l'attività di eliminazione cluster di Azure HDInsight per eliminare il cluster di HDInsight dopo l'uso se è stato creato un cluster di HDInsight su richiesta nel passaggio 2.

5.  Usare l'attività di download BLOB di Azure HDInsight per scaricare i dati di output Pig/Hive dall'archivio BLOB di Azure.

![SSIS-AzureConnector-BigDataScenario](../integration-services/media/ssis-azureconnector-bigdatascenario.png)
 
## <a name="scenario-managing-data-in-the-cloud"></a>Scenario: Gestione di dati nel cloud
 Usare la destinazione BLOB di Azure in un pacchetto SSIS per scrivere i dati di output in un archivio BLOB di Azure oppure usare l'origine BLOB di Azure per leggere i dati da un archivio BLOB di Azure.

![SSIS-AzureConnector-CloudArchive-1](../integration-services/media/ssis-azureconnector-cloudarchive-1.png)
 
 ![SSIS-AzureConnector-CloudArchive-2](../integration-services/media/ssis-azureconnector-cloudarchive-2.png)

 Usare il contenitore Ciclo Foreach con l'enumeratore BLOB di Azure per elaborare i dati in più file BLOB.

![SSIS-AzureConnector-CloudArchive-3](../integration-services/media/ssis-azureconnector-cloudarchive-3.png)
  
