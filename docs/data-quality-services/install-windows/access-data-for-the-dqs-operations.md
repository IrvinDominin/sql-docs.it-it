---
title: Accedere ai dati per le operazioni DQS | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: data-quality-services
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: data-quality-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88dfb9ea-6321-4eaf-b9e4-45d36ef048f6
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf4ccaec030d6db0db4b3e83b8051e4ca97b5b2f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2018
---
# <a name="access-data-for-the-dqs-operations"></a>Accedere ai dati per le operazioni DQS
  Per utilizzare i dati di origine per operazioni [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) ed esportare i dati elaborati, è possibile effettuare una delle operazioni seguenti:  
  
-   Copiare i dati di origine in una tabella o vista nel database DQS_STAGING_DATA, quindi usarli per le operazioni DQS. Inoltre è possibile esportare i dati elaborati in una nuova tabella nel database DQS_STAGING_DATA. A questo scopo, all'account utente di Windows deve essere concesso l'accesso in lettura/scrittura al database DQS_STAGING_DATA.  
  
-   Usare il database in uso come dati di origine per le operazioni DQS e come destinazione per l'esportazione dei dati elaborati. A tale scopo, assicurarsi che il database si trovi nella stessa istanza di SQL Server dei database del server Data Quality. In caso contrario, il database non sarà disponibile nel client Data Quality per le relative operazioni. All'account utente di Windows deve essere concesso anche l'accesso al database DQS_STAGING_DATA per l'esportazione dei risultati corrispondenti perché questa operazione è un processo in due fasi: i risultati corrispondenti vengono prima esportati nelle tabelle temporanee del database DQS_STAGING_DATA e successivamente vengono spostati nella tabella nel database di destinazione.  
  
## <a name="prerequisites"></a>Prerequisites  
  
-   È necessario aver completato l'installazione di [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] tramite l'esecuzione del file DQSInstaller.exe. Per altre informazioni, vedere [Eseguire DQSInstaller.exe per completare l'installazione del server DQS](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).  
  
-   L'account utente di Windows deve essere un membro del ruolo predefinito del server appropriato (ad esempio securityadmin, serveradmin o sysadmin) nell'istanza del motore di database per concedere/modificare l'accesso all'account di accesso SQL sui database.  
  
### <a name="to-grant-readwrite-access-to-a-user-on-the-dqsstagingdata-database"></a>Per concedere l'accesso in lettura/scrittura a un utente sul database DQS_STAGING_DATA  
  
1.  Avviare Microsoft SQL Server Management Studio.  
  
2.  In Microsoft SQL Server Management Studio espandere l'istanza di SQL Server, espandere **Sicurezza**, quindi **Account di accesso**.  
  
3.  Fare clic con il pulsante destro del mouse sull'account di accesso SQL, quindi scegliere **Proprietà**.  
  
4.  Nel riquadro sinistro della finestra di dialogo **Proprietà account di accesso** fare clic su **Mapping utenti** .  
  
5.  Nel riquadro di destra selezionare la casella di controllo sotto la colonna **Mappa** per il database **DQS_STAGING_DATA** , quindi selezionare i ruoli seguenti nel riquadro **Appartenenza a ruoli del database per: DQS_STAGING_DATA** :  
  
    -   **db_datareader**: consente di leggere i dati da tabelle e viste.  
  
    -   **db_datawriter**: consente di aggiungere, eliminare o modificare i dati nelle tabelle.  
  
    -   **db_ddladmin**: consente di creare, modificare o eliminare tabelle e viste.  
  
6.  Nella finestra di dialogo **Proprietà account di accesso** fare clic su **OK** per applicare le modifiche.  
  
## <a name="next-steps"></a>Next Steps  
 Provare a effettuare operazioni DQS tramite cui si accede al database come origine dati per l'operazione DQS, quindi esportare i dati elaborati nel database.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)  
  
  
