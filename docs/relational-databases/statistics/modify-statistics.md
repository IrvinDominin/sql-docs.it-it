---
title: "Modificare statistiche | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-statistics"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "statistiche [SQL Server], modifica"
  - "modifica di statistiche"
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
caps.latest.revision: 9
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 9
---
# Modificare statistiche
  È possibile modificare statistiche esistenti in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Modificare statistiche tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Sono necessarie le autorizzazioni seguenti:  
  
-   L'utente deve disporre dell'autorizzazione ALTER per la tabella o la vista.  
  
-   L'utente deve essere il proprietario della tabella o della vista indicizzata o un membro di uno dei seguenti ruoli: ruolo predefinito del server **sysadmin**, ruolo predefinito del database **db_owner** o ruolo predefinito del database **db_ddladmin**.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### Per modificare le statistiche  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il database in cui si desidera modificare una statistica.  
  
2.  Fare clic sul segno più per espandere la cartella **Tabelle** .  
  
3.  Fare clic sul segno più per espandere la tabella in cui si desidera modificare una statistica.  
  
4.  Fare clic sul segno più per espandere la cartella **Statistiche** .  
  
5.  Fare clic con il pulsante destro del mouse sull'oggetto statistiche che si vuole modificare e scegliere **Proprietà**.  
  
6.  Nella pagina **Generale** della finestra di dialogo **Proprietà statistiche -** *nome_statistiche* fare clic su **Aggiungi**, **Rimuovi**, **Sposta su** o **Sposta giù** oppure su una combinazione qualsiasi di queste opzioni, per modificare le proprietà delle statistiche. Si noti che la posizione di una colonna nella griglia **Colonne statistiche** può avere un impatto significativo sull'utilità delle statistiche.  
  
7.  Scegliere **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilizzo di Transact-SQL  
 **Per modificare le statistiche**  
  
 Non è possibile eseguire questa attività utilizzando istruzioni Transact-SQL. Per modificare statistiche tramite Transact-SQL, è innanzitutto necessario eliminare la statistica esistente e quindi ricrearla con i nuovi attributi.  
  
 Per altre informazioni, vedere [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md) e [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  