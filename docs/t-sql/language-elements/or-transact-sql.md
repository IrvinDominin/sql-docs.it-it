---
title: OR (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OR_TSQL
- OR
dev_langs:
- TSQL
helpviewer_keywords:
- conditions [SQL Server], combining
- combining conditions
- OR operator
ms.assetid: b730a256-4a63-4880-9906-65b05cd9caf2
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 31ced5cce6049cb63f915c6f255cb2649172571d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678339"
---
# <a name="or-transact-sql"></a>OR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Combina due condizioni. Quando un'istruzione include più operatori logici, gli operatori OR vengono valutati dopo gli operatori AND. È tuttavia possibile modificare l'ordine di valutazione tramite l'utilizzo delle parentesi.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
boolean_expression OR boolean_expression  
```  
  
## <a name="arguments"></a>Argomenti  
 *boolean_expression*  
 Qualsiasi [espressione](../../t-sql/language-elements/expressions-transact-sql.md) valida che restituisce TRUE, FALSE o UNKNOWN.  
  
## <a name="result-types"></a>Tipi restituiti  
 **Boolean**  
  
## <a name="result-value"></a>Valore restituito  
 OR restituisce TRUE quando una delle due condizioni è TRUE.  
  
## <a name="remarks"></a>Remarks  
 Nella tabella seguente viene illustrato il risultato dell'operatore OR.  
  
||TRUE|FALSE|UNKNOWN|  
|------|----------|-----------|-------------|  
|**TRUE**|TRUE|TRUE|TRUE|  
|**FALSE**|TRUE|FALSE|UNKNOWN|  
|**UNKNOWN**|TRUE|UNKNOWN|UNKNOWN|  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata la vista `vEmployeeDepartmentHistory` per recuperare i nomi del personale di `Quality Assurance` con turno serale o con turno notturno. Se le parentesi vengono omesse, la query restituisce i dipendenti di `Quality Assurance` con turno serale e tutti i dipendenti con turno notturno.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, Shift   
FROM HumanResources.vEmployeeDepartmentHistory  
WHERE Department = 'Quality Assurance'  
   AND (Shift = 'Evening' OR Shift = 'Night');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 FirstName    LastName         Shift 
 ------------ ---------------- ------- 
 Andreas      Berglund         Evening 
 Sootha       Charncherngkha   Night
 ```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Esempi: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] e [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Nell'esempio seguente vengono recuperati i nomi dei dipendenti con un valore `BaseRate` inferiore a 20 o un valore `HireDate` uguale o successivo al 1 gennaio 2001.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, BaseRate, HireDate   
FROM DimEmployee  
WHERE BaseRate < 10 OR HireDate >= '2001-01-01';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [Funzioni predefinite &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [Operatori &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  


