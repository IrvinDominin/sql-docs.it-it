---
title: Informazioni server Web | Microsoft Docs
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
f1_keywords: sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
caps.latest.revision: "19"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2bd914a68b761c1bcc3658404c3e52e9199bcdbc
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="web-server-information"></a>Informazioni server Web
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Le informazioni sul server Web sono necessarie per l'uso dell'opzione relativa alla sincronizzazione Web per la replica di tipo merge. Per informazioni sulla configurazione della sincronizzazione Web, vedere [Configurare la sincronizzazione Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="options"></a>Opzioni  
 **Indirizzo server Web**  
 Se si è specificato l'indirizzo di un server Web nella pagina **Snapshot FTP e Internet** della finestra di dialogo **Proprietà pubblicazione**, tale indirizzo viene visualizzato in questa casella di testo per impostazione predefinita. È possibile accettare l'impostazione predefinita oppure immettere l'indirizzo di un server Web completo per il server [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) che esegue la sincronizzazione della sottoscrizione.  
  
 **Indicare la modalità di connessione di ogni Sottoscrittore al server Web**  
 Consente di specificare il tipo di autenticazione utilizzato per la connessione al server Web. È consigliabile utilizzare l'autenticazione di base per le connessioni al server IIS realizzate in combinazione con SSL (Secure Sockets Layer). Se si seleziona l'autenticazione di base, immettere l'account e la password che verranno utilizzati per la connessione dal Sottoscrittore al server IIS.  
  
## <a name="see-also"></a>Vedere anche  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Visualizzare e modificare le proprietà delle sottoscrizioni pull](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [Sottoscrittori non SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [Sincronizzazione Web per la replica di tipo merge](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
