---
title: Modificare le dimensioni del log di cronologia processi | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], history
- resizing job history log
- size [SQL Server], job history log
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: ddee1ce8-9d1b-4017-9894-bf7256aed95d
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c04ed3df42c5dc14580e5343b876989144b97d1e
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="resize-the-job-history-log"></a>Modificare le dimensioni del log di cronologia processi
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Questo argomento descrive come impostare le dimensioni massime per i log di cronologia processo di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].
  
-   **Prima di iniziare:**  
  
    [Security](#Security)  
  
-   **Per impostare le dimensioni massime dei log della cronologia dei processi utilizzando:**  
  
    [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>Prima di iniziare  
  
### <a name="Security"></a>Security  
Per informazioni dettagliate, vedere [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilizzo di SQL Server Management Studio  
  
#### <a name="to-resize-the-job-history-log-based-on-raw-size"></a>Per ridimensionare il log cronologia processi in base alle dimensioni dei dati non elaborati  
  
1.  In **Esplora oggetti** connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]ed espandere tale istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella pagina **Cronologia** verificare che la casella di controllo **Limita dimensioni log cronologia processi**sia selezionata.  
  
4.  Nella casella **Dimensioni massime log cronologia processi** immettere il numero massimo di righe consentito per il log cronologia processi.  
  
5.  Nella casella **Numero massimo di righe di cronologia per processo** immettere il numero massimo di righe di cronologia consentito per un processo.  
  
#### <a name="to-resize-the-job-history-log-based-on-time"></a>Per ridimensionare il log cronologia processi in base al tempo  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)], quindi espandere questa istanza.  
  
2.  Fare clic con il pulsante destro del mouse su **SQL Server Agent**, quindi scegliere **Proprietà**.  
  
3.  Nella scheda **Cronologia** fare clic su **Rimuovi automaticamente cronologia dell'agente**.  
  
4.  Selezionare il numero appropriato di **giorno/i**, **settimana/e**o **mese/i**.  
  
