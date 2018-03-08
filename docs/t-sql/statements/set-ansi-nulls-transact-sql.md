---
title: SET ANSI_NULLS (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/04/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET_ANSI_NULLS_TSQL
- ANSI_NULLS
- SET ANSI_NULLS
- ANSI_NULLS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULLS statement
- not equal to operator (<>)
- ANSI_NULLS option
- equals operator (=)
- null values [SQL Server], comparison operators
- comparison operators [SQL Server], null values
ms.assetid: aae263ef-a3c7-4dae-80c2-cc901e48c755
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: a6ef51bb13ae7372175a390a3d8c5509550a3ad1
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2017
---
# <a name="set-ansinulls-transact-sql"></a>SET ANSI_NULLS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Specifica il comportamento conforme all'ISO degli operatori di confronto Uguale a (=) e Diverso da (<>) quando vengono utilizzati con valori Null in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  In una versione futura di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ANSI_NULLS sarà ON e tutte le applicazioni in modo esplicito l'opzione viene impostata su OFF genererà un errore. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>Sintassi

```
-- Syntax for SQL Server

SET ANSI_NULLS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULLS ON
```

## <a name="remarks"></a>Osservazioni  
 Quando SET ANSI_NULLS è impostata su ON, un'istruzione SELECT che utilizza WHERE *column_name* = **NULL** restituisce zero righe, anche se sono presenti valori null in *column_name*. Un'istruzione SELECT che utilizza WHERE *column_name* <> **NULL** restituisce zero righe, anche se sono presenti valori non null in *column_name*.  
  
 Quando l'opzione SET ANSI_NULLS è impostata su OFF, gli operatori uguale a (=) e diverso da (<>) non seguono lo standard ISO. Un'istruzione SELECT che utilizza WHERE *column_name* = **NULL** restituisce le righe contenenti valori null in *column_name*. Un'istruzione SELECT che utilizza WHERE *column_name* <> **NULL** restituisce le righe che contengono valori null nella colonna. Inoltre, un'istruzione SELECT che utilizza WHERE *column_name* <> *valore_XYZ* restituisce tutte le righe che non sono *valore_XYZ* e che non sono NULL.  
  
 Quando l'opzione SET ANSI_NULLS è impostata su ON, tutti i confronti con un valore Null restituiscono UNKNOWN. Quando l'opzione SET ANSI_NULLS è impostata su OFF, i confronti di tutti i dati con un valore Null restituiscono TRUE se il valore dei dati è NULL. In caso di omissione di SET ANSI_NULLS, viene applicata l'impostazione dell'opzione ANSI_NULLS del database corrente. Per ulteriori informazioni sull'opzione di database ANSI_NULLS, vedere [ALTER DATABASE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 SET ANSI_NULLS ON influisce su un confronto solo se uno degli operandi del confronto è una variabile NULL o un valore letterale NULL. Se entrambi gli operandi del confronto sono colonne o espressioni composte, l'impostazione non ha effetto sul confronto.  
  
 Affinché uno script presenti il funzionamento previsto indipendentemente dall'opzione di database ANSI_NULLS o dall'impostazione di SET ANSI_NULLS, utilizzare IS NULL e IS NOT NULL nei confronti che potrebbero includere valori Null.  
  
 Per l'esecuzione di query distribuite, è consigliabile impostare l'opzione SET ANSI_NULLS su ON.  
  
 È inoltre necessario che l'opzione SET ANSI_NULLS sia impostata su ON durante la creazione o la modifica di indici su colonne calcolate o viste indicizzate. Se l'opzione SET ANSI_NULLS è impostata su OFF, qualsiasi istruzione CREATE, UPDATE, INSERT e DELETE eseguita in tabelle con indici su colonne calcolate o viste indicizzate avrà esito negativo. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Restituisce un errore che elenca tutte le opzioni SET che violano i valori richiesti. Inoltre, quando si esegue un'istruzione SELECT, se SET ANSI_NULLS è impostata su OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ignora i valori di indice in colonne calcolate o viste e risolvere l'operazione select come se non vi fosse alcun tali indici in tabelle o viste.  
  
> [!NOTE]  
>  ANSI_NULLS è una delle sette opzioni SET che è necessario impostare sui valori richiesti quando si utilizzano colonne calcolate o viste indicizzate. È inoltre necessario impostare su ON le opzioni ANSI_PADDING, ANSI_WARNINGS, ARITHABORT, QUOTED_IDENTIFIER e CONCAT_NULL_YIELDS_NULL, mentre l'opzione NUMERIC_ROUNDABORT deve essere impostata su OFF.  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Provider OLE DB per [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impostano automaticamente l'opzione ANSI_NULLS su ON durante la connessione. È possibile configurare questa impostazione nelle origini dei dati ODBC, negli attributi di connessione ODBC o nelle proprietà di connessione OLE DB impostate nell'applicazione prima della connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il valore predefinito per SET ANSI_NULLS è OFF.  
  
 Quando l'opzione SET ANSI_DEFAULTS è impostata su ON, l'opzione SET ANSI_NULLS risulta abilitata.  
  
 L'opzione SET ANSI_NULLS viene impostata in fase di esecuzione, non in fase di analisi.  
  
 Per visualizzare l'impostazione corrente per questa impostazione, eseguire la query seguente:
  
```  
DECLARE @ANSI_NULLS VARCHAR(3) = 'OFF';  
IF ( (32 & @@OPTIONS) = 32 ) SET @ANSI_NULLS = 'ON';  
SELECT @ANSI_NULLS AS ANSI_NULLS;  
  
```  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono utilizzati gli operatori di confronto Uguale a (`=`) e Diverso da (`<>`) per confrontare i valori `NULL` e non Null di una tabella. Nell'esempio viene inoltre illustrato che `IS NULL` non è influenzato il `SET ANSI_NULLS` impostazione.  
  
```  
-- Create table t1 and insert values.  
CREATE TABLE dbo.t1 (a INT NULL);  
INSERT INTO dbo.t1 values (NULL),(0),(1);  
GO  
  
-- Print message and perform SELECT statements.  
PRINT 'Testing default setting';  
DECLARE @varname int;   
SET @varname = NULL;  
  
SELECT a  
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to ON and test.  
PRINT 'Testing ANSI_NULLS ON';  
SET ANSI_NULLS ON;  
GO  
DECLARE @varname int;  
SET @varname = NULL  
  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- SET ANSI_NULLS to OFF and test.  
PRINT 'Testing SET ANSI_NULLS OFF';  
SET ANSI_NULLS OFF;  
GO  
DECLARE @varname int;  
SET @varname = NULL;  
SELECT a   
FROM t1   
WHERE a = @varname;  
  
SELECT a   
FROM t1   
WHERE a <> @varname;  
  
SELECT a   
FROM t1   
WHERE a IS NULL;  
GO  
  
-- Drop table t1.  
DROP TABLE dbo.t1;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [= &#40; Uguale a &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/equals-transact-sql.md)   
 [SE... ELSE &#40; Transact-SQL &#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [&#60; &#62; &#40; Non uguale a &#41; &#40; Transact-SQL &#41;](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)   
 [Istruzioni SET &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [IN &#40; Transact-SQL &#41;](../../t-sql/queries/where-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  
