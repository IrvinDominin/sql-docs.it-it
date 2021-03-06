---
title: GetReparentedValue (Motore di database) | Microsoft Docs
ms.custom: ''
ms.date: 7/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reparent_TSQL
- Reparent
dev_langs:
- TSQL
helpviewer_keywords:
- Reparent [Database Engine]
ms.assetid: f47f8e25-08ef-498b-84f4-a317aca1f358
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f1c1f7c877b1f0897e8bcdb3e69162dc0355756a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762319"
---
# <a name="getreparentedvalue-database-engine"></a>GetReparentedValue (Motore di database)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un nodo il cui percorso dalla radice è il percorso *newRoot*, seguito dal percorso da *oldRoot* a *this*.
  
## <a name="syntax"></a>Sintassi  
  
```sql
-- Transact-SQL syntax  
node. GetReparentedValue ( oldRoot, newRoot )  
```  
  
```sql
-- CLR syntax  
SqlHierarchyId GetReparentedValue ( SqlHierarchyId oldRoot , SqlHierarchyId newRoot )  
```  
  
## <a name="arguments"></a>Argomenti  
*oldRoot*  
Valore **hierarchyid** del nodo che rappresenta il livello della gerarchia da modificare.
  
*newRoot*  
Valore **hierarchyid** che rappresenta il nodo che sostituirà la sezione *oldRoot* del nodo corrente per lo spostamento del nodo.
  
## <a name="return-types"></a>Tipi restituiti  
**Tipo SQL Server restituito: hierarchyid**
  
**Tipo CLR restituito: SqlHierarchyId**
  
## <a name="remarks"></a>Remarks  
Può essere usato per modificare l'albero spostando nodi da *oldRoot* a *newRoot*. GetReparentValue può inoltre essere utilizzato per spostare un nodo di una gerarchia in un nuovo percorso della gerarchia. Il tipo di dati **hierarchyid** rappresenta la struttura gerarchica, ma non la applica. Gli utenti devono verificare che hierarchyid sia strutturato in modo appropriato per il nuovo percorso. Un indice univoco applicato al tipo di dati **hierarchyid** può impedire la presenza di voci duplicate. Per un esempio di spostamento di un sottoalbero intero, vedere [Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md).
  
## <a name="examples"></a>Esempi  
  
### <a name="a-comparing-two-node-locations"></a>A. Confronto tra due percorsi di nodi  
Nell'esempio seguente viene illustrato il valore hierarchyid corrente di un nodo. Nell'esempio viene anche illustrato il valore **hierarchyid** del nodo nel caso in cui il nodo venga spostato e diventi un discendente del nodo **@NewParent**. Per visualizzare le relazioni gerarchiche, viene utilizzato il metodo `ToString()`.
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ;  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- who is /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- who is /2/3/  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
(@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) ).ToString() AS Proposed_OrgNode_AS_Text,  
OrgNode AS Current_OrgNode,  
@SubjectEmployee. GetReparentedValue(@OldParent, @NewParent) AS Proposed_OrgNode,  
*  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode = @SubjectEmployee ;  
GO  
```  
  
### <a name="b-updating-a-node-to-a-new-location"></a>B. Aggiornamento di un nodo in un nuovo percorso  
Nell'esempio seguente viene utilizzato `GetReparentedValue()` in un'istruzione UPDATE per spostare un nodo da un percorso obsoleto in un nuovo percorso nella gerarchia:
  
```sql
DECLARE @SubjectEmployee hierarchyid , @OldParent hierarchyid, @NewParent hierarchyid  
SELECT @SubjectEmployee = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\gail0' ; -- Node /1/1/2/  
SELECT @OldParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\roberto0' ; -- Node /1/1/  
SELECT @NewParent = OrgNode FROM HumanResources.EmployeeDemo  
  WHERE LoginID = 'adventure-works\wanida0' ; -- Node /2/3/  
  
UPDATE HumanResources.EmployeeDemo  
SET OrgNode = @SubjectEmployee. GetReparentedValue(@OldParent, @NewParent)   
WHERE OrgNode = @SubjectEmployee ;  
  
SELECT OrgNode.ToString() AS Current_OrgNode_AS_Text,   
*  
FROM HumanResources.EmployeeDemo  
WHERE LoginID = 'adventure-works\gail0' ; -- Now node /2/3/2/  
```  
  
### <a name="c-clr-example"></a>C. Esempio CLR  
Nel frammento di codice seguente viene chiamato il metodo GetReparentedValue ():
  
```sql
this. GetReparentedValue(oldParent, newParent)  
```  
  
## <a name="see-also"></a>Vedere anche
[Guida di riferimento ai metodi per il tipo di dati hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Dati gerarchici &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid &#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  
  
