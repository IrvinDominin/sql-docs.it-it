---
title: Modificare statistiche | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: statistics
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-statistics
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
caps.latest.revision: "9"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 00114f6c9d691ed00b71c9d640fa57d7676c3426
ms.sourcegitcommit: 6b4aae3706247ce9b311682774b13ac067f60a79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="modify-statistics"></a>Modificare statistiche
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] È possibile modificare statistiche esistenti in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'argomento**  
  
-   **Prima di iniziare:**  
  
     [Security](#Security)  
  
-   **Modificare statistiche tramite:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Permissions  
 Sono necessarie le autorizzazioni seguenti:  
  
-   L'utente deve disporre dell'autorizzazione ALTER per la tabella o la vista.  
  
-   L'utente deve essere il proprietario della tabella o della vista indicizzata o un membro di uno dei seguenti ruoli: ruolo predefinito del server **sysadmin** , ruolo predefinito del database **db_owner** o ruolo predefinito del database **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-statistics"></a>Per modificare le statistiche  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il database in cui si desidera modificare una statistica.  
  
2.  Fare clic sul segno più per espandere la cartella **Tabelle** .  
  
3.  Fare clic sul segno più per espandere la tabella in cui si desidera modificare una statistica.  
  
4.  Fare clic sul segno più per espandere la cartella **Statistiche** .  
  
5.  Fare clic con il pulsante destro del mouse sull'oggetto statistiche che si vuole modificare e scegliere **Proprietà**.  
  
6.  Nella pagina **nome_statistichee** *Proprietà statistiche -*  **nome_statistiche** fare clic su **Aggiungi**, **Rimuovi**, **Sposta su**o **Sposta giù**o any combination, to alter the properties of the statistics. Si noti che la posizione di una colonna nella griglia **Colonne statistiche** può avere un impatto significativo sull'utilità delle statistiche.  
  
7.  Fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
 **Per modificare le statistiche**  
  
 Non è possibile eseguire questa attività utilizzando istruzioni Transact-SQL. Per modificare statistiche tramite Transact-SQL, è innanzitutto necessario eliminare la statistica esistente e quindi ricrearla con i nuovi attributi.  
  
 Per altre informazioni, vedere [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md) e [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  
