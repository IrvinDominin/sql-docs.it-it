---
title: sp_helpdistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a909154d1d8f8c5d4a260199b3738d7526338350
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601245"
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le proprietà dei server di pubblicazione utilizzando un server di distribuzione. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@publisher=** ] **'***publisher***'**  
 Server di pubblicazione per il quale vengono restituite le proprietà. *server di pubblicazione* viene **sysname**, il valore predefinito è **%**.  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nome del server di pubblicazione.|  
|**distribution_db**|**sysname**|Database di distribuzione per il server di pubblicazione specificato.|  
|**security_mode**|**int**|Modalità di sicurezza utilizzata dagli agenti di replica per connettersi al server di pubblicazione per le sottoscrizioni ad aggiornamento in coda o a un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autenticazione<br /><br /> **1** = autenticazione di Windows|  
|**login**|**sysname**|Nome account di accesso utilizzato dagli agenti di replica per connettersi al server di pubblicazione per le sottoscrizioni ad aggiornamento in coda o a un server di pubblicazione non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524**|Password restituita in formato crittografato semplice. La password è diverso da NULL per gli utenti **sysadmin**.|  
|**Attiva**|**bit**|Indica se un server di pubblicazione remoto utilizza il server locale come server di distribuzione:<br /><br /> **0** = No<br /><br /> **1** = Sì|  
|**working_directory**|**nvarchar(255)**|Nome della directory di lavoro.|  
|**attendibile**|**bit**|Indica se la password è obbligatoria per la connessione del server di pubblicazione al server di distribuzione. Per la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive, deve sempre restituire **0**, il che significa che la password è obbligatoria.|  
|**thirdparty_flag**|**bit**|Indica se la pubblicazione è abilitata da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o da un'applicazione di terze parti:<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oracle o server di pubblicazione Oracle Gateway.<br /><br /> **1** = server di pubblicazione è stato integrato con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] usando un'applicazione di terze parti.|  
|**publisher_type**|**sysname**|Tipo di server di pubblicazione. Può essere uno dei tipi seguenti:<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Nome dell'origine dati OLE DB nel server di pubblicazione.|  
|**storage_connection_string**|**nvarchar(4000)**|Chiave di accesso di archiviazione per la directory di lavoro quando server di distribuzione o server di pubblicazione nel Database SQL di Azure.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_helpdistpublisher** viene utilizzata in tutti i tipi di replica.  
  
 **sp_helpdistpublisher** non verranno visualizzati l'account di accesso del server di pubblicazione o per impostare una password nel risultato diverso da**sysadmin** gli account di accesso.  
  
## <a name="permissions"></a>Permissions  
 I membri del **sysadmin** ruolo predefinito del server possono essere eseguiti **sp_helpdistpublisher** per qualsiasi server di pubblicazione utilizzando il server locale come server di distribuzione. I membri del **db_owner** ruolo predefinito del database o il **replmonitor** ruolo in un database di distribuzione può eseguire **sp_helpdistpublisher** per qualsiasi server di pubblicazione che utilizza quel database di distribuzione. Elencare gli utenti l'accesso alla pubblicazione per una pubblicazione specificata *server di pubblicazione* può essere eseguita **sp_helpdistpublisher**. Se *server di pubblicazione* non viene specificato, vengono restituite informazioni per tutti gli autori che l'utente disponga dei diritti di accesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  
