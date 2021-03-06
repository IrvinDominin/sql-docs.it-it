---
title: 'Procedura: Creare nuovi oggetti di database tramite query | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: ac983ac7-f9c4-495d-8a99-e1ba370fb271
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bcf7fe3ad0b07b9f8a228318b5eea85b3d8526a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780349"
---
# <a name="how-to-create-new-database-objects-using-queries"></a>Procedura: Creazione di nuovi oggetti di database tramite query
Se si preferisce usare script per creare o modificare viste, stored procedure, funzioni, trigger o tipi definiti dall'utente, è possibile usare l'Editor Transact\-SQL. L'Editor Transact\-SQL fornisce IntelliSense e altro supporto del linguaggio. Per altre informazioni, vedere [Usare l'Editor Transact-SQL per modificare ed eseguire script](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md).  
  
L'Editor Transact\-SQL viene richiamato quando si usa il menu contestuale **Visualizza codice** per aprire un'entità del database in un database connesso o in un progetto. Viene anche aperto automaticamente quando si usa il menu contestuale **Nuova query** da Esplora oggetti di SQL Server o si aggiunge un nuovo oggetto script a un progetto di database. Se non si è connessi a un database ma si vuole eseguire una query sul database stesso, è possibile usare la finestra di dialogo **Nuova connessione query** selezionando il menu **Editor Transact-SQL** dal menu **SQL** per connettersi a un database e avviare l'Editor Transact\-SQL.  
  
> [!WARNING]  
> Nelle procedure seguenti vengono usate entità create nelle procedure precedenti nella sezione [Sviluppo del database connesso](../ssdt/connected-database-development.md).  
  
### <a name="to-create-a-new-table-using-a-transact-sql-query"></a>Per creare una tabella usando una query Transact\-SQL  
  
1.  Fare clic con il pulsante destro del mouse sul nodo del database **Trade** e selezionare **Nuova query**.  
  
2.  Nel riquadro di script incollare questo codice:  
  
    ```  
  
    CREATE TABLE [dbo].[Fruits] (  
        [Id]         INT NOT NULL,  
        [Perishable] BIT DEFAULT ((1)) NULL,  
        PRIMARY KEY CLUSTERED ([Id] ASC),  
        FOREIGN KEY ([Id]) REFERENCES [dbo].[Products] ([Id])   
    );  
    ```  
  
3.  Fare clic sul pulsante **Esegui query** nella barra degli strumenti dell'Editor Transact\-SQL per eseguire questa query.  
  
4.  Fare clic con il pulsante destro del mouse sul database **Trade** in **Esplora oggetti di SQL Server** e selezionare **Aggiorna**. Si noti che la nuova tabella **Fruits** è stata aggiunta al database.  
  
### <a name="to-create-a-new-function"></a>Per creare una nuova funzione  
  
1.  Sostituire il codice nell'Editor Transact\-SQL corrente con quanto riportato di seguito:  
  
    ```  
  
    CREATE FUNCTION [dbo].GetProductsBySupplier  
    (  
    @SupplierId int  
    )  
    RETURNS @returntable TABLE   
    (  
    [Id] int NOT NULL,   
    [Name] NVARCHAR (128) NOT NULL,  
    [Shelflife] INT NOT NULL,  
    [SupplierId] INT NOT NULL,  
    [CustomerId] INT NOT NULL  
    )  
    AS  
    BEGIN  
    INSERT @returntable  
    SELECT *  from Products p  
    where p.SupplierId = @SupplierId  
    RETURN   
    END  
    ```  
  
    Tramite questa funzione verranno restituite tutte le righe nella tabella `Products` il cui `SupplierId` corrisponde al parametro specificato. Fare clic sul pulsante **Esegui query** nella barra degli strumenti dell'Editor Transact\-SQL per eseguire questa query.  
  
2.  Nel nodo **Trade** in Esplora oggetti di SQL Server espandere i nodi **Programmazione** e **Funzioni**. È possibile individuare la nuova funzione appena creata in **Funzioni con valori di tabella**.  
  
### <a name="to-create-a-new-view"></a>Per creare una nuova vista  
  
1.  Sostituire il codice nell'Editor Transact\-SQL corrente con quanto riportato di seguito. Fare clic sul pulsante **Esegui query** sopra l'editor per eseguire questa query.  
  
    ```  
    CREATE VIEW [dbo].PerishableFruits   
    AS SELECT p.Id, p.Name FROM dbo.Products p  
    join dbo.Fruits f on f.Id = p.Id  
    where f.Perishable = 1  
    ```  
  
2.  Nel nodo **Trade** in Esplora oggetti di SQL Server espandere il nodo **Vista** per individuare la nuova vista appena creata.  
  
## <a name="see-also"></a>Vedere anche  
[Gestire tabelle e relazioni e correggere errori](../ssdt/manage-tables-relationships-and-fix-errors.md)  
[Usare l'Editor Transact-SQL per modificare ed eseguire script](../ssdt/use-transact-sql-editor-to-edit-and-execute-scripts.md)  
  
