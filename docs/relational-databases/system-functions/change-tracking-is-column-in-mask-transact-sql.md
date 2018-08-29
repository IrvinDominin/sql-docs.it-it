---
title: CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CHANGE_TRACKING_IS_COLUMN_IN_MASK_TSQL
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], CHANGE_TRACKING_IS_COLUMN_IN_MASK
- CHANGE_TRACKING_IS_COLUMN_IN_MASK
ms.assetid: 649b370b-da54-4915-919d-1b597a39d505
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 591ff9e598bd6224b9d13a0f1785c64fec8ce308
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43064193"
---
# <a name="changetrackingiscolumninmask-transact-sql"></a>CHANGE_TRACKING_IS_COLUMN_IN_MASK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Interpreta il valore SYS_CHANGE_COLUMNS restituito dalla funzione CHANGETABLE (CHANGES...). Consente a un'applicazione di determinare se la colonna specificata è inclusa nei valori restituiti per SYS_CHANGE_COLUMNS.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CHANGE_TRACKING_IS_COLUMN_IN_MASK ( column_id , change_columns )  
```  
  
## <a name="arguments"></a>Argomenti  
 *column_id*  
 ID della colonna sottoposta a verifica. La colonna ID può essere ottenuto usando il [COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md) (funzione).  
  
 *change_columns*  
 I dati binari dalla colonna SYS_CHANGE_COLUMNS dei [CHANGETABLE](../../relational-databases/system-functions/changetable-transact-sql.md) dei dati.  
  
## <a name="return-type"></a>Tipo restituito  
 **bit**  
  
## <a name="return-values"></a>Valori restituiti  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK restituisce i valori seguenti.  
  
|Valore restituito|Description|  
|------------------|-----------------|  
|0|La colonna specificata non è nel *change_columns* elenco.|  
|1|La colonna specificata è inclusa la *change_columns* elenco.|  
  
## <a name="remarks"></a>Note  
 CHANGE_TRACKING_IS_COLUMN_IN_MASK non esegue alcun controllo per convalidare il *column_id* valore o che il *change_columns* parametro ottenuto dalla tabella da cui il  *column_id* è stato ottenuto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene determinato se è stata aggiornata la colonna `Salary` della tabella `Employees`. Il `COLUMNPROPERTY` funzione restituisce l'ID di colonna del `Salary` colonna. La variabile locale `@change_columns` deve essere impostata sui risultati di una query utilizzando CHANGETABLE come origine dati.  
  
```sql  
SET @SalaryChanged = CHANGE_TRACKING_IS_COLUMN_IN_MASK  
    (COLUMNPROPERTY(OBJECT_ID('Employees'), 'Salary', 'ColumnId')  
    ,@change_columns);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni di rilevamento delle modifiche &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-functions-transact-sql.md)   
 [CHANGETABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/changetable-transact-sql.md)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
