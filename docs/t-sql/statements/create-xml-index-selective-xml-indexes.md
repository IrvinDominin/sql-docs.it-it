---
title: CREATE XML INDEX (indici XML selettivi) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1f510151-41d5-45c2-9cd0-b1ca0246fffe
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b0cd1c2dd0c77409768e8ea7838724ca4d6b827e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="create-xml-index-selective-xml-indexes"></a>CREATE XML INDEX (indici XML selettivi)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crea un nuovo indice XML selettivo secondario in un unico percorso già indicizzato da un indice XML selettivo esistente. È inoltre possibile creare indici XML selettivi primari. Per informazioni, vedere [Create, Alter e Drop gli indici XML selettivi](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CREATE XML INDEX index_name  
    ON <table_object> ( xml_column_name )  
    USING XML INDEX sxi_index_name  
    FOR ( <xquery_or_sql_values_path> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<xquery_or_sql_values_path>::=   
<path_name>   
  
<path_name> ::=   
character string literal  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
xmlnamespace_uri AS xmlnamespace_prefix  
  
<index_options> ::=   
(    
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> Argomenti  
 *index_name*  
 Nome del nuovo indice che si desidera creare. I nomi degli indici devono essere necessariamente univoci all'interno di una tabella, ma non all'interno di un database. I nomi di indice devono rispettare le regole di [identificatori](../../relational-databases/databases/database-identifiers.md).  
  
 ON  *\<table_object >* è la tabella che contiene la colonna XML da indicizzare. È possibile usare i formati seguenti:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
 *xml_column_name*  
 Nome della colonna XML contenente il percorso che si desidera indicizzare.  
  
 USING XML INDEX *sxi_index_name*  
 Nome dell'indice XML selettivo esistente.  
  
 PER **(** \<xquery_or_sql_values_path > **)** è il nome del percorso indicizzato in cui creare l'indice XML selettivo secondario. Il percorso che si desidera indicizzare è il nome assegnato dall'istruzione CREATE SELECTIVE XML INDEX. Per altre informazioni, vedere [CREATE SELECTIVE XML INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
 CON \<index_options > per informazioni sulle opzioni di indice, vedere [CREATE XML INDEX](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="remarks"></a>Osservazioni  
 In ogni colonna XML della tabella di base potrebbero essere presenti più indici XML selettivi secondari.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Prima di poter creare indici XML selettivi secondari in una colonna, è necessario che per tale colonna esista un indice XML selettivo.  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER per la tabella o la vista. L'utente deve essere un membro del ruolo predefinito del server **sysadmin** o dei ruoli predefiniti del database **db_ddladmin** e **db_owner** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creato un indice XML selettivo secondario nel percorso `pathabc`. Il percorso da indicizzare è il nome assegnato dal [CREATE SELECTIVE XML INDEX &#40; Transact-SQL &#41; ](../../t-sql/statements/create-selective-xml-index-transact-sql.md).  
  
```  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR ( pathabc );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Creare, modificare o eliminare indici XML selettivi secondari](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)  
  
  

