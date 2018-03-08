---
title: Espressioni (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Boolean expressions
- expressions [SQL Server], about expressions
- combining expressions
- Transact-SQL expressions
- expressions [SQL Server], combining
- simple expressions [SQL Server]
- complex expressions [SQL Server]
ms.assetid: ee53c5c8-e36c-40f9-8cd1-d933791b98fa
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 49efa9c940ff4428747942c88259bdd58b96a658
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="expressions-transact-sql"></a>Espressioni (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Un'espressione è una combinazione di simboli e operatori che vengono valutati da [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in modo da restituire un singolo valore di dati. Le espressioni semplici possono essere costituite da un'unica costante, variabile, colonna o funzione scalare. È possibile utilizzare gli operatori per unire due o più espressioni semplici in modo da ottenere un'espressione complessa.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
{ constant | scalar_function | [ table_name. ] column | variable   
    | ( expression ) | ( scalar_subquery )   
    | { unary_operator } expression   
    | expression { binary_operator } expression   
    | ranking_windowed_function | aggregate_windowed_function  
}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

-- Expression in a SELECT statement  
<expression> ::=   
{  
    constant   
    | scalar_function   
    | column  
    | variable  
    | ( expression  )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE Windows_collation_name ]  
  
-- Scalar Expression in a DECLARE, SET, IF…ELSE, or WHILE statement  
<scalar_expression> ::=  
{  
    constant   
    | scalar_function   
    | variable  
    | ( expression  )  
    | (scalar_subquery )  
    | { unary_operator } expression   
    | expression { binary_operator } expression   
}  
[ COLLATE { Windows_collation_name ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
  
|Nome|Definizione|  
|----------|----------------|  
|*constant*|Simbolo che rappresenta un singolo valore di dati specifico. Per ulteriori informazioni, vedere [costanti &#40; Transact-SQL &#41; ](../../t-sql/data-types/constants-transact-sql.md).|  
|*scalar_function*|È un'unità di [!INCLUDE[tsql](../../includes/tsql-md.md)] sintassi che fornisce un servizio specifico e restituisce un singolo valore. *funzione_scalare* possono essere funzioni scalari predefinite, ad esempio le funzioni SUM, GETDATE o CAST, o funzioni scalari definite dall'utente.|  
|[ *table_name * * *.* * ]|Nome o alias di una tabella.|  
|*column*|Nome di colonna. In un'espressione è consentito soltanto il nome della colonna.|  
|*variable*|Nome di una variabile o parametro. Per altre informazioni, vedere [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).|  
|**(** *espressione***)** |Qualsiasi espressione valida, in base a quanto definito in questo argomento. Le parentesi sono operatori di raggruppamento che assicurano che tutti gli operatori dell'espressione tra parentesi siano valutati prima che l'espressione risultante venga combinata con un'altra espressione.|  
|**(** *scalar_subquery* **)**|Sottoquery che restituisce un valore. Esempio:<br /><br /> `SELECT MAX(UnitPrice)`<br /><br /> `FROM Products`|  
|{ *unary_operator* }|Gli operatori unari possono essere applicati solo a espressioni che restituiscono un tipo di dati appartenente alla categoria dei tipi di dati numerici. Operatore con un solo operando numerico:<br /><br /> + indica un numero positivo.<br /><br /> - indica un numero negativo.<br /><br /> ~ indica l'operatore di complemento a uno.|  
|{ *binary_operator* }|Operatore che consente di definire la modalità in base a cui due espressioni vengono unite per ottenere un unico risultato. *binary_operator* può essere un operatore aritmetico, l'operatore di assegnazione (=), un operatore bit per bit, un operatore di confronto, un operatore logico, l'operatore di concatenazione di stringhe (+) o un operatore unario. Per ulteriori informazioni sugli operatori, vedere [operatori &#40; Transact-SQL &#41; ](../../t-sql/language-elements/operators-transact-sql.md).|  
|*ranking_windowed_function*|Qualsiasi funzione di rango [!INCLUDE[tsql](../../includes/tsql-md.md)]. Per ulteriori informazioni, vedere [funzioni di rango &#40; Transact-SQL &#41; ](../../t-sql/functions/ranking-functions-transact-sql.md).|  
|*aggregate_windowed_function*|Qualsiasi funzione di aggregazione [!INCLUDE[tsql](../../includes/tsql-md.md)] con la clausola OVER. Per ulteriori informazioni, vedere [la clausola OVER &#40; Transact-SQL &#41; ](../../t-sql/queries/select-over-clause-transact-sql.md).|  
  
## <a name="expression-results"></a>Risultati dell'espressione  
 Per un'espressione semplice costituita da un'unica costante, variabile, funzione scalare o colonna, il tipo di dati, le regole di confronto, la precisione, la scala e il valore dell'espressione coincidono con quelli dell'elemento a cui viene fatto riferimento.  
  
 Quando due espressioni vengono unite tramite operatori di confronto o logici, viene restituito uno dei tre valori di tipo booleano seguenti: TRUE, FALSE o UNKNOWN. Per ulteriori informazioni sui tipi di dati booleano, vedere [gli operatori di confronto &#40; Transact-SQL &#41; ](../../t-sql/language-elements/comparison-operators-transact-sql.md).  
  
 Quando due espressioni vengono unite tramite operatori aritmetici, bit per bit o di stringa, il tipo di dati restituito dipende dall'operatore.  
  
 Le espressioni complesse costituite da più simboli e operatori restituiscono un unico valore. Il tipo di dati, le regole di confronto, la precisione e il valore dell'espressione risultante vengono determinati tramite l'unione di due espressioni componenti alla volta, fino a ottenere il risultato finale. La sequenza in base a cui vengono unite le espressioni è definita dall'ordine di precedenza degli operatori utilizzati nell'espressione.  
  
## <a name="remarks"></a>Osservazioni  
 È possibile combinare due espressioni mediante un operatore se entrambe utilizzano tipi di dati supportati dall'operatore e se almeno una delle condizioni seguenti è vera:  
  
-   Alle espressioni è applicato lo stesso tipo di dati.  
  
-   Il tipo di dati con precedenza minore può essere convertito in modo implicito nel tipo di dati con precedenza maggiore.  
  
 Se le espressioni non soddisfano tali condizioni, è possibile utilizzare funzioni CAST o CONVERT per convertire esplicitamente il tipo di dati con precedenza minore nel tipo di dati con precedenza maggiore oppure in un tipo di dati intermedio, che può essere quindi convertito implicitamente nel tipo di dati con precedenza maggiore.  
  
 Se non sono supportate né la conversione implicita né quella esplicita, non è possibile combinare le due espressioni.  
  
 Le regole di confronto di un'espressione che restituisce una stringa di caratteri vengono impostate in base alle regole sulla precedenza delle regole di confronto. Per ulteriori informazioni, vedere [precedenza delle regole di confronto &#40; Transact-SQL &#41; ](../../t-sql/statements/collation-precedence-transact-sql.md).  
  
 In un linguaggio di programmazione come C o [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], un'espressione restituisce sempre un singolo risultato. Le espressioni in un elenco di selezione [!INCLUDE[tsql](../../includes/tsql-md.md)] seguono una variante di questa regola, in quanto vengono valutate singolarmente per ogni riga del set di risultati. Una stessa espressione può avere un valore diverso in ogni riga del set di risultati, ma ogni riga include un solo valore per l'espressione. Nell'istruzione `SELECT` seguente, ad esempio, il riferimento a `ProductID` e il termine `1+2` nell'elenco di selezione sono entrambi espressioni:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, 1+2  
FROM Production.Product;  
GO  
```  
  
 L'espressione `1+2` restituisce `3` in ogni riga del set di risultati. Sebbene l'espressione `ProductID` generi un valore univoco in ogni riga del set di risultati, ogni riga include un solo valore per `ProductID`.  
  
## <a name="see-also"></a>Vedere anche  
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [CASE &#40;Transact-SQL&#41;](../../t-sql/language-elements/case-transact-sql.md)   
 [CAST e CONVERT &#40; Transact-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)   
 [Conversione tipo di dati &#40; motore di Database &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Precedenza tipo di dati &#40; Transact-SQL &#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)   
 [Tipi di dati &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [NULLIF &#40;Transact-SQL&#41;](../../t-sql/language-elements/nullif-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  
