---
title: sp_attachsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_attachsubscription
- sp_attachsubscription_TSQL
helpviewer_keywords:
- sp_attachsubscription
ms.assetid: b9bbda36-a46a-4327-a01e-9cd632e4791b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a69822991154bc5e7b3aa9243834618210dfe733
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47769438"
---
# <a name="spattachsubscription-transact-sql"></a>sp_attachsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Collega un database di sottoscrizione esistente a qualsiasi Sottoscrittore. Questa stored procedure viene eseguita nel database master del nuovo Sottoscrittore.  
  
> [!IMPORTANT]  
>  Questa funzionalità è deprecata e verrà rimossa a partire da una delle prossime versioni. Evitare di utilizzare questa funzionalità in un nuovo progetto di sviluppo. Nel caso di pubblicazioni di tipo merge partizionate mediante filtri con parametri, è consigliabile utilizzare la nuove funzionalità degli snapshot partizionati, che semplificano l'inizializzazione di un ampio numero di sottoscrizioni. Per altre informazioni, vedere [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md). Per le pubblicazioni non partizionate, è possibile inizializzare una sottoscrizione con un backup. Per altre informazioni, vedere [Inizializzazione di una sottoscrizione transazionale senza uno snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_attachsubscription [ @dbname = ] 'dbname'  
        , [ @filename = ] 'filename'  
    [ , [ @subscriber_security_mode = ] 'subscriber_security_mode' ]  
    [ , [ @subscriber_login = ] 'subscriber_login' ]  
    [ , [ @subscriber_password = ] 'subscriber_password' ]  
    [ , [ @distributor_security_mode = ] distributor_security_mode ]   
    [ , [ @distributor_login = ] 'distributor_login' ]   
    [ , [ @distributor_password = ] 'distributor_password' ]   
    [ , [ @publisher_security_mode = ] publisher_security_mode ]   
    [ , [ @publisher_login = ] 'publisher_login' ]   
    [ , [ @publisher_password = ] 'publisher_password' ]   
    [ , [ @job_login = ] 'job_login' ]   
    [ , [ @job_password = ] 'job_password' ]   
    [ , [ @db_master_key_password = ] 'db_master_key_password' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@dbname=** ] **'***dbname***'**  
 Stringa che specifica il database di sottoscrizione di destinazione tramite il nome. *dbname* viene **sysname**, non prevede alcun valore predefinito.  
  
 [  **@filename=** ] **'***filename***'**  
 È il nome e percorso fisico del file MDF primario (**master** file di dati). *nome file* viene **nvarchar(260)**, non prevede alcun valore predefinito.  
  
 [  **@subscriber_security_mode=** ] **'***subscriber_security_mode***'**  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un Sottoscrittore per la sincronizzazione. *subscriber_security_mode* viene **int**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  È necessario utilizzare l'autenticazione di Windows. Se *subscriber_security_mode* non è **1** (autenticazione di Windows), viene restituito un errore.  
  
 [  **@subscriber_login=** ] **'***subscriber_login***'**  
 Nome dell'account di accesso da utilizzare per la connessione a un Sottoscrittore in fase di sincronizzazione. *subscriber_login* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti. Se *subscriber_security_mode* non è **1** e *subscriber_login* è specificato, viene restituito un errore.  
  
 [  **@subscriber_password=** ] **'***subscriber_password***'**  
 Password del Sottoscrittore. *subscriber_password* viene **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Questo parametro è deprecato ed è ancora disponibile per compatibilità con gli script di versioni precedenti. Se *subscriber_security_mode* non è **1** e *subscriber_password* è specificato, viene restituito un errore.  
  
 [  **@distributor_security_mode=** ] *distributor_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un server di distribuzione per la sincronizzazione. *distributor_security_mode* viene **int**, il valore predefinito è **0**. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. **1** specifica l'autenticazione di Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@distributor_login=** ] **'***distributor_login***'**  
 Account di accesso da utilizzare quando ci si connette a un server di distribuzione per la sincronizzazione. *distributor_login* è obbligatorio se *distributor_security_mode* è impostata su **0**. *distributor_login* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@distributor_password=** ] **'***distributor_password***'**  
 Password del database di distribuzione. *distributor_password* è obbligatorio se *distributor_security_mode* è impostata su **0**. *distributor_password* viene **sysname**, con un valore predefinito è NULL. Il valore di *distributor_password* deve essere inferiore a 120 caratteri Unicode.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@publisher_security_mode=** ] *publisher_security_mode*  
 Modalità di sicurezza da utilizzare quando si effettua la connessione a un server di pubblicazione per la sincronizzazione. *publisher_security_mode* viene **int**, il valore predefinito è **1**. Se **0**, specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. Se **1**, specifica l'autenticazione di Windows. [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 [  **@publisher_login=** ] **'***publisher_login***'**  
 Account di accesso da utilizzare per la connessione a un server di pubblicazione in fase di sincronizzazione. *publisher_login* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@publisher_password=** ] **'***publisher_password***'**  
 Password utilizzata per la connessione al server di pubblicazione. *publisher_password* viene **sysname**, con un valore predefinito è NULL. Il valore di *publisher_password* deve essere inferiore a 120 caratteri Unicode.  
  
> [!IMPORTANT]  
>  Non usare una password vuota. Usare una password complessa. Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@job_login=** ] **'***job_login***'**  
 Account di accesso per l'account di Windows utilizzato per l'esecuzione dell'agente. *job_login* viene **nvarchar(257)**, non prevede alcun valore predefinito. Questo account di Windows viene sempre utilizzato per le connessioni dell'agente al server di distribuzione.  
  
 [  **@job_password=** ] **'***job_password***'**  
 Password dell'account di Windows utilizzato per l'esecuzione dell'agente. *job_password* viene **sysname**, non prevede alcun valore predefinito. Il valore di *job_password* deve essere inferiore a 120 caratteri Unicode.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
 [  **@db_master_key_password=** ] **'***db_master_key_password***'**  
 Password di una chiave master di database definita dall'utente. *db_master_key_password* viene **nvarchar(524**, con un valore predefinito NULL. Se *db_master_key_password* non viene specificato, verrà eliminata e ricreata una chiave Master del Database esistente.  
  
> [!IMPORTANT]  
>  Se possibile, richiedere agli utenti di immettere le credenziali di sicurezza in fase di esecuzione. Se è necessario archiviare le credenziali in un file script, è fondamentale proteggere il file per evitare accessi non autorizzati.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_attachsubscription** viene utilizzata nella replica snapshot, la replica transazionale e di tipo merge.  
  
 Non è possibile collegare una sottoscrizione alla pubblicazione se il periodo di memorizzazione della pubblicazione è scaduto. Se si specifica una sottoscrizione quando il periodo di memorizzazione è scaduto, viene generato un errore durante il collegamento o la prima sincronizzazione della sottoscrizione. Le pubblicazioni con un periodo di memorizzazione pari **0** (scadenza) vengono ignorati.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_attachsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
