---
title: sp_indexoption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_indexoption
- sp_indexoption_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_indexoption
ms.assetid: 75f836be-d322-4a53-a45d-25bee6b42a52
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d6df698f13298bf290ad1a0cb9e94ccac0bfce3f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596419"
---
# <a name="spindexoption-transact-sql"></a>sp_indexoption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta i valori dell'opzione di blocco per gli indici cluster e non cluster e per le tabelle senza indici cluster.  
  
 In [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] le opzioni per il blocco a livello di pagina, riga e tabella vengono configurate automaticamente. Non è necessario impostare queste opzioni manualmente. **sp_indexoption** utenti esperti quando un tipo di blocco specifico risulta sempre adeguato.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] Usare invece [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_indexoption [ @IndexNamePattern = ] 'table_or_index_name'   
    , [ @OptionName = ] 'option_name'   
    , [ @OptionValue = ] 'value'  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@IndexNamePattern=**] **'***table_or_index_name***'**  
 Nome completo o non qualificato di una tabella o un indice definito dall'utente. *table_or_index_name* viene **nvarchar(1035)**, non prevede alcun valore predefinito. Se si specifica un nome qualificato di indice o tabella, le virgolette sono obbligatorie. Nel caso di un nome qualificato di tabella, ovvero contenente un nome di database, il nome del database deve corrispondere a quello del database corrente. Se un nome di tabella viene specificato senza alcun indice, il valore dell'opzione specificata viene impostato per tutti gli indici in tale tabella e nella tabella stessa se non esistono indici cluster.  
  
 [  **@OptionName =**] **'***option_name***'**  
 Nome di opzione di indice. *option_name* viene **varchar(35**, non prevede alcun valore predefinito. *option_name* può avere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**AllowRowLocks**|Se è TRUE, i blocchi a livello di riga sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga. Se è FALSE, i blocchi a livello di riga non vengono utilizzati. Il valore predefinito è TRUE.|  
|**AllowPageLocks**|Se è TRUE, i blocchi a livello di pagina sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina. Se è FALSE, i blocchi a livello di pagina non vengono utilizzati. Il valore predefinito è TRUE.|  
|**DisAllowRowLocks**|Se è TRUE, i blocchi a livello di riga non vengono utilizzati. Se è FALSE, i blocchi a livello di riga sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi di riga.|  
|**DisAllowPageLocks**|Se è TRUE, i blocchi a livello di pagina non vengono utilizzati. Se è FALSE, i blocchi a livello di pagina sono consentiti durante l'accesso all'indice. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] determina quando utilizzare blocchi a livello di pagina.|  
  
 [  **@OptionValue =**] **'***valore***'**  
 Specifica se il *option_name* impostazione è abilitata (TRUE, ON, yes o 1) o disabilitata (FALSE, OFF, no o 0). *valore* viene **varchar(12)**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o maggiore di 0 (esito negativo)  
  
## <a name="remarks"></a>Note  
 Gli indici XML non sono supportati. Se si specifica un indice XML oppure un nome di tabella senza un nome di indice e la tabella include un indice XML, l'esecuzione dell'istruzione ha esito negativo. Per impostare queste opzioni, utilizzare [ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md) invece.  
  
 Per visualizzare la riga corrente e la pagina proprietà di blocco, usare [INDEXPROPERTY](../../t-sql/functions/indexproperty-transact-sql.md) o nella [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) vista del catalogo.  
  
