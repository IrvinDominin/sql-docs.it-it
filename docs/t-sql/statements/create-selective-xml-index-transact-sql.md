---
title: CREARE l'indice XML selettivo (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d769f62-f646-4057-b93a-bf5f90e935ed
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 29a2a6eaec3ebbbafef0fcead331835921c7da44
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-selective-xml-index-transact-sql"></a>CREATE SELECTIVE XML INDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crea un nuovo indice XML selettivo nella tabella e nella colonna XML specificate. Gli indici XML selettivi contribuiscono al miglioramento delle prestazioni relative all'indicizzazione e all'esecuzione di query XML indicizzando solo il subset di nodi su cui vengono in genere eseguite query. È inoltre possibile creare indici XML selettivi secondari. Per informazioni, vedere [Create, Alter e Drop indici XML selettivi secondari](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE SELECTIVE XML INDEX index_name  
    ON <table_object> (xml_column_name)  
    [WITH XMLNAMESPACES (<xmlnamespace_list>)]  
    FOR (<promoted_node_path_list>)  
    [WITH (<index_options>)]  
  
<table_object> ::=  
 { [database_name. [schema_name ] . | schema_name. ] table_name }  
  
<promoted_node_path_list> ::=   
<named_promoted_node_path_item> [, <promoted_node_path_list>]  
  
<named_promoted_node_path_item> ::=   
<path_name> = <promoted_node_path_item>  
  
<promoted_node_path_item>::=  
<xquery_node_path_item> | <sql_values_node_path_item>  
  
<xquery_node_path_item> ::=   
<node_path> [AS XQUERY <xsd_type_or_node_hint>] [SINGLETON]  
  
<xsd_type_or_node_hint> ::=   
[<xsd_type>] [MAXLENGTH(x)] | node()  
  
<sql_values_node_path_item> ::=  
<node_path> AS SQL <sql_type> [SINGLETON]  
  
<node_path> ::=   
character_string_literal  
  
<xsd_type> ::=   
character_string_literal  
  
<sql_type> ::=   
identifier  
  
<path_name> ::=   
identifier  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
<xmlnamespace_uri> AS <xmlnamespace_prefix>  
  
<xml_namespace_uri> ::=   
character_string_literal  
  
<xml_namespace_prefix> ::=   
identifier  
  
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
  
 *\<table_object >* è la tabella che contiene la colonna XML da indicizzare. Utilizzare uno dei seguenti formati:  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
-   `table_name`  
  
 *xml_column_name*  
 Nome della colonna XML contenente i percorsi che si desidera indicizzare.  
  
 [WITH XMLNAMESPACES **(**\<xmlnamespace_list >**)**] è riportato l'elenco degli spazi dei nomi utilizzati nei percorsi da indicizzare. Per informazioni sulla sintassi della clausola WITH XMLNAMESPACES, vedere [WITH XMLNAMESPACES &#40; Transact-SQL &#41; ](../../t-sql/xml/with-xmlnamespaces.md).  
  
 PER **(**\<promoted_node_path_list >**)** è riportato l'elenco di percorsi da indicizzare con hint di ottimizzazione facoltativi. Per informazioni sui percorsi e hint di ottimizzazione che è possibile specificare nell'istruzione CREATE o ALTER, vedere [specificare percorsi e hint di ottimizzazione per indici XML selettivi](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md).  
  
 CON  *\<index_options >* per informazioni sulle opzioni di indice, vedere [CREATE XML INDEX &#40; Indici XML selettivi &#41; ](../../t-sql/statements/create-xml-index-selective-xml-indexes.md).  
  
## <a name="best-practices"></a>Procedure consigliate  
 Creare un indice XML selettivo anziché un indice XML comune nella maggior parte dei casi per migliorare le prestazioni e usufruire di uno spazio di archiviazione più efficiente. Non è tuttavia consigliabile creare un indice XML selettivo in presenza di una delle condizioni indicate di seguito.  
  
-   È necessario eseguire il mapping di un numero elevato di percorsi del nodo.  
  
-   È necessario supportare le query per elementi sconosciuti o in una posizione sconosciuta.  
  
## <a name="limitations-and-restrictions"></a>Limitazioni e restrizioni  
 Per informazioni sulle limitazioni e restrizioni, vedere [gli indici XML selettivi &#40; SXI &#41; ](../../relational-databases/xml/selective-xml-indexes-sxi.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione ALTER per la tabella o la vista. L'utente deve essere un membro del ruolo predefinito del server **sysadmin** o dei ruoli predefiniti del database **db_ddladmin** e **db_owner** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata la sintassi per la creazione di un indice XML selettivo. Vengono inoltre mostrate diverse varianti della sintassi per la descrizione dei percorsi che si desidera indicizzare, con hint di ottimizzazione facoltativi.  
  
```  
CREATE TABLE Tbl ( id INT PRIMARY KEY, xmlcol XML );  
GO  
CREATE SELECTIVE XML INDEX sxi_index  
ON Tbl(xmlcol)  
FOR(  
    pathab   = '/a/b' as XQUERY 'node()',  
    pathabc  = '/a/b/c' as XQUERY 'xs:double',   
    pathdtext = '/a/b/d/text()' as XQUERY 'xs:string' MAXLENGTH(200) SINGLETON,  
    pathabe = '/a/b/e' as SQL NVARCHAR(100)  
);  
```  
  
 Nell'esempio seguente è inclusa una clausola WITH XMLNAMESPACES.  
  
```  
CREATE SELECTIVE XML INDEX on T1(C1)  
WITH XMLNAMESPACES ('http://www.tempuri.org/' as myns)  
FOR ( path1 = '/myns:book/myns:author/text()' );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML selettivi &#40;SXI&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [Creare, modificare ed eliminare indici XML selettivi](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)   
 [Specificare percorsi e hint di ottimizzazione per indici XML selettivi](../../relational-databases/xml/specify-paths-and-optimization-hints-for-selective-xml-indexes.md)  
  
  

