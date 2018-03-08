---
title: Parse (motore di Database) | Documenti Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|data-types
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Parse
- Parse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Parse [Database Engine]
ms.assetid: b37e28b6-6e2e-470a-945b-ce5252da743a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e80c29d1a13e0b77792ec6d3533d4d80cf355b40
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="parse-database-engine"></a>Parse (Motore di database)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

L'analisi converte la rappresentazione di stringa canonica di un **hierarchyid** per un **hierarchyid** valore. L'analisi viene chiamato implicitamente quando una conversione da un tipo stringa per **hierarchyid** si verifica. Funziona in modo opposto di [ToString](../../t-sql/data-types/tostring-database-engine.md). Parse () è un metodo statico.
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Transact-SQL syntax  
hierarchyid::Parse ( input )  
-- This is functionally equivalent to the following syntax   
-- which implicitly calls Parse():  
CAST ( input AS hierarchyid )  
```  
  
```sql
-- CLR syntax  
static SqlHierarchyId Parse ( SqlString input )   
```  
  
## <a name="arguments"></a>Argomenti  
*input*  
[!INCLUDE[tsql](../../includes/tsql-md.md)]: valore del tipo di dati character convertito.
  
CLR: valore stringa valutato.
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo: hierarchyid restituito SQL Server**
  
**Tipo CLR restituito: SqlHierarchyId**
  
## <a name="remarks"></a>Osservazioni  
Se l'analisi riceve un valore che non è una rappresentazione di stringa valida di un **hierarchyid**, viene generata un'eccezione. Ad esempio, se **char** tipi di dati contengono spazi finali, viene generata un'eccezione.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-converting-transact-sql-values-without-a-table"></a>A. Conversione di valori Transact-SQL senza una tabella  
Nell'esempio di codice viene illustrato come utilizzare `ToString` per convertire un **hierarchyid** valore in una stringa e `Parse` per convertire un valore stringa in un **hierarchyid**.
  
```sql
DECLARE @StringValue AS nvarchar(4000), @hierarchyidValue AS hierarchyid  
SET @StringValue = '/1/1/3/'  
SET @hierarchyidValue = 0x5ADE  
  
SELECT hierarchyid::Parse(@StringValue) AS hierarchyidRepresentation,  
@hierarchyidValue.ToString() AS StringRepresentation ;
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
hierarchyidRepresentation    StringRepresentation
-------------------------    -----------------------
0x5ADE                       /1/1/3/
```
  
### <a name="b-clr-example"></a>B. Esempio CLR  
Frammento di codice seguente chiama il metodo Parse ():
  
```sql
string input = “/1/2/”;  
SqlHierarchyId.Parse(input);  
```  
  
## <a name="see-also"></a>Vedere anche
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
