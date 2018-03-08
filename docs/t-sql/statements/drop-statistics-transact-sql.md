---
title: DROP STATISTICS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/22/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP STATISTICS
- DROP_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing statistics
- column statistics [SQL Server]
- DROP STATISTICS statement
- deleting statistics
- dropping statistics
- table statistics [SQL Server]
- statistical information [SQL Server], removing
ms.assetid: 222806b7-4e45-445b-8cd0-bd5461f3ca4a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 34cc65eaccfdfcbffd38e93f613f2b2d34de23d0
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="drop-statistics-transact-sql"></a>DROP STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Elimina le statistiche di più raccolte all'interno delle tabelle specificate del database corrente.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP STATISTICS table.statistics_name | view.statistics_name [ ,...n ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP STATISTICS [ schema_name . ] table_name.statistics_name   
[;]  
```  
  
## <a name="arguments"></a>Argomenti  
 *tabella* | *visualizzazione*  
 Nome della tabella o vista indicizzata di destinazione di cui si desidera eliminare le statistiche. I nomi di tabelle e viste devono essere conformi alle regole per [identificatori del Database](../../relational-databases/databases/database-identifiers.md). Il nome del proprietario della tabella o vista è facoltativo.  
  
 *nome_statistiche*  
 Nome del gruppo di statistiche da eliminare. I nomi dei gruppi di statistiche devono essere conformi alle regole per gli identificatori.  
  
## <a name="remarks"></a>Osservazioni  
 Eliminare le statistiche con cautela, in quanto l'operazione può influire sul piano di esecuzione scelto da Query Optimizer.  
  
 Le statistiche negli indici non possono essere eliminate tramite DROP STATISTICS. Le statistiche vengono mantenute per tutta l'esistenza dell'indice.  
  
 Per ulteriori informazioni sulla visualizzazione delle statistiche, vedere [DBCC SHOW_STATISTICS &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione ALTER per la tabella o la vista.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-dropping-statistics-from-a-table"></a>A. Eliminazione di statistiche da una tabella  
 Nell'esempio seguente vengono eliminati i gruppi (raccolte) di statistiche di due tabelle, ossia il gruppo (raccolta) di statistiche `VendorCredit` della tabella `Vendor` e il gruppo (raccolta) di statistiche `CustomerTotal` della tabella `SalesOrderHeader`.  
  
```  
-- Create the statistics groups.  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS VendorCredit  
    ON Purchasing.Vendor (Name, CreditRating)  
    WITH SAMPLE 50 PERCENT  
CREATE STATISTICS CustomerTotal  
    ON Sales.SalesOrderHeader (CustomerID, TotalDue)  
    WITH FULLSCAN;  
GO  
DROP STATISTICS Purchasing.Vendor.VendorCredit, Sales.SalesOrderHeader.CustomerTotal;  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-dropping-statistics-from-a-table"></a>B. Eliminazione di statistiche da una tabella  
 Eliminare gli esempi seguenti il `CustomerStats1` statistiche dalla tabella `Customer`.  
  
```  
DROP STATISTICS Customer.CustomerStats1;  
DROP STATISTICS dbo.Customer.CustomerStats1;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [Sys. stats_columns &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
  
  


