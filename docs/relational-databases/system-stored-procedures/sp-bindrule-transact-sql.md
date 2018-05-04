---
title: sp_bindrule (Transact-SQL) | Documenti Microsoft
ms.custom: ''
ms.date: 11/25/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_bindrule_TSQL
- sp_bindrule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindrule
ms.assetid: 2606073e-c52f-498d-a923-5026b9d97e67
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3aec507212896d9ed03cdb7053b320743b2236c9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="spbindrule-transact-sql"></a>sp_bindrule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Associa una regola a una colonna o a un tipo di dati alias.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Uso[Unique Constraints and Check Constraints](../../relational-databases/tables/unique-constraints-and-check-constraints.md) invece. Vincoli CHECK vengono creati utilizzando la parola chiave CHECK del [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) o [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) istruzioni.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_bindrule [ @rulename = ] 'rule' ,   
     [ @objname = ] 'object_name'   
     [ , [ @futureonly = ] 'futureonly_flag' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@rulename=**] **'***regola***'**  
 Nome della regola creata tramite l'istruzione CREATE RULE. *regola* viene **nvarchar(776)**, non prevede alcun valore predefinito.  
  
 [  **@objname=**] **'***object_name***'**  
 Tabella e colonna, o tipo di dati alias a cui associare la regola. Una regola non può essere associata a una colonna **text**, **ntext**, **image**, **varchar(max)**, **nvarchar(max)**, **varbinary(max)**, **xml**, di tipo CLR definito dall'utente o **timestamp**, né a una colonna calcolata.  
  
 *object_name* viene **nvarchar(776)** non prevede alcun valore predefinito. Se *object_name* è un nome di una sola parte, viene risolto come tipo di dati alias. Se è un nome in due o tre parti, viene prima risolto come tabella e colonna. Se la risoluzione non riesce, viene risolto come tipo di dati alias. Per impostazione predefinita, le colonne esistenti del tipo di dati alias ereditano *regola* , a meno che una regola è stata associata direttamente alla colonna.  
  
> [!NOTE]  
>  *object_name* può contenere parentesi **[** e **]** caratteri come caratteri delimitatori. Per altre informazioni, vedere [Identificatori del database](../../relational-databases/databases/database-identifiers.md).  
  
> [!NOTE]  
>  Le regole create nelle espressioni che utilizzano tipi di dati alias possono essere associate a colonne o a tipi di dati alias, ma non è possibile compilarle quando un altro elemento fa riferimento ad esse. Evitare di utilizzare le regole create nei tipi di dati alias.  
  
 [  **@futureonly=** ] **'***futureonly_flag***'**  
 Utilizzato solo quando si associa una regola a un tipo di dati alias. *future_only_flag* viene **varchar(15)** con un valore predefinito è NULL. Questo parametro quando è impostato su **futureonly** impedisce che le colonne esistenti del tipo di dati alias ereditano la nuova regola. Se *futureonly_flag* è NULL, la nuova regola è associata a tutte le colonne del tipo di dati alias alcuna regola o che utilizzano la regola esistente del tipo di dati alias.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile associare una nuova regola a una colonna (sebbene sia preferibile utilizzare un vincolo CHECK) o a un tipo di dati alias con **sp_bindrule** senza disassociare una regola esistente. La regola precedente verrà infatti ignorata. Se una regola viene associata a una colonna con un vincolo CHECK esistente, vengono valutate tutte le restrizioni. Non è possibile associare una regola a un tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La regola viene applicata quando si esegue un'istruzione INSERT, non in fase di associazione. È possibile associare una regola di tipo carattere a una colonna di **numerico** del tipo di dati, anche se un'operazione di inserimento non è valida.  
  
 Le colonne esistenti del tipo di dati alias ereditano la nuova regola a meno che non *futureonly_flag* è specificato come **futureonly**. Le nuove colonne definite con il tipo di dati alias ereditano sempre la regola. Tuttavia, se la clausola ALTER COLUMN di un'istruzione ALTER TABLE imposta una colonna su un tipo di dati alias associato a una regola, la regola associata al tipo di dati non viene ereditata dalla colonna. La regola deve essere associata in modo specifico per la colonna tramite **sp_bindrule**.  
  
 Quando si associa una regola a una colonna, informazioni correlate vengono aggiunte al **Columns** tabella. Quando si associa una regola a un tipo di dati alias, informazioni correlate vengono aggiunte al **Sys. Types** tabella.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per associare una regola a una colonna di tabella, è necessario disporre dell'autorizzazione ALTER per la tabella. Per associare una regola a un tipo di dati alias, è richiesta l'autorizzazione CONTROL per il tipo di dati alias o l'autorizzazione ALTER per lo schema a cui appartiene il tipo.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-binding-a-rule-to-a-column"></a>A. Associazione di una regola a una colonna  
 Supponendo che la regola `today` sia stata creata nel database corrente tramite l'istruzione CREATE RULE, nell'esempio seguente viene associata tale regola alla colonna `HireDate` della tabella `Employee`. Quando si aggiunge una riga alla tabella `Employee`, i dati della colonna `HireDate` vengono verificati in base alla regola `today`.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'today', 'HumanResources.Employee.HireDate';  
```  
  
### <a name="b-binding-a-rule-to-an-alias-data-type"></a>B. Associazione di una regola a un tipo di dati alias  
 Supponendo che esistano la regola `rule_ssn` e il tipo di dati alias `ssn`, nell'esempio seguente viene associata la regola `rule_ssn` a `ssn`. In un'istruzione CREATE TABLE le colonne di tipo `ssn` ereditano la regola `rule_ssn`. Le colonne esistenti del tipo `ssn` anche ereditare il `rule_ssn` regola, a meno che non **futureonly** specificato per *futureonly_flag*, o `ssn` è associata direttamente una regola. Le regole associate alle colonne sono sempre prioritarie rispetto a quelle associate ai tipi di dati.  
  
```  
USE master;  
GO  
EXEC sp_bindrule 'rule_ssn', 'ssn';  
```  
  
### <a name="c-using-the-futureonlyflag"></a>C. Utilizzo di futureonly_flag  
 Nell'esempio seguente viene associata la regola `rule_ssn` al tipo di dati alias `ssn`. Poiché è stato specificato il flag `futureonly`, l'operazione non ha alcun effetto sulle colonne di tipo `ssn` esistenti.  
  
```  
USE master;  
GO  
EXEC sp_bindrule rule_ssn, 'ssn', 'futureonly';  
```  
  
### <a name="d-using-delimited-identifiers"></a>D. Utilizzo di identificatori delimitati  
 Nell'esempio seguente viene illustrato come utilizzare gli identificatori delimitati in *object_name* parametro.  
  
```  
USE master;  
GO  
CREATE TABLE [t.2] (c1 int) ;  
-- Notice the period as part of the table name.  
EXEC sp_bindrule rule1, '[t.2].c1' ;  
-- The object contains two periods;   
-- the first is part of the table name   
-- and the second distinguishes the table name from the column name.  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure del motore di database &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [DROP RULE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-rule-transact-sql.md)   
 [sp_unbindrule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unbindrule-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
