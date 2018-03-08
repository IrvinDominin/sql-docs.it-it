---
title: sp_add_jobschedule (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/28/2016
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
- sp_add_jobschedule
- sp_add_jobschedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_jobschedule
ms.assetid: ffce19d9-d1d6-45b4-89fd-ad0f60822ba0
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b2da9a4bf2bc1fb7e2768922b6b5dd4d93452571
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="spaddjobschedule-transact-sql"></a>sp_add_jobschedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea una pianificazione per un processo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_jobschedule [ @job_id = ] job_id, | [ @job_name = ] 'job_name', [ @name = ] 'name'  
     [ , [ @enabled = ] enabled_flag ]  
     [ , [ @freq_type = ] frequency_type ]  
     [ , [ @freq_interval = ] frequency_interval ]  
     [ , [ @freq_subday_type = ] frequency_subday_type ]  
     [ , [ @freq_subday_interval = ] frequency_subday_interval ]  
     [ , [ @freq_relative_interval = ] frequency_relative_interval ]  
     [ , [ @freq_recurrence_factor = ] frequency_recurrence_factor ]  
     [ , [ @active_start_date = ] active_start_date ]  
     [ , [ @active_end_date = ] active_end_date ]  
     [ , [ @active_start_time = ] active_start_time ]  
     [ , [ @active_end_time = ] active_end_time ]  
     [ , [ @schedule_id = ] schedule_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@job_id=** ] *job_id*  
 Numero di identificazione del processo a cui viene aggiunta la pianificazione. *job_id* è **uniqueidentifier**, non prevede alcun valore predefinito.  
  
 [ **@job_name=** ] **'***job_name***'**  
 Nome del processo a cui viene aggiunta la pianificazione. *job_name* è **nvarchar (128)**, non prevede alcun valore predefinito.  
  
> [!NOTE]  
>  Entrambi *job_id* o *job_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [  **@name=** ] **'***nome***'**  
 Nome della pianificazione. *nome* è **nvarchar (128)**, non prevede alcun valore predefinito.  
  
 [ **@enabled=** ] *enabled_flag*  
 Indica lo stato corrente della pianificazione. *enabled_flag* è **tinyint**, il valore predefinito è **1** (abilitato). Se **0**, la pianificazione non è abilitata. Quando la pianificazione è disabilitata, il processo non viene eseguito.  
  
 [  **@freq_type=** ] *frequency_type*  
 Valore che indica la frequenza di esecuzione del processo. *frequency_type* è **int**, il valore predefinito è **0**, e può essere uno dei valori seguenti:  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**1**|Una volta|  
|**4**|Ogni giorno|  
|**8**|Settimanale|  
|**16**|Mensile|  
|**32**|Mensile, relativa a *frequency_interval.*|  
|**64**|All'avvio del servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent|  
|**128**|Quando il computer è inattivo|  
  
 [  **@freq_interval=** ] *frequency_interval*  
 Giorno di esecuzione del processo. *frequency_interval* è **int**, con un valore predefinito è 0 e dipende dal valore di *frequency_type* come indicato nella tabella seguente:  
  
|Valore|Effetto|  
|-----------|------------|  
|**1** (una volta)|*frequency_interval* è inutilizzato.|  
|**4** (giornaliera)|Ogni *frequency_interval* giorni.|  
|**8** (settimanale)|*frequency_interval* uno o più dei valori seguenti (in combinazione con un operatore logico OR):<br /><br /> 1 = domenica<br /><br /> 2 = lunedì<br /><br /> 4 = martedì<br /><br /> 8 = mercoledì<br /><br /> 16 = giovedì<br /><br /> 32 = venerdì<br /><br /> 64 = sabato|  
|**16** (mensile)|Nel *frequency_interval* giorno del mese.|  
|**32** (frequenza mensile relativa)|*frequency_interval* è uno dei seguenti:<br /><br /> 1 = domenica<br /><br /> 2 = lunedì<br /><br /> 3 = martedì<br /><br /> 4 = mercoledì<br /><br /> 5 = giovedì<br /><br /> 6 = venerdì<br /><br /> 7 = sabato<br /><br /> 8 = giorno<br /><br /> 9 = giorno feriale<br /><br /> 10 = giorno festivo|  
|**64** (quando il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avvio del servizio agente)|*frequency_interval* è inutilizzato.|  
|**128**|*frequency_interval* è inutilizzato.|  
  
 [ **@freq_subday_type=** ] *frequency_subday_type*  
 Specifica le unità per *frequency_subday_interval*. *frequency_subday_type* è **int**e non prevede alcun valore predefinito può essere uno dei valori seguenti:  
  
|Valore|Descrizione (unità)|  
|-----------|--------------------------|  
|**0x1**|All'ora specificata|  
|**0x4**|Minutes|  
|**0x8**|Ore|  
  
 [ **@freq_subday_interval=** ] *frequency_subday_interval*  
 Numero di *frequency_subday_type* periodi devono intercorrere tra ogni esecuzione del processo. *frequency_subday_interval* è **int**, con un valore predefinito è 0.  
  
 [ **@freq_relative_interval=** ] *frequency_relative_interval*  
 Definisce ulteriormente il *frequency_interval* quando *frequency_type* è impostato su **32** (frequenza mensile relativa).  
  
 *frequency_relative_interval* è **int**e non prevede alcun valore predefinito può essere uno dei valori seguenti:  
  
|Valore|Descrizione (unità)|  
|-----------|--------------------------|  
|**1**|Primo|  
|**2**|Secondo|  
|**4**|Terzo|  
|**8**|Quarto|  
|**16**|Ultimo|  
  
 *frequency_relative_interval* indica l'occorrenza dell'intervallo. Ad esempio, se *frequency_relative_interval* è impostato su **2**, *frequency_type* è impostato su **32**, e *frequency_ intervallo* è impostato su **3**, il processo pianificato verrà eseguito il secondo martedì di ogni mese.  
  
 [  **@freq_recurrence_factor=** ] *frequency_recurrence_factor*  
 Numero di settimane o mesi tra le esecuzioni pianificate del processo. *frequency_recurrence_factor* viene utilizzata solo se *frequency_type* è impostato su **8**, **16**, o **32**. *frequency_recurrence_factor* è **int**, con un valore predefinito è 0.  
  
 [ **@active_start_date=** ] *active_start_date*  
 Data in cui l'esecuzione del processo può avere inizio. *active_start_date* è **int**, non prevede alcun valore predefinito. La data è nel formato AAAAMMGG. Se *active_start_date* è impostata, la data deve essere maggiore o uguale a 19900101.  
  
 Al termine della creazione della pianificazione, esaminare la data di inizio per verificare che corrisponda alla data corretta. Per ulteriori informazioni, vedere la sezione "Pianificazione data di inizio" in [creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5).  
  
 [  **@active_end_date=** ] *active_end_date*  
 Data in cui l'esecuzione del processo può essere arrestata. *active_end_date* è **int**, non prevede alcun valore predefinito. La data è nel formato AAAAMMGG.  
  
 [ **@active_start_time=** ] *active_start_time*  
 Data compresa tra *active_start_date* e *active_end_date* per iniziare l'esecuzione del processo. *active_start_time* è **int**, non prevede alcun valore predefinito. L'ora è in formato HHMMSS a 24 ore.  
  
 [ **@active_end_time=***active_end_time*  
 Data compresa tra *active_start_date* e *active_end_date* per l'esecuzione del processo finale. *active_end_time* è **int**, non prevede alcun valore predefinito. L'ora è in formato HHMMSS a 24 ore.  
  
 [  **@schedule_id=***schedule_id***OUTPUT**  
 Numero di identificazione assegnato alla pianificazione dopo che è stata creata correttamente. *schedule_id* è una variabile di output di tipo **int**, non prevede alcun valore predefinito.  
  
 [  **@schedule_uid** =] *valore schedule_uid * * * OUTPUT**  
 Identificatore univoco della pianificazione. *valore schedule_uid* è una variabile di tipo **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 È possibile gestire le pianificazioni dei processi in modo indipendente dai processi. Per aggiungere una pianificazione a un processo, utilizzare **sp_add_schedule** per creare la pianificazione e **sp_attach_schedule** per associare la pianificazione a un processo.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, questa stored procedure può essere eseguita dai membri del ruolo predefinito del server **sysadmin** . Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79).  
 
 ## <a name="example"></a>Esempio
 Nell'esempio seguente viene assegnato a una pianificazione del processo `SaturdayReports` cui verrà eseguita ogni sabato alle 2:00 AM.
```sql  
EXEC msdb.dbo.sp_add_jobschedule 
        @job_name = N'SaturdayReports', -- Job name
        @name = N'Weekly_Sat_2AM',  -- Schedule name
        @freq_type = 8, -- Weekly
        @freq_interval = 64, -- Saturday
        @freq_recurrence_factor = 1, -- every week
        @active_start_time = 20000 -- 2:00 AM
```
  
## <a name="see-also"></a>Vedere anche  
 [Creare e collegare le pianificazioni ai processi](http://msdn.microsoft.com/library/079c2984-0052-4a37-a2b8-4ece56e6b6b5)   
 [Pianificare un processo](http://msdn.microsoft.com/library/f626390a-a3df-4970-b7a7-a0529e4a109c)   
 [Creare una pianificazione](http://msdn.microsoft.com/library/8c7ef3b3-c06d-4a27-802d-ed329dc86ef3)   
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_help_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)  
  
  
