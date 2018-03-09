---
title: sp_tables_ex (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 428d75a311ba1f160d8200f4b949e6a7eeee8088
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2017
---
# <a name="sptablesex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni relative alle tabelle del server collegato specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@table_server=** ] **'***table_server***'**  
 Nome del server collegato di cui si desidera ottenere informazioni di tabella. *table_server* è **sysname**, non prevede alcun valore predefinito.  
  
 [ **,** [  **@table_name=** ] **'***table_name***'**]  
 Nome della tabella di cui si desidera ottenere informazioni sul tipo di dati. *TABLE_NAME*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_schema=** ] **'***table_schema***'**]  
 Schema della tabella. *TABLE_SCHEMA*è **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_catalog=** ] **'***table_catalog***'**  
 Il nome del database in cui è specificato *table_name* risiede. *TABLE_CATALOG* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@table_type=** ] **'***table_type***'**  
 Tipo di tabella da restituire. *TABLE_TYPE* è **sysname**, con un valore predefinito è NULL e può avere uno dei valori seguenti.  
  
|Valore|Description|  
|-----------|-----------------|  
|**ALIAS**|Nome di un alias.|  
|**TEMPORANEA GLOBALE**|Nome di una tabella temporanea disponibile nell'intero sistema.|  
|**MEMORIA TEMPORANEA LOCALE**|Nome di una tabella temporanea disponibile solo nel processo corrente.|  
|**SYNONYM**|Nome di un sinonimo.|  
|**TABELLA DI SISTEMA**|Nome di una tabella di sistema.|  
|**VISTA DI SISTEMA**|Nome di una vista di sistema.|  
|**TABLE**|Nome di una tabella utente.|  
|**VIEW**|Nome di una vista.|  
  
 [  **@fUsePattern=** ] **'***fUsePattern***'**  
 Determina se i caratteri **_**,  **%** , **[**, e **]** vengono interpretati come caratteri jolly. I valori validi sono 0 (utilizzo dei criteri di ricerca disattivato) e 1 (utilizzo dei criteri di ricerca attivato). *fUsePattern* è **bit**, con un valore predefinito è 1.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Nessuno  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nome del qualificatore della tabella. Vari prodotti DBMS supportano nomi in tre parti per le tabelle (*qualificatore***.** *proprietario***.** *nome*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. In altri prodotti rappresenta il nome del server dell'ambiente di database della tabella. Questo campo può essere NULL.|  
|**TABLE_SCHEM**|**sysname**|Nome del proprietario della tabella. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome dell'utente del database che ha creato la tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_NAME**|**sysname**|Nome della tabella. Questo campo restituisce sempre un valore.|  
|**TABLE_TYPE**|**varchar (32)**|Tabella, tabella di sistema o vista.|  
|**SEZIONE OSSERVAZIONI**|**varchar(254)**|In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene restituito alcun valore per questa colonna.|  
  
## <a name="remarks"></a>Osservazioni  
 **sp_tables_ex** viene eseguita tramite una query di set di righe delle tabelle del **IDBSchemaRowset** interfaccia del provider OLE DB corrispondente a *table_server*. Il *table_name*, *table_schema*, *table_catalog*, e *colonna* i parametri vengono passati a questa interfaccia per limitare le righe restituito.  
  
 **sp_tables_ex** restituisce un risultato vuoto se il provider OLE DB del server collegato specificato non supporta il set di righe delle tabelle di impostare il **IDBSchemaRowset** interfaccia.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulle tabelle contenute nello schema `HumanResources` del database [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] nel server collegato `LONDON2`.  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Query distribuite Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
