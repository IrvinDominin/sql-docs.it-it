---
title: sys.fn_cdc_decrement_lsn (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- fn_cdc_decrement_lsn
- sys.fn_cdc_decrement_lsn_TSQL
- sys.fn_cdc_decrement_lsn
- fn_cdc_decrement_lsn_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_decrement_lsn
- sys.fn_cdc_decrement_lsn
ms.assetid: 83c182ad-4713-439b-8769-9b7408aec8b4
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4a19f14629a651bf872fba6e38ff79aa1b8a9f17
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="sysfncdcdecrementlsn-transact-sql"></a>sys.fn_cdc_decrement_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il precedente numero di sequenza del file di log (LSN) nella sequenza basata sul valore LSN specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_cdc_decrement_lsn ( lsn_value )  
```  
  
## <a name="arguments"></a>Argomenti  
 *lsn_value*  
 Valore LSN. *lsn_value* è **Binary (10)**.  
  
## <a name="return-type"></a>Tipo restituito  
 **binary(10)**  
  
## <a name="remarks"></a>Osservazioni  
 Il valore LSN restituito dalla funzione è sempre inferiore al valore specificato e non può esistere alcun valore LSN tra i due valori.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **pubblica** ruolo del database.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente è utilizzato `sys.fn_cdc_decrement_lsn` per impostare il limite LSN superiore in una query che restituisce righe dei dati delle modifiche che hanno valori LSN inferiori al valore LSN massimo.  
  
```  
Use AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10);  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_decrement_lsn(sys.fn_cdc_get_max_lsn());  
SELECT * FROM cdc.fn_cdc_get_all_changes_HumanResources_Employee( @from_lsn, @to_lsn, 'all');   
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sys.fn_cdc_increment_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-increment-lsn-transact-sql.md)   
 [sys.fn_cdc_get_min_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-min-lsn-transact-sql.md)   
 [sys.fn_cdc_get_max_lsn &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-cdc-get-max-lsn-transact-sql.md)   
 [Log delle transazioni &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)   
 [Informazioni su Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
