---
title: Proprietà avviso - Nuovo avviso (pagina Risposta) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c6a9385a4b783409f66d924f29a719897bc7bdc8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804569"
---
# <a name="alert-properties---new-alert-response-page"></a>Proprietà avviso - Nuovo avviso (pagina Risposta)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Usare questa pagina per specificare un processo che si vuole eseguire e per ottenere un elenco di operatori da notificare in risposta a un avviso di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  

## <a name="options"></a>Opzioni  
**Esegui processo**  
Abilita le opzioni **Elenco processi**, **Nuovo processo** e **Visualizza processo** .  
  
**Nuovo processo**  
Apre la finestra di dialogo **Nuovo processo** . Questo pulsante non è disponibile se l'opzione **Esegui processo** non è selezionata.  
  
**Visualizza processo**  
Consente di visualizzare o modificare il processo selezionato. Questa opzione non è disponibile se l'opzione **Esegui processo** non è selezionata.  
  
**Invia notifica a operatori**  
Consente di abilitare i controlli che consentono di aggiungere, rimuovere o modificare operatori.  
  
**Elenco operatori**  
In questo elenco sono presenti gli operatori da utilizzare per notificare che si è verificato un avviso. Per specificare un metodo di notifica, selezionare la casella di controllo **Posta elettronica**, **Cercapersone**o **Net send** visualizzate dopo il nome dell'operatore. Questa opzione non disponibile se l'opzione **Invia notifica a operatori** non è selezionata.  
  
**Posta elettronica**  
Consente di utilizzare la posta elettronica per l'invio della notifica all'operatore.  
  
**Cercapersone**  
Utilizzare l'indirizzo di posta elettronica del cercapersone per l'invio della notifica all'operatore.  
  
**Net send**  
Usare **Net Send** per l'invio della notifica all'operatore.  
  
**Nuovo operatore**  
Visualizza la finestra di dialogo **Nuovo operatore** in cui è possibile creare un nuovo operatore.  
  
**Visualizza operatore**  
Visualizza la finestra di dialogo **Proprietà** per l'operatore attualmente selezionato. È possibile visualizzare e modificare le proprietà dell'operatore nella finestra di dialogo **Proprietà operatore** .  
  
## <a name="see-also"></a>Vedere anche  
[Avvisi](../../ssms/agent/alerts.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
[Avvisi](../../ssms/agent/alerts.md)  
[Edit an Alert](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
  
