---
title: Connetti al server (Oracle), Account di accesso| Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f3f1b07feed76a99c1d878cc9c93a6cc65603fe4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37248464"
---
# <a name="connect-to-server-oracle-login"></a>Connetti al server (Oracle), Account di accesso
  Utilizzare la scheda **Account di accesso** della finestra di dialogo **Connetti al server** per specificare l'account con cui vengono stabilite le connessioni dal server di distribuzione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al server di pubblicazione Oracle. È necessario utilizzare lo stesso account specificato per lo schema utente di amministrazione della replica durante la configurazione del server di pubblicazione. Per altre informazioni, vedere [Configurare un server di pubblicazione Oracle](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Opzioni  
 **Istanza del server**  
 Transparent Network Substrate del server di pubblicazione Oracle specificato durante la configurazione del software client Oracle installato nel server di distribuzione.  
  
 **Autenticazione**  
 Consente di selezionare l' **Autenticazione standard Oracle** (scelta consigliata) oppure l' **Autenticazione di Windows**. Se si seleziona l' **Autenticazione di Windows**:  
  
-   Il server Oracle deve essere configurato in modo da consentire le connessioni con le credenziali di Windows. Per ulteriori informazioni, vedere la documentazione di Oracle.  
  
-   È necessario eseguire l'accesso con lo stesso account di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows specificato per lo schema utente di amministrazione della replica.  
  
 **Account di accesso** e **Password**  
 Se è stata selezionata l' **Autenticazione standard Oracle** per l'opzione **Autenticazione** , specificare l'account di accesso e la password da utilizzare, che devono corrispondere all'account di accesso e alla password specificati per lo schema utente di amministrazione della replica.  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario dei termini per la pubblicazione Oracle](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
