---
title: sp_kill_filestream_non_transacted_handles (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
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
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cb1054ec1ce9bab7311417e109ac0cece16c9c88
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="filestream-and-filetable---spkillfilestreamnontransactedhandles"></a>FileStream e FileTable - sp_kill_filestream_non_transacted_handles
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Consente di chiudere handle di file non transazionali per dati di tabelle FileTable.  
  
## <a name="syntax"></a>Sintassi  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] ‘table_name’, [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *table_name*  
 Nome della tabella in cui chiudere handle non transazionali.  
  
 È possibile passare *table_name* senza *handle_id* per chiudere handle non transazionali tutti aperti per la tabella FileTable.  
  
 È possibile passare NULL per il valore di *table_name* per chiudere handle non transazionali aperti tutti per tutte le tabelle Filetable nel database corrente. Il valore predefinito è NULL.  
  
 *handle_id*  
 ID facoltativo del singolo handle da chiudere. È possibile ottenere il *handle_id* dal [Sys.dm filestream_non_transacted_handles &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) vista a gestione dinamica. Ogni ID è univoco in un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Se si specifica *handle_id*, quindi è necessario fornire anche un valore per *table_name*.  
  
 È possibile passare NULL per il valore di *handle_id* per chiudere handle non transazionali tutti aperti per la tabella FileTable specificata da *table_name*. Il valore predefinito è NULL.  
  
## <a name="return-code-value"></a>Valore del codice restituito  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-set"></a>Set di risultati  
 Nessuno  
  
## <a name="general-remarks"></a>Osservazioni generali  
 Il *handle_id* richiesto da **sp_kill_filestream_non_transacted_handles** non è correlato a session_id o all'unità di lavoro che viene utilizzato in altre **kill** comandi.  
  
 Per altre informazioni, vedere [Gestire le tabelle FileTable](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Metadati  
 Per informazioni sugli handle di file non transazionali aperti, eseguire una query sulla DMV [Sys.dm filestream_non_transacted_handles &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>Sicurezza  
  
### <a name="permissions"></a>Autorizzazioni  
 È necessario disporre di **VIEW DATABASE STATE** dell'autorizzazione per gli handle di file da ottenere il **Sys.dm filestream_non_transacted_handles** vista a gestione dinamica e per eseguire **sp_kill_filestream_non_ transacted_handles**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come chiamare **sp_kill_filestream_non_transacted_handles** per chiudere l'handle di file non transazionali per dati di tabelle FileTable.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’, @handle_id = 0xFFFAAADD  
```  
  
 Nell'esempio seguente viene illustrato come utilizzare uno script per ottenere un *handle_id* e chiuderlo.  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione di tabelle FileTable](../../relational-databases/blob/manage-filetables.md)  
  
  
