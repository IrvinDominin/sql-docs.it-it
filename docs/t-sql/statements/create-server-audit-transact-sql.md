---
title: CREATE SERVER AUDIT (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2018
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SERVER_AUDIT_TSQL
- SERVER AUDIT
- SERVER_AUDIT_TSQL
- CREATE SERVER AUDIT
dev_langs:
- TSQL
helpviewer_keywords:
- server audit [SQL Server]
- CREATE SERVER AUDIT statement
- audits [SQL Server], creating
ms.assetid: 1c321680-562e-41f1-8eb1-e7fa5ae45cc5
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b6e637bec3ddcfd7b24bb4f4adb87011bbbe2471
ms.sourcegitcommit: e851f3cab09f8f09a9a4cc0673b513a1c4303d2d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2018
---
# <a name="create-server-audit-transact-sql"></a>CREATE SERVER AUDIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene creato un oggetto controllo del server utilizzando [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit. Per altre informazioni, vedere [SQL Server Audit &#40;Motore di database&#41;](../../relational-databases/security/auditing/sql-server-audit-database-engine.md).  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
CREATE SERVER AUDIT audit_name  
{  
    TO { [ FILE (<file_options> [ , ...n ] ) ] | APPLICATION_LOG | SECURITY_LOG }  
    [ WITH ( <audit_options> [ , ...n ] ) ]   
    [ WHERE <predicate_expression> ]  
}  
[ ; ]  
  
<file_options>::=  
{  
        FILEPATH = 'os_file_path'  
    [ , MAXSIZE = { max_size { MB | GB | TB } | UNLIMITED } ]  
    [ , { MAX_ROLLOVER_FILES = { integer | UNLIMITED } } | { MAX_FILES = integer } ]  
    [ , RESERVE_DISK_SPACE = { ON | OFF } ]   
}  
  
<audit_options>::=  
{  
    [   QUEUE_DELAY = integer ]  
    [ , ON_FAILURE = { CONTINUE | SHUTDOWN | FAIL_OPERATION } ]  
    [ , AUDIT_GUID = uniqueidentifier ]  
}  
  
<predicate_expression>::=  
{  
    [NOT ] <predicate_factor>   
    [ { AND | OR } [NOT ] { <predicate_factor> } ]   
    [,...n ]  
}  
  
<predicate_factor>::=   
    event_field_name { = | < > | ! = | > | > = | < | < = } { number | ' string ' }  
```  
  
## <a name="arguments"></a>Argomenti  
 TO { FILE | APPLICATION_LOG | SECURITY_LOG }  
 Determina la posizione della destinazione del controllo. Le opzioni possibili sono un file binario, il registro applicazioni di Windows o il registro di sicurezza di Windows. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Se non si configurano impostazioni aggiuntive in Windows, non sarà possibile scrivere nel registro di sicurezza di Windows. Per altre informazioni, vedere [Scrivere eventi di controllo di SQL Server nel registro di sicurezza](../../relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log.md).  
  
 FILEPATH ='*os_file_path*'  
 Percorso del log di controllo. Il nome del file viene generato in base al nome e al GUID del controllo.  
  
 MAXSIZE = { *max_size }*  
 Specifica le dimensioni massime consentite per il file di controllo. Il *max_size* valore deve essere un numero intero seguito da MB, GB, TB o illimitata. La dimensione minima che è possibile specificare per *max_size* è 2 MB e il valore massimo è 2.147.483.647 TB. Se si specifica UNLIMITED, le dimensioni del file possono aumentare fino a quando non si esaurisce lo spazio su disco. 0 indica UNLIMITED. Specifica un valore inferiore a 2 MB genera l'errore MSG_MAXSIZE_TOO_SMALL. Il valore predefinito è UNLIMITED.  
  
 MAX_ROLLOVER_FILES =*{ integer* | UNLIMITED }  
 Indica il numero massimo di file da mantenere nel file system oltre al file corrente. Il *MAX_ROLLOVER_FILES* valore deve essere un integer o UNLIMITED. Il valore predefinito è UNLIMITED. Questo parametro viene valutato ogni volta che il controllo viene riavviato (che può verificarsi quando l'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] riavvio o quando il controllo viene disabilitato e quindi nuovamente) o quando è necessario un nuovo file è stato raggiunto il valore di MAXSIZE. Quando *MAX_ROLLOVER_FILES* viene valutato, se il numero di file supera il *MAX_ROLLOVER_FILES* impostazione, il file meno recente viene eliminato. Di conseguenza, quando l'impostazione di *MAX_ROLLOVER_FILES* è 0, viene creato ogni volta che un nuovo file di *MAX_ROLLOVER_FILES* impostazione viene valutata. Un solo file viene automaticamente eliminato quando *MAX_ROLLOVER_FILES* impostazione viene valutata, quando il valore di *MAX_ROLLOVER_FILES* è ridotto, il numero di file non viene ridotto a meno che non sono file obsoleti eliminati manualmente. Il numero massimo di file specificabili è 2.147.483.647.  
  
 MAX_FILES =*integer*  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Viene specificato il numero massimo di file di controllo che possono essere creati. Quando si raggiunge il limite, non viene eseguito il rollover del primo file. Quando viene raggiunto il limite MAX_FILES, qualsiasi azione che causa la generazione, di eventi di controllo genera un errore.  
  
 RESERVE_DISK_SPACE = { ON | OFF }  
 Questa opzione consente di preallocare il file sul disco in base al valore MAXSIZE. Viene applicata solo se MAXSIZE non è uguale a UNLIMITED. Il valore predefinito è OFF.  
  
 QUEUE_DELAY =*integer*  
 Specifica la quantità di tempo in millisecondi che può trascorrere prima che venga forzata l'esecuzione delle azioni di controllo. Il valore 0 indica un recapito sincrono. Il valore minimo di ritardo di query che è possibile impostare è 1000 (1 secondo). Tale valore è quello predefinito. Il valore massimo è 2.147.483.647 (2.147.483,647 secondi o 24 giorni, 20 ore, 31 minuti e 23,647 secondi). Specifica un numero non valido, genera l'errore MSG_INVALID_QUEUE_DELAY.  
  
 ON_FAILURE = {CONTINUARE | ARRESTO | FAIL_OPERATION}  
 Viene indicato se l'istanza tramite cui viene effettuata l'operazione di scrittura nella destinazione deve comportare l'esito negativo, la continuazione o l'arresto di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qualora la destinazione non consenta di scrivere nel log di controllo. Il valore predefinito è CONTINUE.  
  
 CONTINUE  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Le operazioni di SQL Server continuano. I record di controllo non vengono mantenuti. Il controllo continua a tentare di accedere a eventi e verrà ripreso se viene risolta la condizione di errore. Selezionare l'opzione per continuare, è possibile consentire l'attività non certificata che potrebbe violare i criteri di sicurezza. Utilizzare questa opzione quando il funzionamento del [!INCLUDE[ssDE](../../includes/ssde-md.md)] è più importante della gestione di un controllo completo.  
  
SHUTDOWN  
Forza l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'arresto, se [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non riesce a scrivere dati nella destinazione di controllo per qualsiasi motivo. L'account di accesso in esecuzione il `CREATE SERVER AUDIT` istruzione deve includere il `SHUTDOWN` autorizzazione all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il comportamento di arresto persiste anche se il `SHUTDOWN` autorizzazione viene revocata in un secondo momento dall'account di accesso in esecuzione. Se l'utente non ha questa autorizzazione, quindi l'istruzione ha esito negativo e il controllo non è essere creata. Utilizzare l'opzione quando un errore a livello di controllo potrebbe compromettere la sicurezza o l'integrità del sistema. Per ulteriori informazioni, vedere [arresto](../../t-sql/language-elements/shutdown-transact-sql.md).  
  
 FAIL_OPERATION  
 Le azioni del database non vengono completate se provocano eventi controllati. Le azioni, che non provocano eventi controllati possono continuare, ma non può verificarsi alcun evento controllato. Il controllo continua a tentare di accedere a eventi e verrà ripreso se viene risolta la condizione di errore. Utilizzare questa opzione quando la gestione di un controllo completo è più importante dell'accesso completo al [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].

 AUDIT_GUID =*uniqueidentifier*  
 Per supportare alcuni tipi di scenari, ad esempio il mirroring del database, a un controllo deve essere associato un GUID specifico corrispondente a quello presente nel database con mirroring. Dopo che il controllo è stato creato, il GUID non può essere modificato.  
  
 predicate_expression  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Viene specificata l'espressione del predicato utilizzata per determinare se un evento deve essere o meno elaborato. Le espressioni del predicato possono essere composte da un massimo di 3000 caratteri, pertanto gli argomenti di tipo stringa risultano limitati.  
  
 event_field_name  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nome del campo relativo all'evento che consente di identificare l'origine del predicato. I campi del controllo sono descritti in [Sys. fn_get_audit_file &#40; Transact-SQL &#41; ](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md). Tutti i campi possono essere filtrati tranne `file_name`, `audit_file_offset`, e `event_time`.  

> [!NOTE]  
>  Mentre il `action_id` e `class_type` campi sono di tipo **varchar** in sys. fn_get_audit_file, possono essere usati solo con i numeri in caso di un'origine di predicato per il filtro. Per ottenere l'elenco di valori da utilizzare con `class_type`, eseguire la query seguente:  
> ```sql
> SELECT spt.[name], spt.[number]
> FROM   [master].[dbo].[spt_values] spt
> WHERE  spt.[type] = N'EOD'
> ORDER BY spt.[name];
> ```


 number  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 È qualsiasi tipo numerico incluso **decimale**. Le limitazioni sono la mancanza di memoria fisica disponibile o un numero troppo grande per essere rappresentato come un numero intero a 64 bit.  
  
 ' string '  
 **Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Stringa ANSI o Unicode come richiesto dal paragone del predicato. Non viene eseguita alcuna conversione del tipo di stringa implicita per le funzioni del paragone del predicato. Il passaggio del tipo non corretto comporta un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene creato un controllo del server, il relativo stato è disabilitato.  
  
 L'istruzione CREATE SERVER AUDIT è nell'ambito di una transazione. L'esecuzione del rollback della transazione comporta il rollback anche per l'istruzione.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per creare, modificare o eliminare un controllo del server, le entità devono disporre dell'autorizzazione ALTER ANY SERVER AUDIT o CONTROL SERVER.  
  
 Quando si salvano informazioni di controllo in un file, per contribuire a impedirne l'alterazione, limitare l'accesso al percorso del file.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-creating-a-server-audit-with-a-file-target"></a>A. Creazione di un controllo del server con un file come destinazione  
 Nell'esempio seguente viene creato un controllo del server denominato `HIPPA_Audit` con un file binario come destinazione e nessuna opzione.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO FILE ( FILEPATH ='\\SQLPROD_1\Audit\' );  
```  
  
### <a name="b-creating-a-server-audit-with-a-windows-application-log-target-with-options"></a>B. Creazione di un controllo del server con il registro applicazioni di Windows come destinazione e con opzioni  
 Nell'esempio seguente viene creato un controllo del server denominato `HIPPA_Audit` con il registro applicazioni di Windows come destinazione. Nella coda viene eseguita un'operazione di scrittura al secondo e il motore di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene arrestato in caso di errore.  
  
```sql  
CREATE SERVER AUDIT HIPAA_Audit  
    TO APPLICATION_LOG  
    WITH ( QUEUE_DELAY = 1000,  ON_FAILURE = SHUTDOWN);  
```  
  
###  <a name="ExampleWhere"></a> C. Creazione di un controllo del server contenente una clausola WHERE  
 Nell'esempio seguente vengono creati un database, uno schema e due tabelle per l'esempio. La tabella denominata `DataSchema.SensitiveData` contiene dati riservati e l'accesso alla tabella deve essere registrato nel controllo. Nella tabella denominata `DataSchema.GeneralData` non sono contenuti dati riservati. La specifica del controllo del database consente di controllare l'accesso a tutti gli oggetti nello schema `DataSchema`. Il controllo del server viene creato con una clausola WHERE che consente di limitare il controllo del server solo alla tabella `SensitiveData`. Il controllo server si presuppone l'esistenza di una cartella del controllo in `C:\SQLAudit`.  
  
```sql  
CREATE DATABASE TestDB;  
GO  
USE TestDB;  
GO  
CREATE SCHEMA DataSchema;  
GO  
CREATE TABLE DataSchema.GeneralData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
CREATE TABLE DataSchema.SensitiveData (ID int PRIMARY KEY, DataField varchar(50) NOT NULL);  
GO  
-- Create the server audit in the master database  
USE master;  
GO  
CREATE SERVER AUDIT AuditDataAccess  
    TO FILE ( FILEPATH ='C:\SQLAudit\' )  
    WHERE object_name = 'SensitiveData' ;  
GO  
ALTER SERVER AUDIT AuditDataAccess WITH (STATE = ON);  
GO  
-- Create the database audit specification in the TestDB database  
USE TestDB;  
GO  
CREATE DATABASE AUDIT SPECIFICATION [FilterForSensitiveData]  
FOR SERVER AUDIT [AuditDataAccess]   
ADD (SELECT ON SCHEMA::[DataSchema] BY [public])  
WITH (STATE = ON);  
GO  
-- Trigger the audit event by selecting from tables  
SELECT ID, DataField FROM DataSchema.GeneralData;  
SELECT ID, DataField FROM DataSchema.SensitiveData;  
GO  
-- Check the audit for the filtered content  
SELECT * FROM fn_get_audit_file('C:\SQLAudit\AuditDataAccess_*.sqlaudit',default,default);  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [ALTER SERVER AUDIT  &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [DROP SERVER AUDIT  &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [CREATE SERVER AUDIT SPECIFICATION &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [DROP SERVER AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [CREATE DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [ALTER DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [DROP DATABASE AUDIT SPECIFICATION &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys.fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys.server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys.server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys.server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys.server_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specification-details-transact-sql.md)   
 [sys.database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys.database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys.dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys.dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys.dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Creazione di un controllo del server e di una specifica del controllo del server](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
