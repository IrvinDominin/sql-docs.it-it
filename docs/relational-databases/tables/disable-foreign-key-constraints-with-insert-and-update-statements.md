---
title: "Disabilitazione di vincoli di chiave esterna con le istruzioni INSERT e UPDATE | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "vincoli [SQL Server], chiavi esterne"
  - "chiavi esterne [SQL Server], disabilitazione dei vincoli"
  - "disabilitazione di vincoli"
  - "istruzione UPDATE [SQL Server], vincoli della chiave esterna"
  - "istruzione INSERT [SQL Server], vincoli della chiave esterna"
ms.assetid: 029168d7-085e-4b13-9b86-5644b67c6e24
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Disabilitazione di vincoli di chiave esterna con le istruzioni INSERT e UPDATE
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  È possibile disabilitare un vincolo di chiave esterna durante le transazioni INSERT e UPDATE in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)]. Usare questa opzione se si è sicuri che i nuovi dati violeranno il vincolo esistente o se il vincolo si applica solo ai dati già presenti nel database.  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per disabilitare un vincolo di chiave esterna per le istruzioni INSERT e UPDATE tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
 Dopo aver disabilitato questi vincoli, gli inserimenti o gli aggiornamenti successivi della colonna non saranno convalidati in base alle condizioni del vincolo.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per disabilitare un vincolo di chiave esterna per le istruzioni INSERT e UPDATE  
  
1.  In **Esplora oggetti**espandere la tabella contenente il vincolo, quindi espandere la cartella **Chiavi** .  
  
2.  Fare clic con il pulsante destro del mouse sul vincolo e selezionare **Modifica**.  
  
3.  Nella griglia in **Progettazione tabelle** fare clic su **Attiva vincolo della chiave esterna**, quindi scegliere **No** nel menu a discesa.  
  
4.  Scegliere **Chiudi**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
  
#### Per disabilitare un vincolo di chiave esterna per le istruzioni INSERT e UPDATE  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare gli esempi seguenti nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Purchasing.PurchaseOrderHeader  
    NOCHECK CONSTRAINT FK_PurchaseOrderHeader_Employee_EmployeeID;  
    GO  
    ```  
  
 Per altre informazioni, vedere [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>  