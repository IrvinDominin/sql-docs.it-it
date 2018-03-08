---
title: sp_revoke_proxy_from_subsystem (Transact-SQL) | Microsoft Docs
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
- sp_revoke_login_from_subsystem
- sp_revoke_login_from_subsystem_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revoke_proxy_from_subsystem
ms.assetid: b87bc8ba-3ea8-4aed-b54b-32c3d82d9d2a
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3408c3ddee13886edaaa410341379ee50d4f9cb3
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="sprevokeproxyfromsubsystem-transact-sql"></a>sp_revoke_proxy_from_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Revoca l'accesso a un sottosistema da un proxy.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_revoke_proxy_from_subsystem   
    [ @proxy_id = ] proxy_id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @subsystem_id = ] subsystem_id,  
    [ @subsystem_name = ] 'subsystem_name'  
```  
  
## <a name="arguments"></a>Argomenti  
 [ **@proxy_id** = ] *id*  
 Numero di identificazione del proxy da cui revocare l'accesso. Il *proxy_id* è **int**, con un valore predefinito è NULL. Entrambi *proxy_id* o *proxy_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@proxy_name** = ] **'***proxy_name***'**  
 Nome del proxy da cui revocare l'accesso. Il *proxy_name* è **sysname**, con un valore predefinito è NULL. Entrambi *proxy_id* o *proxy_name* devono essere specificati, ma non è possibile specificarli entrambi.  
  
 [ **@subsystem_id** = ] *id*  
 Numero di identificazione del sottosistema al quale revocare l'accesso. Il *subsystem_id* è **int**, con un valore predefinito è NULL. Entrambi *subsystem_id* o *subsystem_name* devono essere specificati, ma non è possibile specificarli entrambi. Nella tabella seguente vengono elencati i valori disponibili per ogni sottosistema.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|**2**|Script ActiveX<br /><br /> **\*\*Importante \* \***  verrà rimosso dal sottosistema di Scripting ActiveX di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agente in una versione futura di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata.|  
|**3**|Sistema operativo (CmdExec)|  
|**4**|Agente snapshot repliche|  
|**5**|Agente lettura log repliche|  
|**6**|Agente distribuzione repliche|  
|**7**|Agente merge repliche|  
|**8**|Agente di lettura coda repliche|  
|**9**|Comando di Analysis Services|  
|**10**|Query di Analysis Services|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] esecuzione del pacchetto|  
|**12**|Script di PowerShell|  
  
 [  **@subsystem_name** =] **'***subsystem_name***'**  
 Nome del sottosistema a cui revocare l'accesso. Il *subsystem_name* è **sysname**, con un valore predefinito è NULL. Entrambi *subsystem_id* o *subsystem_name* devono essere specificati, ma non è possibile specificarli entrambi. Nella tabella seguente vengono elencati i valori disponibili per ogni sottosistema.  
  
|Valore|Description|  
|-----------|-----------------|  
|ActiveScripting|Script ActiveX|  
|CmdExec|Sistema operativo (CmdExec)|  
|Snapshot|Agente snapshot repliche|  
|LogReader|Agente lettura log repliche|  
|Distribuzione|Agente distribuzione repliche|  
|Merge|Agente merge repliche|  
|QueueReader|Agente di lettura coda repliche|  
|ANALYSISQUERY|Comando di Analysis Services|  
|ANALYSISCOMMAND|Query di Analysis Services|  
|Dts|[!INCLUDE[ssIS](../../includes/ssis-md.md)] esecuzione del pacchetto|  
|PowerShell|Script di PowerShell|  
  
## <a name="remarks"></a>Osservazioni  
 La revoca dell'accesso a un sottosistema non modifica le autorizzazione per l'entità specificata nel proxy.  
  
> [!NOTE]  
>  Per determinare quali passaggi del processo fanno riferimento a un proxy, fare doppio clic sul **proxy** nodo **SQL Server Agent** in Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], quindi fare clic su **proprietà**. Nel **proprietà Account Proxy** la finestra di dialogo, seleziona il **riferimenti** pagina per visualizzare tutti i passaggi di processo che fanno riferimento a questo proxy.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_revoke_proxy_from_subsystem**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene revocato l'accesso al sottosistema [!INCLUDE[ssIS](../../includes/ssis-md.md)] per il proxy `Catalog application proxy`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_revoke_proxy_from_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_name = N'Dts';  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Agent Stored procedure &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [Implementazione della sicurezza SQL Server Agent](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_grant_proxy_to_subsystem &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-proxy-to-subsystem-transact-sql.md)  
  
  
