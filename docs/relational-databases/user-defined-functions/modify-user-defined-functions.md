---
title: Modificare funzioni definite dall'utente | Microsoft Docs
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: udf
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-udf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 891c37b3-cb72-411f-9937-ee87e6d95f34
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c7b7c08f7f2a853402fa2f9b8e870a317cb44554
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="modify-user-defined-functions"></a>Modificare funzioni definite dall'utente
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
È possibile modificare le funzioni definite dall'utente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. La modifica delle funzioni definite dall'utente come descritto di seguito non comporta la modifica delle autorizzazioni delle funzioni, né influisce su funzioni dipendenti, stored procedure o trigger.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Security](#Security)  
  
-   **Per modificare una funzione definita dall'utente tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Non è possibile utilizzare ALTER FUNCTION per eseguire le azioni seguenti:  
  
-   Modificare una funzione a valori scalari in una funzione con valori di tabella o viceversa.  
  
-   Modificare una funzione inline in una funzione a più istruzioni o viceversa.  
  
-   Modificare una funzione Transact-SQL in una funzione CLR o viceversa.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 È necessario disporre dell'autorizzazione ALTER per la funzione o lo schema. Se per la funzione viene specificato un tipo definito dall'utente, è necessario disporre dell'autorizzazione EXECUTE per tale tipo.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-a-user-defined-function"></a>Per modificare una funzione definita dall'utente  
  
1.  Fare clic sul segno più accanto al database che contiene la funzione che si desidera modificare.  
  
2.  Fare clic sul segno più accanto alla cartella **Programmabilità** .  
  
3.  Fare clic sul segno più accanto alla cartella che contiene la funzione che si desidera modificare:  
  
    -   Table-valued Function  
  
    -   Funzione a valori scalari  
  
    -   Funzione di aggregazione  
  
4.  Fare clic con il pulsante destro del mouse sulla funzione da modificare, quindi scegliere **Modifica**.  
  
5.  Nella Finestra Query apportare le modifiche necessarie all'istruzione ALTER FUNCTION.  
  
6.  Nel menu **File** fare clic su **Salva***nome_funzione*.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-modify-a-user-defined-function"></a>Per modificare una funzione definita dall'utente  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**.  
  
    ```  
    -- Scalar-Valued Function  
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetAccountingEndDate]()  
    RETURNS [datetime]   
    AS   
    BEGIN  
        RETURN DATEADD(millisecond, -2, CONVERT(datetime, '20040701', 112));  
    END;  
    ```  
  
    ```  
    -- Table-Valued Function   
    USE [AdventureWorks2012]  
    GO  
    ALTER FUNCTION [dbo].[ufnGetContactInformation](@PersonID int)  
    RETURNS @retContactInformation TABLE   
    (  
        -- Columns returned by the function  
        [PersonID] int NOT NULL,   
        [FirstName] [nvarchar](50) NULL,   
        [LastName] [nvarchar](50) NULL,   
        [JobTitle] [nvarchar](50) NULL,  
        [BusinessEntityType] [nvarchar](50) NULL  
    )  
    AS   
    -- Returns the first name, last name, job title and business entity type for the specified contact.  
    -- Since a contact can serve multiple roles, more than one row may be returned.  
    BEGIN  
    IF @PersonID IS NOT NULL   
    BEGIN  
         IF EXISTS(SELECT * FROM [HumanResources].[Employee] e   
         WHERE e.[BusinessEntityID] = @PersonID)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, e.[JobTitle], 'Employee'  
              FROM [HumanResources].[Employee] AS e  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = e.[BusinessEntityID]  
              WHERE e.[BusinessEntityID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Purchasing].[Vendor] AS v  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Vendor Contact'   
              FROM [Purchasing].[Vendor] AS v  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = v.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Sales].[Store] AS s  
         INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
         WHERE bec.[PersonID] = @PersonID)  
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, ct.[Name], 'Store Contact'   
              FROM [Sales].[Store] AS s  
              INNER JOIN [Person].[BusinessEntityContact] bec ON bec.[BusinessEntityID] = s.[BusinessEntityID]  
              INNER JOIN [Person].ContactType ct ON ct.[ContactTypeID] = bec.[ContactTypeID]  
              INNER JOIN [Person].[Person] p ON p.[BusinessEntityID] = bec.[PersonID]  
              WHERE bec.[PersonID] = @PersonID;  
  
         IF EXISTS(SELECT * FROM [Person].[Person] AS p  
         INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
         WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL)   
         INSERT INTO @retContactInformation  
              SELECT @PersonID, p.FirstName, p.LastName, NULL, 'Consumer'   
              FROM [Person].[Person] AS p  
              INNER JOIN [Sales].[Customer] AS c ON c.[PersonID] = p.[BusinessEntityID]  
              WHERE p.[BusinessEntityID] = @PersonID AND c.[StoreID] IS NULL;   
         END  
    RETURN;  
    END;  
    ```  
  
 Per altre informazioni, vedere [ALTER FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-function-transact-sql.md).  
  
  
