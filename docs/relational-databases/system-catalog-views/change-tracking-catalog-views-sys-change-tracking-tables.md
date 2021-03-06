---
title: Sys. change_tracking_tables (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- change_tracking_tables_TSQL
- sys.change_tracking_tables
- change_tracking_tables
- sys.change_tracking_tables_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- change tracking [SQL Server], sys.change_tracking_tables
- sys.change_tracking_tables
ms.assetid: 97ec69b6-0d49-4d98-82f0-d3e77ba1ad2b
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 254a785e679450d59281410e72e9aa6b725ad48a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752939"
---
# <a name="change-tracking-catalog-views---syschangetrackingtables"></a>Modificare viste del catalogo di rilevamento - Sys. change_tracking_tables
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  Restituisce una riga per ogni tabella nel database corrente in cui è abilitato il rilevamento delle modifiche.  
   
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|object_id|**int**|ID di una tabella con un registro delle modifiche. La tabella può presentare un registro delle modifiche anche se il rilevamento delle modifiche è al momento disattivato.<br /><br /> L'ID della tabella è univoco all'interno del database.|  
|is_track_columns_updated_on|**bit**|Stato corrente di rilevamento delle modifiche nella tabella:<br /><br /> 0 = OFF<br /><br /> 1 = ON|  
|begin_version|**bigint**|Versione del database all'inizio del rilevamento delle modifiche per la tabella. Questa versione indica generalmente quando è stato abilitato il rilevamento delle modifiche, tuttavia se la tabella viene troncata il valore viene reimpostato.|  
|cleanup_version|**bigint**|Versione fino alla quale la pulizia potrebbe aver rimosso le informazioni sul rilevamento delle modifiche.|  
|min_valid_version|**bigint**|Minima versione valida delle informazioni sul rilevamento delle modifiche disponibili per la tabella.<br /><br /> Quando si ottengono modifiche dalla tabella associata a questa riga, il valore di last_sync_version deve essere maggiore o uguale alla versione indicata in questa colonna. Per altre informazioni, vedere [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md).|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [CHANGE_TRACKING_MIN_VALID_VERSION &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-tracking-min-valid-version-transact-sql.md)   
 [Viste del catalogo di rilevamento delle modifiche &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/6e8fd949-5560-4b34-879f-4e25aa24b183)   
 [Rilevare le modifiche ai dati &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)  
  
  
