---
title: "Procedura: Creare un progetto di test per l'esecuzione di unit test del database di SQL Server | Microsoft Docs"
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 4b3e7ba8-b565-4689-af1a-34cc255b7c60
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f9e856bfbbcb8cba527d1f34f0f7bc99afadc023
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792879"
---
# <a name="how-to-create-a-test-project-for-sql-server-database-unit-testing"></a>Procedura: Creare un progetto di test per l'esecuzione di unit test del database di SQL Server
Prima di iniziare a scrivere unit test per valutare gli oggetti di database, è necessario creare innanzitutto un progetto di test. Il progetto contiene unit test di SQL Server, ma può includere altri tipi di test.  
  
È possibile inserire tutti gli unit test di SQL Server di un determinato progetto di database all'interno di un solo progetto di test. Può tuttavia essere opportuno creare progetti di test aggiuntivi, in base alle risposte fornite alle domande seguenti:  
  
|||  
|-|-|  
|**Domanda**|**Decisione**|  
|È necessario l'accesso di unit test di SQL Server differenti a connessioni di database diverse per l'esecuzione o la convalida dei test?|Se sì, sono necessari più progetti di test. Non è possibile specificare più di una connessione al database per l'esecuzione del test. Tuttavia, è possibile specificare una connessione al database differente per la convalida del test.|  
|Si desidera distribuire progetti di database diversi per unit test differenti?|Se sì, sono necessari più progetti di test. Un progetto di test può distribuire un solo progetto di database.|  
  
Per altre informazioni su ognuna di queste domande, vedere [Procedura: Configurare l'esecuzione di unit test di SQL Server](../ssdt/how-to-configure-sql-server-unit-test-execution.md). In alternativa alla creazione di più progetti di test, è anche possibile fornire la propria implementazione di [DatabaseTestService](https://msdn.microsoft.com/library/microsoft.data.schema.unittesting.databasetestservice.aspx) Microsoft.Data.Schema.UnitTesting.DatabaseTestService.  
  
Sono disponibili tre opzioni per l'aggiunta di un progetto di test a una soluzione contenente un progetto di database:  
  
-   Aggiungere un progetto di test alla soluzione. Nel progetto di test è incluso uno unit test standard, che è possibile eliminare. Nel progetto non è contenuta una classe di unit test di SQL Server, che è necessario aggiungere.  
  
-   Aggiungere un nuovo unit test di SQL Server dal menu **Test**. Quando si aggiunge lo unit test, in SQL Server Data Tools viene anche creato un progetto di test, se richiesto. Questo progetto contiene una classe di unit test di SQL Server. Le classi di test per unit test di SQL Server contengono uno o più unit test.  
  
-   Creare uno unit test da una stored procedure, una funzione o un trigger da un progetto aperto in Esplora oggetti di SQL Server. Quando si crea lo unit test, in SQL Server Data Tools viene anche creato un progetto di test, se richiesto. Questo progetto contiene una classe di unit test di SQL Server. Le classi di test di SQL Server contengono uno o più unit test.  
  
Ogni approccio viene descritto nelle procedure riportate di seguito.  
  
### <a name="to-add-a-test-project-to-an-existing-solution"></a>Per aggiungere un progetto di test a una soluzione esistente  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
    Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  In **Modelli installati** espandere il nodo **SQL Server** e quindi selezionare **Progetto di database di SQL Server**.  
  
3.  Nella casella **Nome** digitare un nome per il progetto.  
  
### <a name="to-create-a-test-project-with-a-sql-server-unit-test-class"></a>Per creare un progetto di test con una classe di test di SQL Server  
  
-   Seguire la procedura descritta in [Procedura: Creare uno unit test di SQL Server vuoto](../ssdt/how-to-create-an-empty-sql-server-unit-test.md) o in [Procedura: Creare unit test di SQL Server per funzioni, trigger e stored procedure](../ssdt/how-to-create-unit-tests-for-functions-triggers-stored-procedures.md).  
  
## <a name="see-also"></a>Vedere anche  
[Creazione e definizione di unit test di SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  
