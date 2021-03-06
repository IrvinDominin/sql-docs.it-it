---
title: sp_adddistributiondb (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributiondb_TSQL
- sp_adddistributiondb
helpviewer_keywords:
- sp_adddistributiondb
ms.assetid: e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c2ba920af692d85cbe8df1df69169fcde01a5c78
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610119"
---
# <a name="spadddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crea un nuovo database di distribuzione e installa lo schema del server di distribuzione. Nel database di distribuzione vengono archiviate le procedure, lo schema e i metadati utilizzati nella replica. Questa stored procedure viene eseguita nel database master del server di distribuzione per la creazione del database di distribuzione e per l'installazione delle tabelle e delle stored procedure necessarie per la distribuzione della replica.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_adddistributiondb [ @database= ] 'database'   
    [ , [ @data_folder= ] 'data_folder' ]   
    [ , [ @data_file= ] 'data_file' ]   
    [ , [ @data_file_size= ] data_file_size ]   
    [ , [ @log_folder= ] 'log_folder' ]   
    [ , [ @log_file= ] 'log_file' ]   
    [ , [ @log_file_size= ] log_file_size ]   
    [ , [ @min_distretention= ] min_distretention ]   
    [ , [ @max_distretention= ] max_distretention ]   
    [ , [ @history_retention= ] history_retention ]   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @createmode= ] createmode ]  
    [ , [ @from_scripting = ] from_scripting ] 
    [ , [ @deletebatchsize_xact = ] deletebatchsize_xact ] 
    [ , [ @deletebatchsize_cmd = ] deletebatchsize_cmd ] 
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@database=**] *database'*  
 Nome del database di distribuzione da creare. *database* viene **sysname**, non prevede alcun valore predefinito. Se il database specificato esiste già e non è contrassegnato come database di distribuzione, vengono installati gli oggetti necessari per consentire la distribuzione e il database viene contrassegnato come database di distribuzione. Se il database specificato è già abilitato come database di distribuzione, viene restituito un errore.  
  
 [  **@data_folder=**] **' * * * data_folder'*  
 Nome della directory utilizzata per l'archiviazione del file di dati del database di distribuzione. *data_folder* viene **nvarchar(255**, con un valore predefinito è NULL. Se NULL, la directory dei dati per l'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene usato, ad esempio, `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`.  
  
 [  **@data_file=**] **'***data_file***'**  
 Nome del file di database. *data_file* viene **nvarchar(255**, il valore predefinito è **database**. Se il valore è NULL, la stored procedure crea il nome del nuovo file in base al nome del database.  
  
 [  **@data_file_size=**] *data_file_size*  
 Dimensioni iniziali del file di dati in megabyte (MB). *data_file_size ho*s **int**, con un valore predefinito è 5 MB.  
  
 [  **@log_folder=**] **'***log_folder***'**  
 Nome della directory utilizzata per il file di log del database. *log_folder* viene **nvarchar(255**, con un valore predefinito è NULL. Se il valore è Null, viene utilizzata la directory dei dati di tale istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (ad esempio `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`).  
  
 [  **@log_file=**] **'***file_registro***'**  
 Nome del file di log. *file_registro* viene **nvarchar(255**, con un valore predefinito è NULL. Se il valore è NULL, la stored procedure crea il nome del nuovo file in base al nome del database.  
  
 [  **@log_file_size=**] *log_file_size*  
 Dimensioni iniziali del file di log in megabyte (MB). *log_file_size* viene **int**, con un valore predefinito è 0 MB, che indica che le dimensioni del file sono il più piccolo log file dimensioni consentite dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [  **@min_distretention=**] *min_distretention*  
 Periodo di memorizzazione minimo, espresso in ore, che deve trascorrere prima dell'eliminazione delle transazioni dal database di distribuzione. *min_distretention* viene **int**, con un valore predefinito è 0 ore.  
  
 [  **@max_distretention=**] *max_distretention*  
 Periodo di memorizzazione massimo, espresso in ore, trascorso il quale le transazioni vengono eliminate. *max_distretention* viene **int**, con un valore predefinito di 72 ore. Le sottoscrizioni che non hanno ricevuto comandi replicati e che hanno superato il periodo di memorizzazione massimo per la distribuzione vengono contrassegnate come inattive e devono essere reinizializzate. Per ogni sottoscrizione disattivata viene eseguita l'istruzione RAISERROR 21011. Un valore pari **0** significa che le transazioni replicate non viene archiviate nel database di distribuzione.  
  
 [  **@history_retention=**] *history_retention*  
 Numero di ore di memorizzazione della cronologia. *history_retention* viene **int**, con un valore predefinito è 48 ore.  
  
 [  **@security_mode=**] *security_mode*  
 Modalità di sicurezza da utilizzare quando ci si connette al server di distribuzione. *security_mode* viene **int**, con un valore predefinito è 1. **0** specifica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione. **1** specifica l'autenticazione integrata di Windows.  
  
 [  **@login=**] **'***account di accesso***'**  
 Nome dell'account di accesso utilizzato per la connessione al server di distribuzione per la creazione del database di distribuzione. È obbligatorio se *security_mode* è impostata su **0**. *login* è di tipo **sysname** e il valore predefinito è NULL.  
  
 [  **@password=**] **'***password***'**  
 Password utilizzata per la connessione al server di distribuzione. È obbligatorio se *security_mode* è impostata su **0**. *la password* viene **sysname**, con un valore predefinito è NULL.  
  
 [  **@createmode=**] *createmode*  
 *createmode* viene **int**, con un valore predefinito è 1, e può essere uno dei valori seguenti.  
  
|valore|Description|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (impostazione predefinita)|CREATE DATABASE o Usa esistente del database e quindi applicare **instdist** file per creare gli oggetti di replica nel database di distribuzione.|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
 [  **@from_scripting =** ] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
 
 [  **@deletebatchsize_xact=**] *deletebatchsize_xact*  
 Specifica le dimensioni del batch da utilizzare durante la pulizia delle transazioni scadute dalle tabelle MSRepl_Transactions. *deletebatchsize_xact* viene **int**, con un valore predefinito è 5000. Questo parametro è stata introdotta in SQL Server 2017, seguita da versioni di SQL Server 2012 SP4 e SQL Server 2016 SP2.  

 [  **@deletebatchsize_cmd=**] *deletebatchsize_cmd*  
 Specifica le dimensioni del batch da utilizzare durante la pulizia dei comandi scaduti dalle tabelle MSRepl_Commands. *deletebatchsize_cmd* viene **int**, con un valore predefinito di 2000. Questo parametro è stata introdotta in SQL Server 2017, seguita da versioni di SQL Server 2012 SP4 e SQL Server 2016 SP2. 
 
  
## <a name="return-code-values"></a>Valori restituiti  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="remarks"></a>Note  
 **sp_adddistributiondb** viene utilizzata in tutti i tipi di replica. ma viene eseguita solo in un server di distribuzione.  
  
 È necessario configurare il server di distribuzione eseguendo [sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) prima di eseguire **sp_adddistributiondb**.  
  
 Eseguire **sp_adddistributor** prima dell'esecuzione **sp_adddistributiondb**.  
  
## <a name="example"></a>Esempio  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_adddistributiondb**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurare la pubblicazione e la distribuzione](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Configurare la distribuzione](../../relational-databases/replication/configure-distribution.md)  
  
  
