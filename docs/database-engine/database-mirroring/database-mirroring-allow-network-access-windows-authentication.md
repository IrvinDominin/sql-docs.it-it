---
title: Concedere l'accesso alla rete a un endpoint per il mirroring del database usando l'autenticazione di Windows | Microsoft Docs
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-mirroring
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows authentication [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 28c8fec5-5feb-4c84-8d72-f2bd1ae3b40d
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 699ad47950411f90e9585b5a72fb2b1c89ff4587
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="database-mirroring---allow-network-access---windows-authentication"></a>Concedere l'accesso alla rete a un endpoint per il mirroring del database usando l'autenticazione di Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
L'utilizzo dell'autenticazione di Windows per la connessione degli endpoint del mirroring di database di due istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] richiede la configurazione manuale degli account di accesso nelle seguenti condizioni:  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione come servizi con diversi account di dominio (in domini uguali o attendibili), è necessario creare l'account di accesso di ogni account in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint.  
  
-   Se l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è in esecuzione come account del servizio di rete, l'account di accesso di ogni account del computer host (*DomainName***\\***ComputerName$*) deve essere creato in **master** in ognuna delle istanze del server remoto e a quell'account di accesso devono essere concesse le autorizzazioni CONNECT sull'endpoint. Ciò avviene in quanto un'istanza del server che è in esecuzione con l'account del servizio di rete esegue l'autenticazione utilizzando l'account di dominio del computer host.  
  
> [!NOTE]  
>  Assicurarsi che sia disponibile un endpoint per ogni istanza del server. Per altre informazioni, vedere [Creare un endpoint del mirroring del database per l'autenticazione Windows &#40;Transact-SQL&#41;](../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md).  
  
### <a name="to-configure-logins-for-windows-authentication"></a>Per configurare gli account di accesso per l'autenticazione di Windows  
  
1.  Per l'account utente di ogni istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], creare un account di accesso nelle altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilizzare un'istruzione [CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md) con la clausola FROM WINDOWS.  
  
     Per altre informazioni, vedere [Creazione di un account di accesso](../../relational-databases/security/authentication-access/create-a-login.md).  
  
2.  Per assicurarsi inoltre che l'utente di accesso sia in grado di accedere all'endpoint, utilizzare l'istruzione [GRANT](../../t-sql/statements/grant-transact-sql.md) per concedere le autorizzazioni di connessione sull'endpoint per l'account di accesso. Si noti che la concessione di autorizzazioni di accesso per l'endpoint non è necessaria se l'utente è un amministratore.  
  
     Per altre informazioni, vedere [Grant a Permission to a Principal](../../relational-databases/security/authentication-access/grant-a-permission-to-a-principal.md).  
  
## <a name="example"></a>Esempio  
 Nel seguente esempio [!INCLUDE[tsql](../../includes/tsql-md.md)] viene creato un account di accesso [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per un account utente denominato `Otheruser` che appartiene a un dominio denominato `Adomain`. Nell'esempio vengono quindi concesse all'utente autorizzazioni per la connessione a un endpoint di mirroring del database preesistente denominato `Mirroring_Endpoint`.  
  
```  
USE master;  
GO  
CREATE LOGIN [Adomain\Otheruser] FROM WINDOWS;  
GO  
GRANT CONNECT on ENDPOINT::Mirroring_Endpoint TO [Adomain\Otheruser];  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica di gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Sicurezza trasporto per il mirroring del database e i gruppi di disponibilità AlwaysOn &#40;SQL Server&#41;](../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [Endpoint del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
