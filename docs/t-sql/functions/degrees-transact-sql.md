---
title: DEGREES (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DEGREES
- DEGREES_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DEGREES function
- number of degrees
ms.assetid: 5208de3c-90a3-4f59-a7e3-10b01bf285bb
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c046df68b15c40b692fceae9d6f1befe09a96cc2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="degrees-transact-sql"></a>DEGREES (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce l'angolo in gradi corrispondente all'angolo specificato in radianti.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
DEGREES ( numeric_expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *numeric_expression*  
 [Espressione](../../t-sql/language-elements/expressions-transact-sql.md) della categoria di tipi di dati numerici esatti o numerici approssimativi, ad eccezione del tipo di dati **bit**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 Restituisce lo stesso tipo di *numeric_expression*.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituito il numero di gradi di un angolo il cui valore in radianti è PI/2.  
  
```  
SELECT 'The number of degrees in PI/2 radians is: ' +   
CONVERT(varchar, DEGREES((PI()/2)));  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
The number of degrees in PI/2 radians is 90         
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni matematiche &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)  
  
  

