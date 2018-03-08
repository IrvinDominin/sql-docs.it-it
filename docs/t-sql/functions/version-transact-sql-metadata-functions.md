---
title: VERSION (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 95a79b33-98f2-4929-a1a5-93b522a9e152
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ba4237f9a43a525571a2d25f95acb0a31d4a5cb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="version---transact-sql-metadata-functions"></a>Versione - funzioni di metadati SQL
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

 Restituisce la versione di [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] o [!INCLUDE[ssPDW_md](../../includes/sspdw-md.md)] in esecuzione nel dispositivo.  
  
![Icona di collegamento argomento](../../database-engine/configure-windows/media/topic-link.gif "icona Collegamento argomento") [convenzioni della sintassi Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
-- Azure SQL Data Warehouse and Parallel Data Warehouse  
VERSION ( )  
```  
  
## <a name="arguments"></a>Argomenti  
  
## <a name="general-remarks"></a>Osservazioni generali  
Un nome di tabella deve essere specificato un [FROM](../../t-sql/queries/from-transact-sql.md) clausola per questa funzione restituire i risultati. Verrà restituita una riga di risultati per ogni riga nel set di risultati per la query. Utilizzare [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md) per limitare il numero di righe restituite.  
  
## <a name="examples"></a>Esempi  
L'esempio seguente restituisce il numero di versione.  
  
```  
SELECT VERSION();  
```  
  
## <a name="see-also"></a>Vedere anche 
[SESSION_ID (Transact-SQL)](../../t-sql/functions/session-id-transact-sql.md)  
[DB_NAME &#40;Transact-SQL&#41;](../../t-sql/functions/db-name-transact-sql.md)  
  
  
