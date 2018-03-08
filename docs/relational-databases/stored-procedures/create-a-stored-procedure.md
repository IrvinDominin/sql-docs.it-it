---
title: Creare una stored procedure | Microsoft Docs
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-stored-Procs
ms.tgt_pltfrm: 
ms.topic: get-started-article
helpviewer_keywords:
- new stored procedures
- stored procedures [SQL Server], creating
- creating stored procedures
ms.assetid: 76e8a6ba-1381-4620-b356-4311e1331ca7
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 36ca0485ec35bcfd14ee1da0d01ac66c0a40c886
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="create-a-stored-procedure"></a>Creazione di una stored procedure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 > Per il contenuto relativo alle versioni precedenti di SQL Server, vedere [Creazione di una stored procedure](https://msdn.microsoft.com/en-US/library/ms345415(SQL.120).aspx).

  In questo argomento viene descritta la procedura per la creazione di una stored procedure [!INCLUDE[tsql](../../includes/tsql-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e l'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE PROCEDURE.  
  
##  <a name="Top"></a>   
-   **Prima di iniziare:**  [Autorizzazioni](#Permissions)  
  
-   **Per creare una stored procedure:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione CREATE PROCEDURE per il database e dell'autorizzazione ALTER per lo schema in cui la stored procedure viene creata.  
  
##  <a name="Procedures"></a> Procedura: creazione di una stored procedure  
 È possibile usare uno dei seguenti elementi:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per creare una stored procedure in Esplora oggetti**  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere **Database**, il database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] e quindi **Programmabilità**.  
  
3.  Fare clic con il pulsante destro del mouse su **Stored procedure**e quindi scegliere **Nuova stored procedure**.  
  
4.  Scegliere **Imposta valori per parametri modello** dal menu **Query**.  
  
5.  Nella finestra di dialogo **Imposta valori per parametri modello** immettere i seguenti valori per i parametri indicati.  
  
    |Parametro|valore|  
    |---------------|-----------|  
    |Autore|*Nome dell'utente*|  
    |Data di creazione|*Data corrente*|  
    |Description|Restituisce i dati dei dipendenti.|  
    |Procedure_name|HumanResources.uspGetEmployeesTest|  
    |@Param1|@LastName|  
    |@Datatype_For_Param1|**nvarchar**(50)|  
    |Default_Value_For_Param1|NULL|  
    |@Param2|@FirstName|  
    |@Datatype_For_Param2|**nvarchar**(50)|  
    |Default_Value_For_Param2|NULL|  
  
6.  Fare clic su **OK**.  
  
7.  Nell' **editor di query**sostituire l'istruzione SELECT con l'istruzione seguente:  
  
    ```sql  
    SELECT FirstName, LastName, Department  
    FROM HumanResources.vEmployeeDepartmentHistory  
    WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    ```  
  
8.  Per controllare la sintassi, scegliere **Analizza** dal menu **Query**. Se viene restituito un messaggio di errore, confrontare le istruzioni con le informazioni precedenti e apportare le modifiche necessarie.  
  
9. Per creare la stored procedure, nel menu **Query** fare clic su **Esegui**. La stored procedure viene creata come un oggetto nel database.  
  
10. Per visualizzare la stored procedure nell'elenco di Esplora oggetti, fare clic con il pulsante destro del mouse su **Stored procedure** e scegliere **Aggiorna**.  
  
11. Per eseguire la stored procedure in Esplora oggetti, fare clic con il pulsante destro del mouse sul nome della stored procedure **HumanResources.uspGetEmployeesTest** e scegliere **Esegui stored procedure**.  
  
12. Nella finestra **Esegui procedura** immettere Margheim come valore per il parametro @LastName e Diane come valore per il parametro @FirstName.  
  
> [!WARNING]  
>  Convalidare sempre input di tutti gli utenti. Non concatenare l'input dell'utente prima di averlo convalidato. Non eseguire mai un comando creato dall'input dell'utente non convalidato.  
  
###  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per creare una stored procedure nell'editor di query**  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Nel menu **File** , fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio viene creata la stessa stored procedure precedente utilizzando un nome diverso.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE PROCEDURE HumanResources.uspGetEmployeesTest2   
        @LastName nvarchar(50),   
        @FirstName nvarchar(50)   
    AS   
  
        SET NOCOUNT ON;  
        SELECT FirstName, LastName, Department  
        FROM HumanResources.vEmployeeDepartmentHistory  
        WHERE FirstName = @FirstName AND LastName = @LastName  
        AND EndDate IS NULL;  
    GO  
  
    ```  
  
4.  Per eseguire la stored procedure, copiare l'esempio seguente e incollarlo in una nuova finestra Query, quindi fare clic su **Esegui**. Notare che vengono mostrati metodi diversi per specificare i valori del parametro.  
  
    ```  
    EXECUTE HumanResources.uspGetEmployeesTest2 N'Ackerman', N'Pilar';  
    -- Or  
    EXEC HumanResources.uspGetEmployeesTest2 @LastName = N'Ackerman', @FirstName = N'Pilar';  
    GO  
    -- Or  
    EXECUTE HumanResources.uspGetEmployeesTest2 @FirstName = N'Pilar', @LastName = N'Ackerman';  
    GO  
  
    ```  
  
##  <a name="PowerShellProcedure"></a>   
## <a name="see-also"></a>Vedere anche  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)  
  
  
