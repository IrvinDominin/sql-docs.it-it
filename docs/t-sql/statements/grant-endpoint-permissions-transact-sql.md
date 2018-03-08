---
title: Autorizzazioni per Endpoint GRANT (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/17/2017
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
dev_langs:
- TSQL
helpviewer_keywords:
- endpoints [SQL Server], permissions
- granting permissions [SQL Server], endpoints
- GRANT statement, endpoints
- permissions [SQL Server], endpoints
ms.assetid: 9eda885c-fc3a-4c9d-8de6-ce07fb35a934
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 9106f72b1e7d8c137b4a2f80d332db87750309ee
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="grant-endpoint-permissions-transact-sql"></a>GRANT - autorizzazioni per endpoint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede le autorizzazioni per un endpoint.  

  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
GRANT permission  [ ,...n ] ON ENDPOINT :: endpoint_name  
        TO < server_principal >  [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>Argomenti  
 *autorizzazione*  
 Specifica un'autorizzazione che può essere concessa per un endpoint. Per un elenco delle autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 ENDPOINT **::***endpoint_name*  
 Specifica l'endpoint per cui viene concessa l'autorizzazione. Il qualificatore di ambito (**::**) è obbligatorio.  
  
 PER \<server_principal >  
 Specifica l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a cui viene concessa l'autorizzazione.  
  
 *SQL_Server_login*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 *SQL_Server_login_from_Windows_login*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] creato da un account di accesso di Windows.  
  
 *SQL_Server_login_from_certificate*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a un certificato.  
  
 *SQL_Server_login_from_AsymKey*  
 Specifica il nome di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sul quale viene eseguito il mapping a una chiave asimmetrica.  
  
 WITH GRANT OPTION  
 Indica che l'entità potrà inoltre concedere l'autorizzazione specificata ad altre entità.  
  
 AS *SQL_Server_login*  
 Specifica l'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dal quale l'entità che esegue la query ottiene il diritto di concedere l'autorizzazione.  
  
## <a name="remarks"></a>Osservazioni  
 Le autorizzazioni nell'ambito del server possono essere concesso solo quando il database corrente è **master**.  
  
 Informazioni sugli endpoint sono visibili nella [Endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md) vista del catalogo. Informazioni sulle autorizzazioni del server sono visibili nella [server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) è visibile nella vista del catalogo e le informazioni sulle entità server il [Sys. server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) vista del catalogo.  
  
 Un endpoint è un'entità a protezione diretta a livello del server. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che è possibile concedere per un endpoint, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione dell'endpoint|Autorizzazione dell'endpoint in cui è inclusa|Autorizzazione del server in cui è inclusa|  
|-------------------------|------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY ENDPOINT|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione CONTROL per l'endpoint o l'autorizzazione ALTER ANY ENDPOINT per il server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-granting-view-definition-permission-on-an-endpoint"></a>A. Concessione dell'autorizzazione VIEW DEFINITION per un endpoint  
 Nell'esempio seguente viene concessa l'autorizzazione `VIEW DEFINITION` per l'endpoint `Mirror7` all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `ZArifin`.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON ENDPOINT::Mirror7 TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>B. Concessione dell'autorizzazione TAKE OWNERSHIP con GRANT OPTION  
 Nell'esempio seguente viene concessa l'autorizzazione `TAKE OWNERSHIP` per l'endpoint `Shipping83` all'account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `PKomosinski` con `GRANT OPTION`.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON ENDPOINT::Shipping83 TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [NEGARE autorizzazioni per Endpoint &#40; Transact-SQL &#41;](../../t-sql/statements/deny-endpoint-permissions-transact-sql.md)   
 [REVOKE-autorizzazioni per Endpoint &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-endpoint-permissions-transact-sql.md)   
 [CREATE ENDPOINT &#40;Transact-SQL&#41;](../../t-sql/statements/create-endpoint-transact-sql.md)   
 [Viste del catalogo degli endpoint &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Sys. Endpoints &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
