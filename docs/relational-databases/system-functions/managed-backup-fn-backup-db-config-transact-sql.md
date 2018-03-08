---
title: managed_backup.fn_backup_db_config (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
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
f1_keywords:
- smart_admin.fn_backup_db_config
- smart_admin.fn_backup_db_config_TSQL
- fn_backup_db_config
- fn_backup_db_config_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.fn_backup_db_config
- fn_backup_db_config
ms.assetid: 7c755d8a-64dd-44b2-be5e-735d30758900
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d18a24bdf8021fd27df0ec51e4937e80ae9c0516
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="managedbackupfnbackupdbconfig-transact-sql"></a>managed_backup.fn_backup_db_config (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Restituisce 0, 1 o più righe con le impostazioni di configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)]. Restituisce una riga per il database specificato o restituisce le informazioni per tutti i database configurati con il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] nell'istanza.  
  
 Utilizzare questa stored procedure per controllare o determinare le impostazioni di configurazione correnti del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per un database o tutti i database in un'istanza di SQL Server.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
managed_backup.fn_backup_db_config (‘database_name’ | ‘’ | NULL)  
```  
  
##  <a name="Arguments"></a> Argomenti  
 @db_name  
 Nome del database. Il @db_name parametro **SYSNAME**. Se una stringa vuota o un valore NULL viene passato a questo parametro, vengono restituite le informazioni su tutti i database nell'istanza di SQL Server.  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|db_name|SYSNAME|Nome del database.|  
|db_guid|UNIQUEIDENTIFIER|Identificatore che identifica in modo univoco il database.|  
|is_availability_database|BIT|Specifica se il database partecipa al gruppo di disponibilità. Il valore 1 indica che si tratta di un database di disponibilità mentre 0 che non lo è.|  
|is_dropped|BIT|Il valore 1 indica che si tratta di un database rimosso.|  
|credential_name|SYSNAME|Nome delle credenziali SQL utilizzate per l'autenticazione per l'account di archiviazione. Il valore NULL indica che non sono state impostate le credenziali SQL.|  
|retention_days|INT|Periodo di memorizzazione corrente espresso in giorni. Il valore NULL indica che il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] non è stato configurato mai per questo database.|  
|is_smart_backup_enabled|INT|Indica se il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è attualmente abilitato per questo database. Un valore 1 indica che il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è attualmente abilitato e il valore 0 indica che il [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] è disabilitato per questo database.|  
|storage_url|NVARCHAR(1024)|URL dell'account di archiviazione.|  
|Encryption_algorithm|NCHAR(20)|Restituisce l'algoritmo di crittografia corrente da utilizzare quando si crittografa il backup.|  
|Encryptor_type|NCHAR(15)|Restituisce l'impostazione del componente di crittografia: certificato o chiave asimmetrica.|  
|Encryptor_name|NCHAR(max_length_of_cert/asymm_key_name)|Nome del certificato o della chiave asimmetrica.|  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **db_backupoperator** ruolo del database con **ALTER ANY CREDENTIAL** autorizzazioni. L'utente non deve essere rifiutato **VIEW ANY DEFINITION** autorizzazioni.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per 'TestDB'.  
  
 Per ogni frammento di codice, selezionare 'tsql' nel campo dell'attributo di linguaggio.  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config('TestDB')  
```  
  
 Nell'esempio seguente viene restituita la configurazione del [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] per tutti i database nell'istanza di SQL Server in cui viene eseguito.  
  
```  
Use msdb  
GO  
SELECT * FROM managed_backup.fn_backup_db_config (NULL)  
```  
  
  
