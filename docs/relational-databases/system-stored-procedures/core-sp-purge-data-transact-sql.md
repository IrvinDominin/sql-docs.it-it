---
title: core.sp_purge_data (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 08/09/2016
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
- sp_purge_data_TSQL
- sp_purge_data
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_data
- management data warehouse, data collector stored procedures
- core.sp_purge_data stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 056076c3-8adf-4f51-8a1b-ca39696ac390
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fb74c4993f7a7d013e56061e3a572052c2939a99
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="coresppurgedata-transact-sql"></a>core.sp_purge_data (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove i dati dal data warehouse di gestione in base ai criteri di memorizzazione. Questa procedura viene eseguita ogni giorno da mdw_purge_data[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] processo dell'agente per il data warehouse di gestione associato con l'istanza specificata. È possibile utilizzare questa procedura per eseguire una rimozione su richiesta dei dati dal data warehouse di gestione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
core.sp_purge_data  
    [ [ @retention_days = ] retention_days ]  
    [ , [ @instance_name = ] 'instance_name' ]  
    [ , [ @collection_set_uid = ] 'collection_set_uid' ]  
    [ , [ @duration = ] duration ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [@retention_days =] *retention_days*  
 Numero di giorni per cui conservare i dati nelle tabelle del data warehouse di gestione. I dati con un timestamp meno recente *retention_days* viene rimosso. *retention_days* è **smallint**, con un valore predefinito è NULL. Se specificato, il valore deve essere positivo. Quando è NULL, il valore nella colonna valid_through della vista core.snapshots determina le righe da rimuovere.  
  
 [@instance_name =] '*instance_name*'  
 Nome dell'istanza per l'insieme di raccolta. *instance_name* è **sysname**, con un valore predefinito è NULL.  
  
 *instance_name* deve essere il nome di istanza completo, che include il nome del computer e il nome dell'istanza nel formato *computername*\\*instancename*. Quando è NULL, viene utilizzata l'istanza predefinita nel server locale.  
  
 [@collection_set_uid = ] '*collection_set_uid*'  
 GUID per il set di raccolta. *collection_set_uid* è **uniqueidentifier**, con un valore predefinito è NULL. Quando è NULL, vengono rimosse le righe risultanti da tutti i set di raccolta. Per ottenere questo valore, eseguire una query sulla vista del catalogo syscollector_collection_sets.  
  
 [@duration =] *durata*  
 Numero massimo di minuti per l'esecuzione dell'operazione di eliminazione. *durata* è **smallint**, con un valore predefinito è NULL. Se specificato, il valore deve essere zero o un numero intero positivo. Quando è NULL, l'operazione viene eseguita finché non vengono rimosse tutte le righe restituite o l'operazione non viene arrestata manualmente.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Questa procedura seleziona le righe della vista core.snapshots risultanti per la rimozione in base a un periodo di memorizzazione. Tutte le righe risultanti per la rimozione vengono eliminate dalla tabella core.snapshots_internal. L'eliminazione delle righe precedenti genera un'azione di eliminazione a catena in tutte le tabelle del data warehouse di gestione. Questa operazione viene eseguita utilizzando la clausola ON DELETE CASCADE definita per tutte le tabelle in cui vengono archiviati i dati raccolti.  
  
 Ogni snapshot e i dati associati vengono eliminati all'interno di una transazione esplicita, dopodiché viene eseguito il commit. Pertanto, se l'operazione di eliminazione viene arrestata manualmente oppure il valore specificato per @duration viene superato, rimangono solo i dati non salvate. Questi dati possono essere rimossi alla successiva esecuzione del processo.  
  
 La procedura deve essere eseguita nel contesto del database del data warehouse di gestione.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza di **mdw_admin** (con autorizzazione EXECUTE) ruolo predefinito del database.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-running-sppurgedata-with-no-parameters"></a>A. Esecuzione di sp_purge_data senza parametri  
 Nell'esempio seguente viene eseguito core.sp_purge_data senza specificare alcun parametro. Il valore predefinito NULL viene pertanto utilizzato per tutti i parametri, con il comportamento associato.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data;  
GO  
```  
  
### <a name="b-specifying-retention-and-duration-values"></a>B. Specifica dei valori di memorizzazione e durata  
 Nell'esempio seguente vengono rimossi dal data warehouse di gestione i dati più vecchi di 7 giorni. Inoltre, il @duration viene specificato in modo che l'esecuzione dell'operazione non duri più di 5 minuti.  
  
```  
USE <management_data_warehouse>;  
EXECUTE core.sp_purge_data @retention_days = 7, @duration = 5;  
GO  
```  
  
### <a name="c-specifying-an-instance-name-and-collection-set"></a>C. Specifica del nome di un'istanza e di un set di raccolta  
 Nell'esempio seguente vengono rimossi i dati dal data warehouse di gestione per un set di raccolta specifico nell'istanza specificata di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Poiché @retention_days non è specificato, il valore nella colonna valid_through della vista viene utilizzato per determinare le righe idonee per la rimozione del set di raccolta.  
  
```  
USE <management_data_warehouse>;  
GO  
-- Get the collection set unique identifier for the Disk Usage system collection set.  
DECLARE @disk_usage_collection_set_uid uniqueidentifier = (SELECT collection_set_uid   
    FROM msdb.dbo.syscollector_collection_sets WHERE name = N'Disk Usage');   
  
EXECUTE core.sp_purge_data @instance_name = @@SERVERNAME, @collection_set_uid = @disk_usage_collection_set_uid;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
