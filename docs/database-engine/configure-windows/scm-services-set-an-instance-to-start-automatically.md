---
title: Gestione configurazione SQL Server - Impostare un'istanza per l'avvio automatico | Microsoft Docs
ms.custom: ''
ms.date: 01/06/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 08986df74a5df440bf1cfb589cbe39680bce8a56
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47788839"
---
# <a name="scm-services---set-an-instance-to-start-automatically"></a>Gestione configurazione SQL Server - Impostare un'istanza per l'avvio automatico
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In questo argomento viene illustrato come impostare un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'avvio automatico in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] utilizzando Gestione configurazione SQL Server. Durante l'installazione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] viene normalmente configurato per l'avvio automatico. In caso contrario, è possibile modificare questa impostazione in qualsiasi momento.  
  
##  <a name="SSMSProcedure"></a> Utilizzo di Gestione configurazione SQL Server  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>Per impostare un'istanza di SQL Server per l'avvio automatico  
  
1.  Fare clic sul menu **Start** , scegliere **Tutti i programmi**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Strumenti di configurazione**e quindi **Gestione configurazione SQL Server**.  
  
    > [!NOTE]  
    >  Poiché Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è uno snap-in per il programma [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console e non un programma autonomo, Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non viene visualizzato come applicazione nelle nuove versioni di Windows.  
    >   
    >  -   **Windows 10**:  
    >          per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , nella **pagina iniziale**digitare SQLServerManager13.msc (per [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). Per le versioni precedenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sostituire 13 con un numero inferiore. Se si fa clic su SQLServerManager13.msc, viene aperto Gestione configurazione. Per aggiungere Gestione configurazione alla pagina iniziale o alla barra delle applicazioni, fare clic con il pulsante destro del mouse su SQLServerManager13.msc e quindi scegliere **Apri percorso file**. In Esplora file di Windows fare clic con il pulsante destro del mouse su SQLServerManager13.msc e quindi scegliere **Aggiungi a Start** o **Aggiungi alla barra delle applicazioni**.  
    > -   **Windows 8**:  
    >          Per aprire Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nell'accesso alla **ricerca** in **App** digitare **SQLServerManager\<versione>.msc**, ad esempio **SQLServerManager13.msc** e quindi premere **INVIO**.  
  
2.  In **Gestione configurazione SQL Server**espandere **Servizi**e quindi fare clic su **SQL Server**.  
  
3.  Nel riquadro dei dettagli fare clic con il pulsante destro del mouse sul nome dell'istanza per la quale impostare l'avvio automatico, quindi scegliere **Proprietà**.  
  
4.  Nella finestra di dialogo **SQL Server \<***nomeistanza***> Proprietà** impostare  **Modalità di avvio** su **Automatica**.  
  
5.  Fare clic su **OK**e chiudere Gestione configurazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Impedire l'avvio automatico di un'istanza di SQL Server &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Connettersi a un altro computer &#40;Gestione configurazione SQL Server&#41;](../../database-engine/configure-windows/scm-services-connect-to-another-computer.md)   
 [Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
