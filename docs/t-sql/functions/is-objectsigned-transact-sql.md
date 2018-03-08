---
title: IS_OBJECTSIGNED (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_OBJECTSIGNED
- IS_OBJECTSIGNED_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IS_OBJECTSIGNED function
ms.assetid: afbc4f7f-8266-4ee6-9802-14a2dbe69ef6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e3cdcdfec27373a437af6895cbd68a1ceb609c7c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="isobjectsigned-transact-sql"></a>IS_OBJECTSIGNED (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Indica se un oggetto viene firmato da una chiave asimmetrica o da un certificato specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
IS_OBJECTSIGNED (   
'OBJECT', @object_id, @class, @thumbprint  
  )   
```  
  
## <a name="arguments"></a>Argomenti  
 **'OBJECT'**  
 Tipo di classe a protezione diretta.  
  
 *@object_id*  
 object_id dell'oggetto sottoposto a test. *@object_id*è di tipo **int**.  
  
 *@class*  
 Classe dell'oggetto.  
  
-   'certificate'  
  
-   'asymmetric key'  
  
 *@class*è **sysname**.  
  
 *@thumbprint*  
 Identificazione digitale SHA dell'oggetto. *@thumbprint*è di tipo **varbinary(32)**.  
  
## <a name="returned-types"></a>Tipi restituiti  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 IS_OBJECTSIGNED restituisce i valori seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|NULL|L'oggetto non è firmato oppure l'oggetto non è valido.|  
|0|L'oggetto viene firmato, ma la firma non è valida.|  
|1|L'oggetto viene firmato.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW DEFINITION per il certificato o la chiave asimmetrica.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-displaying-extended-properties-on-a-database"></a>A. Visualizzazione delle proprietà estese in un database  
 Nell'esempio seguente verifica se la tabella spt_fallback_db il **master** database firmato dallo schema del certificato di firma.  
  
```  
USE master;  
-- Declare a variable to hold a thumbprint and an object name  
DECLARE @thumbprint varbinary(20), @objectname sysname;  
  
-- Populate the thumbprint variable with the thumbprint of   
-- the master database schema signing certificate  
SELECT @thumbprint = thumbprint   
FROM sys.certificates   
WHERE name LIKE '%SchemaSigningCertificate%';  
  
-- Populate the object name variable with a table name in master  
SELECT @objectname = 'spt_fallback_db';  
  
-- Query to see if the table is signed by the thumbprint  
SELECT @objectname AS [object name],  
IS_OBJECTSIGNED(  
'OBJECT', OBJECT_ID(@objectname), 'certificate', @thumbprint  
) AS [Is the object signed?] ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [fn_check_object_signatures &#40; Transact-SQL &#41;](../../relational-databases/system-functions/sys-fn-check-object-signatures-transact-sql.md)  
  
  
