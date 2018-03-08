---
title: DROP PROCEDURE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 05/11/2017
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
- DROP PROCEDURE
- DROP_PROCEDURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing stored procedures
- dropping procedure groups
- deleting stored procedures
- deleting procedure groups
- DROP PROCEDURE statement
- dropping stored procedures
- stored procedures [SQL Server], removing
- removing procedure groups
ms.assetid: 1c2d7235-7b9b-4336-8f17-429e7d82c2c3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: aef67c09e34bf23fa1185cc10b12ff3fb88e6a6c
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="drop-procedure-transact-sql"></a>DROP PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Rimuove una o più stored procedure o gruppi di stored procedure dal database corrente in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP { PROC | PROCEDURE } [ IF EXISTS ] { [ schema_name. ] procedure } [ ,...n ]  
```  
  
```sql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP { PROC | PROCEDURE } { [ schema_name. ] procedure_name }  
```  
  
## <a name="arguments"></a>Argomenti  
 *SE ESISTE*  
 **Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Elimina in modo condizionale la procedura solo se esiste già.  
  
 *schema_name*  
 Nome dello schema a cui appartiene la procedura. Non è possibile specificare un nome di server o di database.  
  
 *procedure*  
 Nome della stored procedure o del gruppo di stored procedure da rimuovere. Non è possibile eliminare singole procedure all'interno di un gruppo di procedure numerate. In questo caso, viene eliminato l'intero gruppo.  
  
## <a name="best-practices"></a>Procedure consigliate  
 Prima di rimuovere qualsiasi stored procedure, verificare la presenza di eventuali oggetti dipendenti e modificare tali oggetti di conseguenza, L'eliminazione di una stored procedure può causare errori in oggetti e script dipendenti, se tali oggetti non vengono aggiornati. Per ulteriori informazioni, vedere [visualizzare le dipendenze di una Stored Procedure](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)  
  
## <a name="metadata"></a>Metadati  
 Per visualizzare un elenco di procedure esistenti, eseguire una query di **Sys. Objects** vista del catalogo. Per visualizzare la definizione della routine, eseguire una query di **Sys. sql_modules** vista del catalogo.  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 Richiede **controllo** autorizzazione per la procedura, o **ALTER** l'autorizzazione per lo schema a cui appartiene la stored procedure o l'appartenenza di **db_ddladmin** ruolo predefinito del server .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si rimuove la stored procedure `dbo.uspMyProc` nel database corrente.  
  
```  
DROP PROCEDURE dbo.uspMyProc;  
GO  
```  
  
 Nell'esempio seguente vengono rimosse varie stored procedure dal database corrente.  
  
```  
DROP PROCEDURE dbo.uspGetSalesbyMonth, dbo.uspUpdateSalesQuotes, dbo.uspGetSalesByYear;  
```  
  
 L'esempio seguente rimuove il `dbo.uspMyProc` stored procedure se esiste, ma non viene generato un errore se la procedura non esiste. Questa sintassi è stata introdotta in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)].  
  
```  
DROP PROCEDURE IF EXISTS dbo.uspMyProc;  
GO  
```  
  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [Sys. Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Eliminare una stored procedure](../../relational-databases/stored-procedures/delete-a-stored-procedure.md)  
  
  


