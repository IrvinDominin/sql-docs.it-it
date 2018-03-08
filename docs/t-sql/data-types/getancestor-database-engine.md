---
title: GetAncestor (motore di Database) | Documenti Microsoft
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
- GetAncestor_TSQL
- GetAncestor
dev_langs:
- TSQL
helpviewer_keywords:
- GetAncestor [Database Engine]
ms.assetid: b96a986f-d5e4-4034-8013-de7974594ee9
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b232238dccf5c22918a8805cdc9cd876dfef5723
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="getancestor-database-engine"></a>GetAncestor (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un **hierarchyid** che rappresenta il  *n* predecessore di *questo*.
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Transact-SQL syntax  
child.GetAncestor ( n )   
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetAncestor ( int n )  
```  
  
## <a name="arguments"></a>Argomenti  
*n*  
Un **int**, che rappresenta il numero di livelli da salire nella gerarchia.
  
## <a name="return-types"></a>Tipi restituiti
**Tipo: hierarchyid restituito SQL Server**
  
**Tipo CLR restituito: SqlHierarchyId**
  
## <a name="remarks"></a>Osservazioni  
Utilizzato per testare se per ogni nodo nell'output il nodo corrente rappresenta un predecessore al livello specificato.
  
Se un numero maggiore di [Getlevel](../../t-sql/data-types/getlevel-database-engine.md) viene superato, viene restituito NULL.
  
Se viene passato un numero negativo, viene generata un'eccezione.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-finding-the-child-nodes-of-a-parent"></a>A. Ricerca dei nodi figlio di un padre  
`GetAncestor(1)` restituisce i dipendenti per cui `david0` rappresenta il predecessore immediato (padre). Nell'esempio seguente viene utilizzato `GetAncestor(1)`:
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(1) = @CurrentEmployee ;  
```  
  
### <a name="b-returning-the-grandchildren-of-a-parent"></a>B. Restituzione di nipoti di un padre  
`GetAncestor(2)` restituisce i dipendenti che si trovano in una posizione inferiore di due livelli nella gerarchia rispetto al nodo corrente. Tali nodi sono i nipoti del nodo corrente. Nell'esempio seguente viene utilizzato `GetAncestor(2)`:
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\ken0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(2) = @CurrentEmployee ;  
```  
  
### <a name="c-returning-the-current-row"></a>C. Restituzione della riga corrente  
Per restituire il nodo corrente utilizzando `GetAncestor(0)`, eseguire il codice seguente.
  
```sql
DECLARE @CurrentEmployee hierarchyid  
SELECT @CurrentEmployee = OrgNode FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\david0'  
  
SELECT OrgNode.ToString() AS Text_OrgNode, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetAncestor(0) = @CurrentEmployee ;  
```  
  
### <a name="d-returning-a-hierarchy-level-if-a-table-is-not-present"></a>D. Restituzione di un livello della gerarchia se una tabella non è presente  
`GetAncestor` restituisce il livello selezionato della gerarchia anche se una tabella non è presente. Nel codice seguente ad esempio viene determinato un dipendente corrente e viene restituito il valore `hierarchyid` del predecessore del dipendente corrente senza fare riferimento a una tabella.
  
```sql
DECLARE @CurrentEmployee hierarchyid ;  
DECLARE @TargetEmployee hierarchyid ;  
SELECT @CurrentEmployee = '/2/3/1.2/5/3/' ;  
SELECT @TargetEmployee = @CurrentEmployee.GetAncestor(2) ;  
SELECT @TargetEmployee.ToString(), @TargetEmployee ;  
```  
  
### <a name="e-calling-a-common-language-runtime-method"></a>E. Chiamata a un metodo Common Language Runtime  
Nel frammento di codice seguente viene chiamato il metodo `GetAncestor()`.
  
```sql
this.GetAncestor(1)  
```  
  
## <a name="see-also"></a>Vedere anche
[IsDescendantOf &#40; motore di Database &#41;](../../t-sql/data-types/isdescendantof-database-engine.md)  
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
