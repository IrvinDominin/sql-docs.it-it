---
title: sys.database_mirroring_witnesses (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring_witnesses
- sys.database_mirroring_witnesses_TSQL
- database_mirroring_witnesses
- database_mirroring_witnesses_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], catalog views
- sys.database_mirroring_witnesses catalog view
- witness [SQL Server], sys.database_mirroring_witnesses catalog view
ms.assetid: 0dd5b794-733b-4a3c-b5a4-62f9f1f0f22d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3ce23f7d9f763bf08842a1f121c881fb5fbdcee0
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="database-mirroring-witness-catalog-views---sysdatabasemirroringwitnesses"></a>Viste del catalogo controllo del mirroring, Mirroring del database database_mirroring_witnesses
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni ruolo del server di controllo del mirroring che un server riveste in una relazione di mirroring del database. 
  
  In una sessione di mirroring del database, il failover automatico richiede un server di controllo del mirroring. In una situazione ideale, il server di controllo del mirroring risiede su un computer distinto dal server principale e dal server mirror. Il server di controllo non esegue verifiche nel database, ma monitora lo stato del server principale e del server mirror. In caso di errore del server principale, il server di controllo del mirroring può iniziare il failover automatico sul server mirror. 
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**sysname**|Nome delle due copie del database nella sessione di mirroring del database.|  
|**principal_server_name**|**sysname**|Nome del server partner la cui copia del database è attualmente il database principale.|  
|**mirror_server_name**|**sysname**|Nome del server partner la cui copia del database è attualmente il database mirror.|  
|**safety_level**|**tinyint**|Impostazione relativa alla protezione delle transazioni per gli aggiornamenti nel database mirror:<br /><br /> 0 = Stato sconosciuto<br /><br /> 1 = protezione disattivata (asincrona)<br /><br /> 2 = protezione completa (sincrona)<br /><br /> L'utilizzo di un server di controllo del mirroring per il failover automatico richiede la protezione completa delle transazioni, ovvero l'impostazione predefinita.|  
|**safety_level_desc**|**nvarchar(60)**|Descrizione della garanzia di protezione degli aggiornamenti nel database mirror:<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL|  
|**safety_sequence_number**|**int**|Aggiornare il numero di sequenza per modifiche **safety_level**.|  
|**role_sequence_number**|**int**|Numero di sequenza di aggiornamento per le modifiche dei ruoli principale/mirror rivestiti dai partner per il mirroring.|  
|**mirroring_guid**|**uniqueidentifier**|Identificatore della relazione di mirroring.|  
|**family_guid**|**uniqueidentifier**|Identificatore del gruppo di backup del database. Utilizzato per rilevare gli stati di ripristino corrispondenti.|  
|**is_suspended**|**bit**|Il mirroring del database è sospeso.|  
|**is_suspended_sequence_number**|**int**|Numero di sequenza dell'impostazione **is_suspended**.|  
|**partner_sync_state**|**tinyint**|Stato della sincronizzazione della sessione di mirroring:<br /><br /> 5 = i partner sono sincronizzati. Il failover è possibile. Per informazioni sui requisiti per il failover, vedere [cambio di ruolo durante una Database Mirroring sessione &#40; SQL Server &#41; ](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).<br /><br /> 6 = i partner non sono sincronizzati. Il failover ora non è possibile.|  
|**partner_sync_state_desc**|**nvarchar(60)**|Descrizione dello stato di sincronizzazione della sessione di mirroring:<br /><br /> SYNCHRONIZED<br /><br /> UNSYNCHRONIZED|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo del mirroring del database](../../database-engine/database-mirroring/database-mirroring-witness.md)   
 [sys.database_mirroring &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-transact-sql.md)   
 [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query nel catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
