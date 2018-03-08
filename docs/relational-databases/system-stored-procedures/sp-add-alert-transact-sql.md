---
title: sp_add_alert (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e66b0fd7fffb92a9646e99f84576651e4dd8b70e
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spaddalert-transact-sql"></a>sp_add_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un avviso.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_alert [ @name = ] 'name'   
     [ , [ @message_id = ] message_id ]   
     [ , [ @severity = ] severity ]   
     [ , [ @enabled = ] enabled ]  
     [ , [ @delay_between_responses = ] delay_between_responses ]   
     [ , [ @notification_message = ] 'notification_message' ]   
     [ , [ @include_event_description_in = ] include_event_description_in ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @event_description_keyword = ] 'event_description_keyword_pattern' ]   
     [ , { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ]   
     [ , [ @raise_snmp_trap = ] raise_snmp_trap ]   
     [ , [ @performance_condition = ] 'performance_condition' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@name =** ] **'***nome***'**  
 Nome dell'avviso. Tale nome viene visualizzato nel messaggio di posta elettronica o di cercapersone inviato in risposta all'avviso. Deve essere univoco e può contenere la percentuale (**%**) caratteri. *nome* è **sysname**, non prevede alcun valore predefinito.  
  
 [ **@message_id =** ] *message_id*  
 Numero dell'errore del messaggio che definisce l'avviso (Corrisponde in genere a un numero di errore di **sysmessages** tabella.) *message_id* è **int**, il valore predefinito è **0**. Se *gravità* viene utilizzato per definire l'avviso, *message_id* deve essere **0** o NULL.  
  
> [!NOTE]  
>  Solo **sysmessages** errori scritti nel registro applicazioni di Microsoft Windows possono causare un avviso da inviare.  
  
 [ **@severity =** ] *severity*  
 Il livello di gravità (da **1** tramite **25**) che definisce l'avviso. Qualsiasi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] messaggio archiviato nel **sysmessages** inviata nella tabella di [!INCLUDE[msCoName](../../includes/msconame-md.md)] nel registro applicazioni di Windows con indicazione della gravità provoca l'avviso da inviare. *gravità* è **int**, con un valore predefinito è 0. Se *message_id* viene utilizzato per definire l'avviso, *gravità* deve essere **0**.  
  
 [  **@enabled =** ] *abilitato*  
 Indica lo stato corrente dell'avviso. *abilitato* è **tinyint**, con un valore predefinito è 1 (abilitato). Se **0**, l'avviso non è abilitato e non viene generato.  
  
 [  **@delay_between_responses =** ] *delay_between_responses*  
 Periodo di attesa, in secondi, tra le risposte all'avviso. *delay_between_responses*è **int**, il valore predefinito è **0**, non ovvero non esiste alcun intervallo di attesa tra le risposte (ogni occorrenza dell'avviso genera una risposta). La risposta può assumere una delle due forme seguenti:  
  
-   Una o più notifiche inviate tramite posta elettronica o cercapersone.  
  
-   Un processo da eseguire.  
  
 L'impostazione di tale valore impedisce, ad esempio, l'invio di più messaggi di posta elettronica quando un avviso viene generato ripetutamente in un breve periodo di tempo.  
  
 [  **@notification_message =** ] **'***notification_message***'**  
 Messaggio aggiuntivo facoltativo inviato all'operatore come parte del messaggio di posta elettronica, **net send**, o una notifica tramite cercapersone. *notification_message* è **nvarchar (512)**, con un valore predefinito è NULL. Specifica di *notification_message* è utile per aggiungere note speciali, ad esempio procedure di correzione.  
  
 [ **@include_event_description_in =** ] *include_event_description_in*  
 Indica se la descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deve essere inclusa nel messaggio di notifica. *include_event_description_in*è **tinyint**, il valore predefinito è **5** (posta elettronica e **net send**) e può avere uno o più dei valori seguenti combinati con un **o** operatore logico.  
  
