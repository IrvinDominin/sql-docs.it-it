---
title: Modificare un indice | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: indexes
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-indexes
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- indexes [SQL Server], modifying
- modifying indexes
- index changes [SQL Server]
ms.assetid: 97e3110d-fde7-4f5d-9309-dc1697960aeb
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 539cd81a09c10703b4826e37245a9f225f606554
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2018
---
# <a name="modify-an-index"></a>Modificare un indice
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  In questo argomento viene descritto come modificare un indice in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] usando [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
> [!IMPORTANT]  
>  Gli indici creati come risultato di un vincolo PRIMARY KEY o UNIQUE non possono essere modificati con questo metodo. È necessario invece modificare il vincolo.  
  
 **Contenuto dell'argomento**  
  
-   **Per modificare un indice usando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilizzo di SQL Server Management Studio  
  
#### <a name="to-modify-an-index"></a>Per modificare un indice  
  
1.  In Esplora oggetti connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , quindi espandere questa istanza.  
  
2.  Espandere **Database**, espandere il database a cui appartiene la tabella e quindi espandere **Tabelle**.  
  
3.  Espandere la tabella a cui appartiene l'indice e quindi espandere **Indici**.  
  
4.  Fare clic con il pulsante destro del mouse sull'indice da modificare l'indice e scegliere **Proprietà**.  
  
5.  Nella finestra di dialogo **Proprietà indice** apportare le modifiche desiderate. È ad esempio possibile aggiungere o rimuovere una colonna dalla chiave di indice o modificare l'impostazione di un'opzione di indice.  
  
#### <a name="to-modify-index-columns"></a>Per modificare le colonne indice  
  
1.  Per aggiungere, rimuovere o modificare la posizione di una colonna indice, selezionare la pagina **Generale** della finestra di dialogo **Proprietà indice** .  
  
##  <a name="TsqlProcedure"></a> Uso di Transact-SQL  
  
#### <a name="to-modify-an-index"></a>Per modificare un indice  
  
1.  Connettersi al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dalla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra delle query e fare clic su **Esegui**. In questo esempio viene eliminato e ricreato un indice esistente sulla colonna `ProductID` della tabella `Production.WorkOrder` tramite l'opzione `DROP_EXISTING` . Vengono inoltre impostate le opzioni `FILLFACTOR` e `PAD_INDEX` .  
  
     [!code-sql[IndexDDL#CreateIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_1.sql)]  
  
     Nell'esempio seguente viene usato ALTER INDEX per impostare diverse opzioni sull'indice `AK_SalesOrderHeader_SalesOrderNumber`.  
  
     [!code-sql[IndexDDL#AlterIndex4](../../relational-databases/indexes/codesnippet/tsql/modify-an-index_2.sql)]  
  
#### <a name="to-modify-index-columns"></a>Per modificare le colonne indice  
  
1.  Per aggiungere, rimuovere o modificare la posizione di una colonna dell'indice, è necessario eliminare e ricreare l'indice.  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Impostare le opzioni di indice](../../relational-databases/indexes/set-index-options.md)   
 [Ridenominazione di indici](../../relational-databases/indexes/rename-indexes.md)  
  
  
