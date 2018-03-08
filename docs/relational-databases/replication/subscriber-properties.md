---
title: "Proprietà Sottoscrittore | Microsoft Docs"
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
f1_keywords: sql13.rep.configdistwizard.subscribers.f1
helpviewer_keywords: Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
caps.latest.revision: "22"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ccced37e2c29aa47c2d5ce67d3adeebba6ec5c58
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/18/2018
---
# <a name="subscriber-properties"></a>Proprietà Sottoscrittore
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] La finestra di dialogo **Proprietà Sottoscrittore** contiene informazioni relative ai Sottoscrittori che eseguono versioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Connessione dell'agente al Sottoscrittore**  
 Contesto nel quale l'agente di distribuzione e l'agente di merge eseguono la connessione dal server di distribuzione al Sottoscrittore. Questa opzione riguarda solo le versioni precedenti a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Selezionare **Rappresenta l'account del processo dell'agente** per eseguire connessioni al Sottoscrittore utilizzando il contesto dell'account di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent nel server di distribuzione oppure specificare **Autenticazione di SQL Server**e quindi immettere un valore per **Nome account di accesso** e **Password**. [!INCLUDE[msCoName](../../includes/msconame-md.md)] consiglia di selezionare **Rappresenta l'account del processo dell'agente**.  
  
 Per [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] e versioni successive le informazioni sulla connessione vengono specificate per ogni sottoscrizione nella Creazione guidata nuova sottoscrizione e possono essere modificate nella finestra di dialogo **Proprietà sottoscrizione** .  
  
 **Pianificazioni agenti predefinite**  
 Pianificazione predefinita utilizzata nella Creazione guidata nuova sottoscrizione per i Sottoscrittori che eseguono versioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
 **Varie**  
 Include informazioni sul Sottoscrittore e sul tipo di Sottoscrittore.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare e modificare le proprietà del server di pubblicazione e del database di distribuzione](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Riferimento alle proprietà &#40;replica&#41;](../../relational-databases/replication/properties-reference-replication.md)   
 [Sottoscrizione delle pubblicazioni](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