-   L'accesso all'indice sono consentiti riga, pagina e i blocchi a livello di tabella quando **AllowRowLocks** = TRUE oppure **DisAllowRowLocks** = FALSE, e **AllowPageLocks** = TRUE oppure  **DisAllowPageLocks** = FALSE. [!INCLUDE[ssDE](../../includes/ssde-md.md)] sceglie il blocco appropriato e può eseguire un'escalation del blocco da un blocco di riga o di pagina a un blocco di tabella.  
  
 Solo un blocco a livello di tabella è consentito l'accesso all'indice quando **AllowRowLocks** = FALSE o **DisAllowRowLocks** = TRUE e **AllowPageLocks** = FALSE o  **DisAllowPageLocks** = TRUE.  
  
 Se si specifica un nome di tabella senza alcun indice, le impostazioni vengono applicate a tutti gli indici in tale tabella. Se la tabella sottostante non include indici cluster, ovvero è un heap, le impostazioni vengono applicate nel modo descritto di seguito:  
  
-   Quando **AllowRowLocks** oppure **DisAllowRowLocks** viene impostato su TRUE o FALSE, l'impostazione viene applicata all'heap e a eventuali indici non cluster associati.  
  
-   Quando **AllowPageLocks** opzione è impostata su TRUE oppure **DisAllowPageLocks** è impostato su FALSE, l'impostazione viene applicata all'heap e a eventuali indici non cluster associati.  
  
-   Quando **AllowPageLocks** opzione è impostata a FALSE oppure **DisAllowPageLocks** è impostata su TRUE, l'impostazione viene applicata completamente agli indici non cluster. ovvero vengono disattivati tutti i blocchi a livello di pagina negli indici non cluster. Nell'heap sono disattivati solo i blocchi condivisi (S), i blocchi di aggiornamento (U) e i blocchi esclusivi (X) a livello di pagina. Il [!INCLUDE[ssDE](../../includes/ssde-md.md)] può comunque acquisire un blocco preventivo a livello di pagina (IS, IU o IX) per scopi interni.  
  
## <a name="permissions"></a>Permissions  
 È necessario disporre dell'autorizzazione ALTER per la tabella.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-setting-an-option-on-a-specific-index"></a>A. Impostazione di un'opzione in un indice specifico  
 Nell'esempio seguente non consente blocchi di pagina sul `IX_Customer_TerritoryID` indicizzare nel `Customer` tabella.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_indexoption N'Sales.Customer.IX_Customer_TerritoryID',  
    N'disallowpagelocks', TRUE;  
```  
  
### <a name="b-setting-an-option-on-all-indexes-on-a-table"></a>B. Impostazione di un'opzione in tutti gli indici di una tabella  
 Nell'esempio seguente i blocchi a livello di riga vengono disattivati in tutti gli indici associati alla tabella `Product`. Viene eseguita una query sulla vista del catalogo `sys.indexes` prima e dopo l'esecuzione della stored procedure `sp_indexoption` per visualizzare i risultati dell'istruzione.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
-- Set the disallowrowlocks option on the Product table.   
EXEC sp_indexoption N'Production.Product',  
    N'disallowrowlocks', TRUE;  
GO  
--Verify the row and page lock options for all indexes on the table.  
SELECT name, type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE object_id = OBJECT_ID(N'Production.Product');  
GO  
```  
  
### <a name="c-setting-an-option-on-a-table-with-no-clustered-index"></a>C. Impostazione di un'opzione in una tabella senza indici cluster  
 Nell'esempio seguente i blocchi a livello di pagina vengono disattivati in una tabella senza indici cluster (heap). Il `sys.indexes` vista del catalogo viene eseguita una query prima e dopo il `sp_indexoption` procedure viene eseguita per visualizzare i risultati dell'istruzione.  
  
```sql  
USE AdventureWorks2012;  
GO  
--Display the current row and page lock options of the table.   
SELECT OBJECT_NAME (object_id) AS [Table], type_desc, allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
-- Set the disallowpagelocks option on the table.   
EXEC sp_indexoption DatabaseLog,  
    N'disallowpagelocks', TRUE;  
GO  
--Verify the row and page lock settings of the table.  
SELECT OBJECT_NAME (object_id) AS [Table], allow_row_locks, allow_page_locks   
FROM sys.indexes  
WHERE OBJECT_NAME (object_id) = N'DatabaseLog';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  
