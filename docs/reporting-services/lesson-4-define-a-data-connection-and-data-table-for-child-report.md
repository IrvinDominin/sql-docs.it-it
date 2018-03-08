---
title: 'Lesson 4: Define a Data Connection and Data Table for Child Report (Lezione 4: Definire una connessione dati e una tabella dati per il report figlio) | Microsoft Docs'
ms.custom: 
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2016
ms.assetid: a6aa2c56-227c-43c5-a28e-c7104131ac5e
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5a9893a646617d3f3bca68c7c22de1a7a10d7455
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="lesson-4-define-a-data-connection-and-data-table-for-child-report"></a>Lezione 4: Definire una connessione dati e una tabella di dati per il report figlio
Dopo aver progettato il report padre, il passaggio successivo consiste nel creare una connessione dati e una tabella di dati per il report figlio. In questa esercitazione la connessione dati è al database AdventureWorks2014.  
  
### <a name="to-define-a-data-connection-and-datatable-by-adding-a-dataset-for-child-report"></a>Per definire una connessione dati e l'oggetto DataTable aggiungendo un oggetto DataSet (per il report figlio)  
  
1.  Selezionare **Aggiungi nuovo elemento** dal menu **Sito Web**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento** selezionare **DataSet** e scegliere **Aggiungi**. Quando richiesto, è necessario aggiungere l'elemento alla cartella **App_Code** selezionando **Sì**.  
  
    Verrà aggiunto un nuovo file XSD **DataSet2.xsd** al progetto e verrà aperto Progettazione DataSet.  
  
3.  Dalla finestra della casella degli strumenti trascinare un controllo **TableAdapter** nell'area di progettazione. Verrà avviata la configurazione guidata **TableAdapter** .  
  
4.  Nella pagina **Seleziona connessione dati** è possibile selezionare la connessione creata nella lezione 2. Se è già selezionata, selezionate **Avanti** e andare al passaggio 8. In caso contrario, selezionare **Nuova connessione**.  
  
5.  Nella finestra di dialogo **Aggiungi connessione** effettuare i passaggi seguenti:  
  
    1.  Nella casella **Nome server** immettere il server in cui si trova il database **AdventureWorks2014** .  
  
        L'istanza predefinita di SQL Server Express è **(local)\sqlexpress**.  
  
    2.  Nella sezione **Accesso al server** selezionare l'opzione di accesso ai dati. **Usa autenticazione di Windows** è l'impostazione predefinita.  
  
    3.  Nell'elenco a discesa **Selezionare o immettere un nome di database** selezionare **AdventureWorks2014**.  
  
    4.  Selezionare **OK**e quindi selezionare **Avanti**.  
  
6.  Se è stato selezionato **Usa autenticazione di SQL Server** nel passaggio 5 (b), selezionare l'opzione per includere i dati sensibili nella stringa o per impostare le informazioni nel codice dell'applicazione.  
  
7.  Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** digitare il nome per la stringa di connessione o accettare l'impostazione predefinita **AdventureWorks2014ConnectionString**. Fare clic su **Avanti**.  
  
8.  Nella pagina **Seleziona un tipo di comando** selezionare **Usa istruzioni SQL**e quindi fare clic su **Avanti**.  
  
9. Nella pagina **Immettere un'istruzione SQL** immettere la seguente query Transact-SQL per recuperare i dati dal database **AdventureWorks2014** e quindi fare clic su **Avanti**.  
  
    ```  
    SELECT PurchaseOrderID, PurchaseOrderDetailID, OrderQty, ProductID, ReceivedQty, RejectedQty, StockedQty FROM Purchasing.PurchaseOrderDetail  
    ```  
  
    È anche possibile creare la query facendo clic su **Generatore di query**e, successivamente, verificare la query facendo clic su **Esegui query** . Se non vengono restituiti i dati previsti dalla query, è possibile che si stia utilizzando una versione precedente di AdventureWorks. Per altre informazioni su come ottenere il database di esempio **AdventureWorks2014**, vedere [Database di esempio AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases).  
  
10. Nella pagina **Scegliere i metodi per generare** deselezionare **Crea metodi per inviare aggiornamenti direttamente al database (GenerateDBDirectMethods)**, quindi fare clic su **Fine**.  
  
    > [!WARNING]  
    > Assicurarsi di deselezionare **Crea metodi per inviare aggiornamenti direttamente al database (GenerateDBDirectMethods)**  
  
    È stata completata la configurazione dell'oggetto [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) di ADO.NET come origine dati del report. Nella pagina Progettazione DataSet in Visual Studio si dovrebbe visualizzare l'oggetto **DataTable** aggiunto, con le colonne specificate nella query. In DataSet2 sono inclusi i dati della tabella PurhcaseOrderDetail, basati sulla query.  
  
11. Salvare il file.  
  
12. Per visualizzare un'anteprima dei dati, scegliere **Anteprima dati** dal menu **Dati** e quindi fare clic su **Anteprima**.  
  
## <a name="next-task"></a>Attività successiva  
È stata creata correttamente una connessione dati e una tabella di dati per il report figlio. Successivamente, verrà progettato il report figlio utilizzando la Creazione guidata report. Vedere [Lezione 5: Progettare il report figlio tramite la Creazione guidata report](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md).  
  

