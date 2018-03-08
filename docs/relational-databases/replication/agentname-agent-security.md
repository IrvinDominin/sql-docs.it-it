---
title: Sicurezza agente &lt;NomeAgente&gt; | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 946cba7a7af21e52de146d753728aa30bbc15b16
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="ltagentnamegt-agent-security"></a>Sicurezza agente &lt;NomeAgente&gt;
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La pagina **Sicurezza agente \<NomeAgente>** consente di specificare gli account usati per l'esecuzione dall'agente di distribuzione (per la replica transazionale e snapshot) o dall'agente di merge (per la replica di tipo merge) e per la creazione di connessioni ai computer in una topologia di replica. Per informazioni sulle autorizzazioni necessarie per gli agenti e le procedure migliori per la sicurezza della replica, vedere [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md) e [Procedure consigliate per la sicurezza della replica](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## <a name="options"></a>Opzioni  
 Fare clic sul pulsante delle proprietà (**...**) nella riga di ciascun Sottoscrittore per accedere alla finestra di dialogo **Sicurezza agente di distribuzione** o **Sicurezza agente di merge** . Per ulteriori informazioni sulle autorizzazioni necessarie per gli account utilizzati dagli agenti, fare clic su **?** nella finestra di dialogo visualizzata.  
  
 Dopo l'immissione delle impostazioni in una delle finestre di dialogo, le informazioni di connessione per il Sottoscrittore vengono visualizzate nella griglia.  
  
 **Agente per Sottoscrittore**  
 Nome di ciascun Sottoscrittore.  
  
 **Connessione al server di distribuzione**  
 Visualizzato per la replica transazionale e snapshot. Contesto in cui viene creata la connessione al server di distribuzione. Le connessioni locali vengono create sempre mediante il contesto dell'account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni push, la connessione locale è quella stabilita con il server di distribuzione, pertanto in questo campo viene sempre visualizzato: **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** o **Rappresenta '\<Computer>\\<AccountDiAccesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni pull, la connessione può inoltre essere creata nel contesto di un account di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nel campo viene visualizzato uno dei valori seguenti: **Usa l'account di accesso '\<Account accesso>'**, **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** oppure **Rappresenta '\<Computer>\\<AccountDiAccesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di stabilire tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
 **Connessione al server di pubblicazione e al server di distribuzione**  
 Visualizzato per la replica di tipo merge. Contesto in cui vengono create le connessioni al server di pubblicazione e al server di distribuzione. Le connessioni locali vengono create sempre mediante il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni push, la connessione locale è quella stabilita con il server di pubblicazione e il server di distribuzione, pertanto in questo campo viene sempre visualizzato: **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** o **Rappresenta '\<Computer>\\<AccountDiAccesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni pull, la connessione può inoltre essere creata nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nel campo viene visualizzato uno dei valori seguenti: **Usa l'account di accesso '\<AccountDiAccesso>'**, **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** o **Rappresenta '\<Computer>\\<AccountDiAccesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di stabilire tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
 **Connessione al Sottoscrittore**  
 Contesto in cui viene creata la connessione al Sottoscrittore. Le connessioni locali vengono create sempre mediante il contesto dell'account di Windows utilizzato per l'esecuzione dell'agente:  
  
-   Per le sottoscrizioni pull, la connessione locale è quella stabilita con il Sottoscrittore, pertanto in questo campo viene sempre visualizzato: **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** o **Rappresenta '\<Computer>\\<AccountDiAccesso\>'** per le sottoscrizioni push.  
  
-   Per le sottoscrizioni push, la connessione può inoltre essere creata nel contesto di un account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nel campo viene visualizzato uno dei valori seguenti: **Usa l'account di accesso '\<Account accesso>'**, **Rappresenta '\<Dominio>\\<AccountDiAccesso\>'** oppure **Rappresenta '\<Computer>\\<AccountDiAccesso\>'**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di stabilire tutte le connessioni utilizzando il contesto dell'account di Windows.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni push](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [Gestire gli account di accesso e le password nella replica](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Modello di sicurezza dell'agente di replica](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [Sicurezza e protezione &#40;replica&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
