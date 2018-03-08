---
title: Visualizzazione di informazioni sulle regole di confronto | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: collations
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collations [SQL Server], view
ms.assetid: 1338b4ea-7142-44bc-a3b9-44e54431405f
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4095965899da005d767bb124806fbb116379a1f6
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="view-collation-information"></a>Visualizzazione di informazioni sulle regole di confronto
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
##  <a name="Top"></a> È possibile visualizzare le regole di confronto di un server, di un database o di una colonna in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usando le opzioni di menu di Esplora oggetti oppure tramite [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
##  <a name="Procedures"></a> Visualizzazione di un'impostazione relativa alle regole di confronto  
 È possibile usare uno dei seguenti elementi:  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
 **Per visualizzare un'impostazione delle regole di confronto per un server (istanza di SQL Server) in Esplora oggetti**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Fare clic con il pulsante destro del mouse sull'istanza e selezionare **Proprietà**.  
  
 **Per visualizzare un'impostazione delle regole di confronto per un database in Esplora oggetti**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e quindi espanderla.  
  
2.  Espandere **Database**, fare clic con il pulsante destro del mouse sul database e selezionare **Proprietà**.  
  
 **Per visualizzare un'impostazione delle regole di confronto per una colonna in Esplora oggetti**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e quindi espanderla.  
  
2.  Espandere **Database**, il database desiderato, quindi **Tabelle**.  
  
3.  Espandere la tabella che contiene la colonna, quindi espandere **Colonne**.  
  
4.  Fare clic con il pulsante destro del mouse sulla colonna e selezionare **Proprietà**. Se la proprietà di regola di confronto è vuota, la colonna non è un tipo di dati character.  
  
###  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per visualizzare l'impostazione delle regole di confronto di un server**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e nella barra degli strumenti fare clic su **Nuova query**.  
  
2.  Nella finestra Query, immettere l'istruzione seguente che usano la funzione di sistema SERVERPROPERTY.  
  
    ```  
    SELECT CONVERT (varchar, SERVERPROPERTY('collation'));  
    ```  
  
3.  In alternativa, è possibile usare la stored procedure di sistema sp_helpsort.  
  
    ```  
    EXECUTE sp_helpsort;  
    ```  
  
 **Per visualizzare tutte le regole di confronto supportate da [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e nella barra degli strumenti fare clic su **Nuova query**.  
  
2.  Nella finestra Query, immettere l'istruzione seguente che usano la funzione di sistema SERVERPROPERTY.  
  
    ```  
    SELECT name, description FROM sys.fn_helpcollations();  
    ```  
  
 **Per visualizzare l'impostazione delle regole di confronto di un database**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e nella barra degli strumenti fare clic su **Nuova query**.  
  
2.  Nella finestra Query, immettere l'istruzione seguente che usano la vista del catalogo sys.databases.  
  
    ```  
    SELECT name, collation_name FROM sys.databases;  
    ```  
  
3.  In alternativa, è possibile usare la funzione di sistema DATABASEPROPERTYEX.  
  
    ```  
    SELECT CONVERT (varchar, DATABASEPROPERTYEX('database_name','collation'));  
    ```  
  
 **Per visualizzare l'impostazione delle regole di confronto di una colonna**  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] e nella barra degli strumenti fare clic su **Nuova query**.  
  
2.  Nella finestra Query, immettere l'istruzione seguente che usano la vista del catalogo sys.columns.  
  
    ```  
    SELECT name, collation_name FROM sys.columns WHERE name = N'<insert character data type column name>';  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [Precedenza delle regole di confronto &#40;Transact-SQL&#41;](../../t-sql/statements/collation-precedence-transact-sql.md)   
 [sp_helpsort &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsort-transact-sql.md)  
  
  
