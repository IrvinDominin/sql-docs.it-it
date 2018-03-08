---
title: Connettersi al database del catalogo SSISDB in Azure | Microsoft Docs
ms.date: 09/25/2017
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
ms.openlocfilehash: 98aed78b69a108ae5b0c8f914540b385403a60f9
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Connettersi al database del catalogo SSISDB in Azure

Ottenere le informazioni di connessione necessarie per connettersi al database del catalogo SSISDB ospitato in un server di database SQL di Azure. Per eseguire la connessione sono necessari gli elementi seguenti:
- nome completo del server
- nome del database
- informazioni di accesso 

> [!IMPORTANT]
> In questo momento, non è possibile creare il database del catalogo SSISDB in un database SQL di Azure se non si crea il runtime di integrazione SSIS di Azure in Azure Data Factory versione 2. È il runtime di integrazione SSIS di Azure che esegue i pacchetti SSIS in Azure. Per altre informazioni, vedere [Distribuire pacchetti SQL Server Integration Services in Azure](https://docs.microsoft.com/azure/data-factory/tutorial-create-azure-ssis-runtime-portal). 

## <a name="prerequisites"></a>Prerequisites
Prima di iniziare, verificare di avere la versione 17.2 o successiva di SQL Server Management Studio. Per scaricare la versione più recente di SSMS, vedere [Scaricare SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="get-the-connection-info-from-the-azure-portal"></a>Ottenere le informazioni di connessione dal portale di Azure
1. Accedere al [portale di Azure](https://portal.azure.com/).
2. Nel portale di Azure selezionare **Database SQL** dal menu a sinistra e quindi selezionare il database `SSISDB` nella pagina dei **database SQL**. 
3. Nella pagina **Panoramica** del database `SSISDB` controllare il nome completo del server come illustrato nella figura seguente. Passare il mouse sul nome del server per visualizzare l'opzione **Fare clic per copiare**.

    ![Informazioni di connessione server](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. Se non si ricordano i dati di accesso al server di database SQL, passare alla pagina del server di database SQL. Nella pagina è possibile visualizzare il nome dell'amministratore del server e, se necessario, reimpostare la password.

## <a name="connect-with-ssms"></a>Connettersi a SSMS
1. Aprire SQL Server Management Studio.

2. **Connettersi al server**. Immettere le informazioni seguenti nella finestra di dialogo **Connetti al server**:

   | Impostazione       | Valore suggerito | Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Tipo server** | Motore di database | Questo valore è obbligatorio. |
   | **Nome server** | Nome completo del server | Il nome deve essere nel formato **mysqldbserver.database.windows.net**. |
   | **Autenticazione** | autenticazione di SQL Server | In questa guida rapida viene usata l'autenticazione SQL. |
   | **Account di accesso** | Account amministratore del server | Si tratta dell'account specificato al momento della creazione del server. |
   | **Password** | Password per l'account amministratore del server | Si tratta della password specificata al momento della creazione del server. |

3. **Connettersi al database SSISDB**. Selezionare **Opzioni** per espandere la finestra di dialogo **Connetti al server**. Nella finestra di dialogo **Connetti al server** espansa selezionare la scheda **Proprietà connessione**. Nel campo **Connetti al database** selezionare o immettere `SSISDB`.

    > [!IMPORTANT]
    > Se non si seleziona `SSISDB` durante la connessione, può non essere possibile visualizzare il catalogo SSIS in Esplora oggetti.

4. Selezionare **Connetti**.

5. In Esplora oggetti espandere **Cataloghi di Integration Services** e quindi espandere **SSISDB** per visualizzare gli oggetti nel database del catalogo SSIS.

## <a name="next-steps"></a>Passaggi successivi
- Distribuire un pacchetto. Per altre informazioni, vedere [Distribuire un progetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Eseguire un pacchetto. Per altre informazioni, vedere [Eseguire un pacchetto SSIS con SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Pianificare un pacchetto. Per altre informazioni, vedere [Pianificare l'esecuzione del pacchetto SSIS in Azure](ssis-azure-schedule-packages.md)
