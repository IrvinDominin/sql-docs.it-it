---
title: sys.sysconstraints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysconstraints
- sys.sysconstraints
- sysconstraints_TSQL
- sys.sysconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysconstraints compatibility view
- sysconstraints system table
ms.assetid: f2b2e2ad-ba24-48a1-913c-8ee4e0895dc4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: fce3ca4a2055d7f4eb10cfdcac7f09c7fd004282
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806879"
---
# <a name="syssysconstraints-transact-sql"></a>sys.sysconstraints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Contiene mapping di vincoli per gli oggetti ai quali appartengono i vincoli nel database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|Numero del vincolo.|  
|**id**|**int**|ID della tabella a cui appartiene il vincolo.|  
|**colid**|**smallint**|ID della colonna nella quale è definito il vincolo.<br /><br /> 0 = vincolo di tabella|  
|**spare1**|**tinyint**|Riservato|  
|**status**|**int**|Pseudomaschera di bit che indica lo stato. I possibili valori sono i seguenti:<br /><br /> 1 = vincolo PRIMARY KEY<br /><br /> 2 = vincolo UNIQUE KEY<br /><br /> 3 = vincolo FOREIGN KEY<br /><br /> 4 = vincolo CHECK<br /><br /> 5 = vincolo DEFAULT<br /><br /> 16 = vincolo a livello di colonna<br /><br /> 32 = vincolo a livello di tabella|  
|**Azioni**|**int**|Riservato|  
|**Errore**|**int**|Riservato|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
