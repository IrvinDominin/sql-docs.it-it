---
title: Server di pubblicazione Oracle | Microsoft Docs
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
f1_keywords: sql13.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: feef7ef05ecc84fd1c7354537da2a48400a22a03
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="oracle-publisher"></a>Server di pubblicazione Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] A partire da [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consente di pubblicare i dati di un database Oracle mediante la replica transazionale o snapshot. Per altre informazioni, vedere [Panoramica della pubblicazione Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 Il server di pubblicazione Oracle deve utilizzare un server di distribuzione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] remoto nel quale deve essere eseguita la procedura guidata dopo che il software di rete Oracle necessario è stato installato e testato. Per altre informazioni, vedere [Configurare un server di pubblicazione Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
> [!IMPORTANT]  
>  Se un altro amministratore ha configurato il database Oracle come database di pubblicazione, dopo aver fatto clic su **Avanti** verrà richiesto di digitare la password per l'accesso alla replica utilizzata per connettersi al database Oracle. In[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verrà quindi definito il mapping tra l'account di accesso utilizzato e la connessione del server collegato al database Oracle. Non sarà più necessario digitare la password per le connessioni successive al database Oracle.  
  
## <a name="options"></a>Opzioni  
 **Server di pubblicazione Oracle**  
 Consente di selezionare un server di pubblicazione Oracle nell'elenco. Nell'elenco sono inclusi i server di pubblicazione Oracle precedentemente configurati per l'utilizzo del server su cui viene eseguita la procedura guidata come server di distribuzione. Se l'elenco è vuoto oppure il server di pubblicazione Oracle desiderato non è presente, fare clic su **Aggiungi server di pubblicazione Oracle**.  
  
 **Aggiungi server di pubblicazione Oracle**  
 Fare clic su questo pulsante per visualizzare la finestra di dialogo **Proprietà server di distribuzione** . In questa finestra di dialogo fare clic su **Aggiungi**e quindi su **Aggiungi server di pubblicazione Oracle**. Nella finestra di dialogo **Connetti al server** specificare il nome del server Oracle, nonché l'account di accesso e la password per lo schema utente di amministrazione della replica. Per altre informazioni, vedere [Connetti al server &#40;Oracle&#41;, Account di accesso](../../relational-databases/replication/connect-to-server-oracle-login.md).  
  
> [!NOTE]  
>  Se il server su cui viene eseguita la procedura guidata non è stato ancora configurato come server di distribuzione, viene richiesto di eseguire la configurazione adesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare una pubblicazione da un database Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md)   
 [Riferimento alle proprietà &#40;replica&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
