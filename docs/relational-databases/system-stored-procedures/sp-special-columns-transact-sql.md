---
title: sp_datatype_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_special_columns_TSQL
- sp_special_columns
dev_langs: TSQL
helpviewer_keywords: sp_special_columns
ms.assetid: 0b0993f8-73e0-402b-8c6c-1b0963956f5d
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 902c3fc7afb5ede1af0d49ef4429f8177b2101ad
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2018
---
# <a name="spspecialcolumns-transact-sql"></a>sp_special_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce il set di colonne ottimale per l'identificazione univoca di una riga nella tabella. Restituisce inoltre le colonne che vengono aggiornate automaticamente quando qualsiasi valore della riga viene aggiornato tramite una transazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
sp_special_columns [ @table_name = ] 'table_name'     
     [ , [ @table_owner = ] 'table_owner' ]   
     [ , [ @qualifier = ] 'qualifier' ]   
     [ , [ @col_type = ] 'col_type' ]   
     [ , [ @scope = ] 'scope' ]  
     [ , [ @nullable = ] 'nullable' ]   
     [ , [ @ODBCVer = ] 'ODBCVer' ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @table_name=] '*table_name*'  
 Nome della tabella utilizzata per restituire informazioni sul catalogo. *nome* è **sysname**, non prevede alcun valore predefinito. I criteri di ricerca con caratteri jolly non sono supportati.  
  
 [ @table_owner=] '*table_owner*'  
 Proprietario della tabella utilizzata per restituire informazioni sul catalogo. *proprietario* è **sysname**, con un valore predefinito è NULL. I criteri di ricerca con caratteri jolly non sono supportati. Se *proprietario* viene omesso, si applicano le regole di visibilità della tabella predefinite del sistema DBMS sottostante.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se l'utente corrente è il proprietario di una tabella con il nome specificato, vengono restituite le colonne di tale tabella. Se *proprietario* viene omesso e l'utente corrente non dispone di una tabella dell'oggetto specificato *nome*, viene eseguita la ricerca per una tabella dell'oggetto specificato *nome* dal database di proprietà proprietario. Se la tabella esiste, vengono restituite le colonne corrispondenti.  
  
 [ @qualifier=] '*qualificatore*'  
 Nome del qualificatore di tabella. *qualificatore* è **sysname**, con un valore predefinito è NULL. Vari prodotti DBMS supportano nomi in tre parti per le tabelle (*composti*). In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] questa colonna rappresenta il nome del database. In alcuni prodotti rappresenta il nome del server dell'ambiente di database della tabella.  
  
 [ @col_type=] '*col_type*'  
 Tipo di colonna. *col_type* è **char (**1**)**, con valore predefinito è R. tipo R restituisce la colonna o ottimale set di colonne che, tramite il recupero dei valori di colonna o delle colonne, che consente di ogni riga nell'oggetto specificato tabella per essere identificato in modo univoco. Una colonna può essere una pseudocolonna progettata a questo scopo oppure la colonna o le colonne di un indice univoco della tabella. Il tipo di colonna V restituisce le eventuali colonne della tabella specificata che vengono aggiornate automaticamente dall'origine dati in corrispondenza dell'aggiornamento di un valore della riga tramite una transazione.  
  
 [ @scope=] '*ambito*'  
 Ambito minimo richiesto per ROWID. *ambito* è **char (**1**)**, con valore predefinito è l'ambito T. C specifica che il valore ROWID è valido solo se posizionato in tale riga. L'ambito T indica che il valore ROWID è valido per la transazione.  
  
 [ @nullable=] '*nullable*'  
 Indica se le colonne speciali possono accettare un valore null. *ammette valori null* è **char (**1**)**, con valore predefinito è U Specifica le colonne speciali che non ammettono valori null. mentre U specifica le colonne che ammettono parzialmente valori Null.  
  
 [ @ODBCVer=] '*ODBCVer*'  
 Versione ODBC utilizzata. *ODBCVer* è **int (**4**)**, con un valore predefinito è 2. che indica ODBC versione 2.0. Per ulteriori informazioni sulla differenza tra la versione 2.0 e ODBC versione 3.0, vedere la specifica ODBC SQLSpecialColumns per ODBC versione 3.0.  
  
## <a name="return-code-values"></a>Valori restituiti  
 None  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|SCOPE|**smallint**|Ambito effettivo dell'ID della riga. Il Può essere 0, 1 o 2. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Restituisce sempre 0. Questo campo restituisce sempre un valore.<br /><br /> 0 = SQL_SCOPE_CURROW. La validità dell'ID di riga è garantita solo mentre si è posizionati in tale riga. Una selezione successiva in base all'ID di riga potrebbe non restituire la riga se questa è stata aggiornata o eliminata da un'altra transazione.<br /><br /> 1 = SQL_SCOPE_TRANSACTION. La validità dell'ID di riga è garantita per l'intera durata della transazione corrente.<br /><br /> 2 = SQL_SCOPE_SESSION. La validità dell'ID della riga è garantita per l'intera durata della sessione (oltre i limiti delle transazioni).|  
|COLUMN_NAME|**sysname**|Nome della colonna per ogni colonna del *tabella*restituito. Questo campo restituisce sempre un valore.|  
|DATA_TYPE|**smallint**|Tipo di dati SQL ODBC.|  
|TYPE_NAME|**sysname**|Nome del tipo di dati dipende dall'origine dati; ad esempio, **char**, **varchar**, **money**, o **testo**.|  
|PRECISION|**Int**|Precisione della colonna nell'origine dati. Questo campo restituisce sempre un valore.|  
|LENGTH|**Int**|Lunghezza, espressa in byte, necessaria per il tipo di dati in formato binario nell'origine dati, ad esempio, 10 per **char (**10**)**, 4 per **intero**e 2 per **smallint** .|  
|SCALE|**smallint**|Scala della colonna nell'origine dati. Per i tipi di dati in cui la scala non è applicabile viene restituito NULL.|  
|PSEUDO_COLUMN|**smallint**|Indica se la colonna è una pseudocolonna. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce sempre 1:<br /><br /> 0 = SQL_PC_UNKNOWN<br /><br /> 1 = SQL_PC_NOT_PSEUDO<br /><br /> 2 = SQL_PC_PSEUDO|  
  
## <a name="remarks"></a>Osservazioni  
 sp_datatype_columns corrisponde a SQLSpecialColumns in ODBC. I risultati restituiti vengono ordinati in base a SCOPE.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT per lo schema.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulla colonna che identifica in modo univoco le righe nella tabella `HumanResources.Department`.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_special_columns @table_name = 'Department'   
    ,@table_owner = 'HumanResources';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Catalogo Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