> [!IMPORTANT]  
>  Le opzioni Cercapersone e **net send** verranno rimosse da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare pertanto di utilizzarle in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui sono state implementate.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**0**|Nessuno|  
|**1**|Posta elettronica|  
|**2**|Cercapersone|  
|**4**|**net send**|  
  
 [ **@database_name =** ] **'***database***'**  
 Database in cui deve verificarsi l'errore affinché l'avviso venga generato. Se *database*non viene specificato, l'avviso viene attivato indipendentemente dalla posizione dell'errore. *database* è **sysname**. I nomi racchiusi tra parentesi quadre ([ ]) non sono ammessi. Il valore predefinito è NULL.  
  
 [ **@event_description_keyword =** ] **'***event_description_keyword_pattern***'**  
 Sequenza di caratteri della descrizione dell'errore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. È possibile utilizzare i caratteri dei criteri di ricerca dell'espressione LIKE [!INCLUDE[tsql](../../includes/tsql-md.md)]. *event_description_keyword_pattern* è **nvarchar (100)**, con un valore predefinito è NULL. Questo parametro è utile per filtrare i nomi degli oggetti (ad esempio, **% customer_table %**).  
  
 [ **@job_id =** ] *job_id*  
 Numero di identificazione del processo da eseguire in risposta all'avviso. *job_id* è **uniqueidentifier**, con un valore predefinito è NULL.  
  
 [ **@job_name =** ] **'***job_name***'**  
 Nome del processo da eseguire in risposta all'avviso. *job_name*è **sysname**, con un valore predefinito è NULL.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@raise_snmp_trap =** ] *raise_snmp_trap*  
 Non implementato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versione 7.0. *raise_snmp_trap* è **tinyint**, con un valore predefinito è 0.  
  
 [ **@performance_condition =** ] **'***performance_condition***'**  
 È un valore espresso nel formato '*itemcomparatorvalue*'. *performance_condition* è **nvarchar (512)** con un valore predefinito è NULL ed è costituito da questi elementi.  
  
|Componente del formato|Description|  
|--------------------|-----------------|  
|*Elemento*|Oggetto prestazioni, contatore delle prestazioni o istanza denominata del contatore|  
|*Criterio di confronto*|Uno degli operatori seguenti: >, < o =|  
|*Valore*|Valore numerico del contatore|  
  
 [ **@category_name =** ] **'***category***'**  
 Nome della categoria di avvisi. *categoria* è **sysname**, con un valore predefinito è NULL.  
  
 [  **@wmi_namespace** =] **'***wmi_namespace***'**  
 Spazio dei nomi WMI in cui eseguire query per gli eventi. *wmi_namespace* è **sysname**, con un valore predefinito è NULL. Sono supportati solo gli spazi di nomi nel server locale.  
  
 [ **@wmi_query**= ] **'***wmi_query***'**  
 Query che consente di specificare l'evento WMI per l'avviso. *Wmi_query* è **nvarchar (512)**, con un valore predefinito è NULL.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 **sp_add_alert** deve essere eseguita la **msdb** database.  
  
 Di seguito sono descritti i casi in cui gli errori/messaggi generati da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e da applicazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vengono inviati al registro applicazioni di Windows in modo da poter generare avvisi:  
  
-   Livello di gravità 19 o superiore **Sys. Messages** errori  
  
-   Qualsiasi istruzione RAISERROR richiamata con la clausola WITH LOG  
  
-   Qualsiasi **Sys. Messages** errore modificato o creato tramite **sp_altermessage**  
  
-   Qualsiasi evento registrato tramite **xp_logevent**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include un semplice strumento grafico per la gestione del sistema di avvisi ed è lo strumento consigliato per la configurazione di un'infrastruttura di avvisi.  
  
 Se un avviso non funziona adeguatamente, controllare se:  
  
-   Il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent è in esecuzione.  
  
-   L'evento è incluso nel registro applicazioni di Windows.  
  
-   L'avviso è attivato.  
  
-   Gli eventi generati con la stored procedure **xp_logevent** si verificano nel database master. Pertanto, **xp_logevent** genera un avviso solo se **@database_name** per l'avviso è **'master'** o NULL.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_add_alert**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiunto un avviso (Test Alert) che esegue il processo `Back up the AdventureWorks2012 Database` quando viene generato.  
  
> [!NOTE]  
>  Nell'esempio si presuppone che il messaggio 55001 e il processo `Back up the AdventureWorks2012 Database` siano già esistenti. Questo esempio viene fornito solo a scopo illustrativo.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_alert  
    @name = N'Test Alert',  
    @message_id = 55001,   
   @severity = 0,   
   @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
   @job_name = N'Back up the AdventureWorks2012 Database' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
