---
title: sp_control_plan_guide (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_control_plan_guide
- sp_control_plan_guide_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_control_plan_guide
ms.assetid: c96d43d5-6507-4d66-b3f5-f44c0617cb5c
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9f1e9e78020787bcec4f6b3a04efbdc4ba466023
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spcontrolplanguide-transact-sql"></a>sp_control_plan_guide (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina, abilita o disabilita una guida di piano.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_control_plan_guide [ @operation = ] N'<control_option>'  
  [ , [ @name = ] N'plan_guide_name' ]  
  
<control_option>::=  
{   
    DROP   
  | DROP ALL  
  | DISABLE  
  | DISABLE ALL  
  | ENABLE   
  | ENABLE ALL  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 **N'** *plan_guide_name* **'**  
 Viene specificata la guida di piano da eliminare, abilitare o disabilitare. *plan_guide_name* viene risolto nel database corrente. Se non specificato, *plan_guide_name* valore predefinito è NULL.  
  
 DROP  
 Elimina la Guida di piano specificata in *plan_guide_name*. Dopo l'eliminazione di una guida di piano, le future esecuzioni di una query a cui la guida di piano era in precedenza associata non saranno più influenzate dalla guida di piano.  
  
 DROP ALL  
 Elimina tutte le guide di piano nel database corrente. **N' * * * plan_guide_name* non può essere utilizzato quando DROP ALL è specificata.  
  
 DISABLE  
 Disabilita la Guida di piano specificata in *plan_guide_name*. Dopo la disabilitazione di una guida di piano, le future esecuzioni di una query a cui la guida di piano era in precedenza associata non saranno più influenzate dalla guida di piano.  
  
 DISABLE ALL  
 Disabilita tutte le guide di piano nel database corrente. **N' * * * plan_guide_name* non può essere utilizzato quando DISABLE ALL è specificata.  
  
 ENABLE  
 Consente la Guida di piano specificata in *plan_guide_name*. Dopo che è stata abilitata, una guida di piano può essere associata a una query idonea. Per impostazione predefinita, le guide di piano vengono abilitate in fase di creazione.  
  
 ENABLE ALL  
 Abilita tutte le guide di piano nel database corrente. **N'***plan_guide_name***'** non può essere utilizzato quando ENABLE ALL è specificata.  
  
## <a name="remarks"></a>Osservazioni  
 Se si tenta di eliminare o modificare una funzione, una stored procedure o un trigger DML a cui viene fatto riferimento in una guida di piano abilitata o disabilitata, viene generato un errore.  
  
 La disabilitazione di una guida di piano disabilitata o l'abilitazione di una guida di piano abilitata non ha alcun effetto e viene eseguita senza la restituzione di un errore.  
  
 Le guide di piano non sono disponibili in ogni edizione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Edizioni e funzionalità supportate per SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md). Tuttavia, è possibile eseguire **sp_control_plan_guide** con l'opzione DROP o DROP ALL in qualsiasi edizione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eseguire **sp_control_plan_guide** su una Guida di piano di tipo OBJECT (creato specificando  **@type ='** oggetto **'** ) richiede l'autorizzazione ALTER per l'oggetto che fa riferimento la Guida di piano. Per tutte le altre guide di piano è necessario disporre dell'autorizzazione ALTER DATABASE.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-enabling-disabling-and-dropping-a-plan-guide"></a>A. Abilitazione, disabilitazione ed eliminazione di una guida di piano  
 Nell'esempio seguente viene creata, disabilitata, attivata ed eliminata una guida di piano.  
  
```  
--Create a procedure on which to define the plan guide.  
IF OBJECT_ID(N'Sales.GetSalesOrderByCountry', N'P') IS NOT NULL  
    DROP PROCEDURE Sales.GetSalesOrderByCountry;  
GO  
CREATE PROCEDURE Sales.GetSalesOrderByCountry   
    (@Country nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country;  
END  
GO  
--Create the plan guide.  
EXEC sp_create_plan_guide N'Guide3',  
    N'SELECT *  
    FROM Sales.SalesOrderHeader AS h   
    INNER JOIN Sales.Customer AS c ON h.CustomerID = c.CustomerID  
    INNER JOIN Sales.SalesTerritory AS t ON c.TerritoryID = t.TerritoryID  
    WHERE t.CountryRegionCode = @Country',  
    N'OBJECT',  
    N'Sales.GetSalesOrderByCountry',  
    NULL,  
    N'OPTION (OPTIMIZE FOR (@Country = N''US''))';  
GO  
--Disable the plan guide.  
EXEC sp_control_plan_guide N'DISABLE', N'Guide3';  
GO  
--Enable the plan guide.  
EXEC sp_control_plan_guide N'ENABLE', N'Guide3';  
GO  
--Drop the plan guide.  
EXEC sp_control_plan_guide N'DROP', N'Guide3';  
```  
  
### <a name="b-disabling-all-plan-guides-in-the-current-database"></a>B. Disabilitazione di tutte le guide di piano nel database corrente  
 Nell'esempio seguente vengono disabilitate tutte le guide di piano nel database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_control_plan_guide N'DISABLE ALL';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [Guide di piano](../../relational-databases/performance/plan-guides.md)  
  
  
