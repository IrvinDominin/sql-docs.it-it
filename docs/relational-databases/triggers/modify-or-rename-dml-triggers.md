---
title: "Modifica o ridenominazione di trigger DML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ridenominazione di trigger"
  - "modifica di trigger"
  - "trigger DML, modifica"
ms.assetid: c7317eec-c0e9-479e-a4a7-83b6b6c58d59
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Modifica o ridenominazione di trigger DML
  In questo argomento viene illustrato come modificare o rinominare un trigger DML in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Indicazioni](#Recommendations)  
  
     [Sicurezza](#Security)  
  
-   **Per modificare o rinominare un trigger DML utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   Quando si rinomina un trigger, il trigger deve trovarsi nel database corrente e il nuovo nome deve seguire le regole per gli [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
###  <a name="Recommendations"></a> Indicazioni  
  
-   È consigliabile non usare la stored procedure [sp_rename](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md) per rinominare un trigger. La modifica di una parte del nome di un oggetto potrebbe compromettere il funzionamento di script e stored procedure. La ridenominazione di un trigger non comporta la modifica del nome dell'oggetto corrispondente nella colonna di definizione della vista del catalogo [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md). È consigliabile eliminare e ricreare il trigger.  
  
-   Se si modifica il nome di un oggetto a cui fa riferimento un trigger DML, è necessario modificare il trigger in modo che il testo corrisponda al nuovo nome. Pertanto, prima di rinominare un oggetto, visualizzare le dipendenze dell'oggetto per determinare se la modifica proposta interessa i trigger.  
  
-   È inoltre possibile rinominare i trigger DML per crittografarne la definizione.  
  
-   Per visualizzare le dipendenze di un trigger, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o la funzione e viste del catalogo seguenti:  
  
    -   [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)  
  
    -   [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)  
  
    -   [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per modificare un trigger DML è necessaria l'autorizzazione ALTER sulla tabella o vista in cui è definito il trigger.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per modificare un trigger DML  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , quindi espanderla.  
  
2.  Espandere il database desiderato, espandere **Tabelle**, quindi espandere la tabella che contiene il trigger da modificare.  
  
3.  Espandere **Trigger**, fare clic con il pulsante destro del mouse sul trigger da modificare, quindi scegliere **Modifica**.  
  
4.  Modificare il trigger e fare clic su **Esegui**.  
  
#### Per rinominare un trigger DML  
  
1.  [Eliminare il trigger](../../relational-databases/triggers/delete-or-disable-dml-triggers.md) che si desidera rinominare.  
  
2.  [Ricreare il trigger](../../relational-databases/triggers/create-dml-triggers.md), specificando il nuovo nome.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per modificare un trigger utilizzando ALTER TRIGGER  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella query. Eseguire il primo esempio per creare un trigger DML per la stampa di un messaggio definito dall'utente nel client quando un utente tenta di aggiungere o modificare i dati delle modifiche nella tabella `SalesPersonQuotaHistory`. Eseguire l'istruzione [ALTER TRIGGER](../../t-sql/statements/alter-trigger-transact-sql.md) per modificare il trigger in modo che venga attivato solo con le attività `INSERT` . Questo trigger risulta molto utile, in quanto ricorda all'utente che aggiorna o inserisce righe nella tabella di inviare una notifica al reparto `Compensation` .  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
```tsql  
USE AdventureWorks2012;  
GO  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
#### Per rinominare un trigger utilizzando DROP TRIGGER e ALTER TRIGGER  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**. In questo esempio vengono utilizzate le istruzioni [DROP TRIGGER](../../t-sql/statements/drop-trigger-transact-sql.md) e [ALTER TRIGGER](../../t-sql/statements/alter-trigger-transact-sql.md) per rinominare il trigger `Sales.bonus_reminder` in `Sales.bonus_reminder_2`.  
  
```tsql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID(N'Sales.bonus_reminder', N'TR') IS NOT NULL  
    DROP TRIGGER Sales.bonus_reminder;  
GO  
CREATE TRIGGER Sales.bonus_reminder_2  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
  
```  
  
## Vedere anche  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [Ottieni informazioni sui trigger DML](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  