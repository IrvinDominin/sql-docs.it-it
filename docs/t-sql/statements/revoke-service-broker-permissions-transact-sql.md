---
title: REVOCARE autorizzazioni per Service Broker (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
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
- routes [Service Broker], permissions
- Service Broker, permissions
- remote service bindings [Service Broker], permissions
- permissions [Service Broker]
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
- services [Service Broker], permissions
- REVOKE statement, Service Broker
ms.assetid: 70f1d938-97e2-48a4-9bc0-8be9f2f2c36d
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 897da4d05bcd9a2cfbb88ce5383ba7a71867edcc
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="revoke-service-broker-permissions-transact-sql"></a>REVOKE (autorizzazioni di Service Broker) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Revoca le autorizzazioni per un contratto, un tipo di messaggio, un'associazione al servizio remoto, una route o un servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ] ON  
    {   
       [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
        }  
    { TO | FROM } database_principal [ ,...n ]  
    [ CASCADE ]  
    [ AS revoking_principal ]  
```  
  
## <a name="arguments"></a>Argomenti  
 GRANT OPTION FOR  
 Indica che il diritto a concedere l'autorizzazione specificata ad altre entità verrà rimosso. L'autorizzazione stessa non verrà revocata.  
  
> [!IMPORTANT]  
>  Se l'autorizzazione specificata è stata concessa all'entità senza l'opzione GRANT, l'autorizzazione stessa verrà revocata.  
  
 *permission*  
 Specifica un'autorizzazione che può essere revocata per un'entità a sicurezza diretta di [!INCLUDE[ssSB](../../includes/sssb-md.md)]. Per un elenco di queste autorizzazioni, vedere la sezione Osservazioni di seguito in questo argomento.  
  
 CONTRATTO **:: * * * contract_name*  
 Specifica il contratto a cui viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 MESSAGE TYPE **::***message_type_name*  
 Specifica il tipo di messaggio a cui viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 L'associazione al servizio remoto **:: * * * remote_binding_name*  
 Specifica l'associazione al servizio remoto a cui viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 ROUTE **::***route_name*  
 Specifica la route a cui viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 SERVICE **::***message_type_name*  
 Specifica il servizio a cui viene revocata l'autorizzazione. Il qualificatore di ambito **::** è obbligatorio.  
  
 *database_principal*  
 Specifica l'entità da cui viene revocata l'autorizzazione. *database_principal* può essere uno dei seguenti:  
  
-   Utente del database  
  
-   Ruolo del database  
  
-   Ruolo applicazione  
  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
 CASCADE  
 Indica che l'autorizzazione che viene revocata anche ad altre entità a cui è stata concessa o negata da questa entità.  
  
> [!CAUTION]  
>  La revoca propagata di un'autorizzazione concessa con WITH GRANT OPTION comporterà la revoca sia delle autorizzazioni GRANT che delle autorizzazioni DENY per tale autorizzazione.  
  
 AS *revoking_principal*  
 Specifica un'entità dalla quale l'entità che esegue la query ottiene il diritto di revocare l'autorizzazione. *revoking_principal* può essere uno dei seguenti:  
  
-   Utente del database  
  
-   Ruolo del database  
  
-   Ruolo applicazione  
  
-   Utente del database di cui è stato eseguito il mapping a un account di accesso di Windows  
  
-   Utente del database di cui è stato eseguito il mapping a un gruppo di Windows  
  
-   Utente del database di cui è stato eseguito il mapping a un certificato  
  
-   Utente del database di cui è stato eseguito il mapping a una chiave asimmetrica  
  
-   Utente del database sul quale non viene eseguito il mapping ad alcuna entità server  
  
## <a name="remarks"></a>Osservazioni  
  
## <a name="service-broker-contracts"></a>Contratti di Service Broker  
 Un contratto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Autorizzazioni più specifiche e limitate che è possibile revocare per un [!INCLUDE[ssSB](../../includes/sssb-md.md)] contratto sono elencati nella tabella seguente, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del contratto di Service Broker|Autorizzazione del contratto di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Tipi di messaggio di Service Broker  
 Un tipo di messaggio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere revocate per un tipo di messaggio di [!INCLUDE[ssSB](../../includes/sssb-md.md)], con le autorizzazioni più generali in cui sono incluse in modo implicito.  
  
|Autorizzazione del tipo di messaggio di Service Broker|Autorizzazione del tipo di messaggio di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Associazioni ai servizi remoti di Service Broker  
 Un'associazione al servizio remoto di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Nella tabella seguente sono elencate le autorizzazioni più specifiche e limitate che possono essere revocate per un'associazione al servizio remoto di [!INCLUDE[ssSB](../../includes/sssb-md.md)], con le autorizzazioni più generali in cui sono incluse in modo implicito.  
  
|Autorizzazione dell'associazione al servizio remoto di Service Broker|Autorizzazione dell'associazione al servizio remoto di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Route di Service Broker  
 Una route di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Autorizzazioni più specifiche e limitate che è possibile revocare per un [!INCLUDE[ssSB](../../includes/sssb-md.md)] route sono elencati nella tabella seguente, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione della route di Service Broker|Autorizzazione della route di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Servizi di Service Broker  
 Un servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)] è un'entità a sicurezza diretta a livello di database contenuta nel database padre nella gerarchia di autorizzazioni. Autorizzazioni più specifiche e limitate che è possibile revocare per un [!INCLUDE[ssSB](../../includes/sssb-md.md)] servizio sono elencati nella tabella seguente, insieme alle autorizzazioni più generali che le includono in modo implicito.  
  
|Autorizzazione del servizio di Service Broker|Autorizzazione del servizio di Service Broker in cui è inclusa|Autorizzazione del database in cui è inclusa|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Autorizzazioni  
 È necessaria l'autorizzazione CONTROL per il contratto, il tipo di messaggio, l'associazione al servizio remoto, la route o il servizio di [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio di concessione delle autorizzazioni di Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/grant-service-broker-permissions-transact-sql.md)   
 [NEGARE autorizzazioni per Service Broker &#40; Transact-SQL &#41;](../../t-sql/statements/deny-service-broker-permissions-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Autorizzazioni &#40;motore di database&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Entità &#40;Motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
