---
title: Gestire le pianificazioni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.manageschedules.f1
ms.assetid: f56c0736-dccc-41d2-afcf-71344aff143a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: dc219f1a5ec75d98d90168811630a39438a9bbd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683635"
---
# <a name="manage-schedules"></a>Gestione pianificazioni
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In [Istanza gestita di database SQL di Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) sono attualmente supportate la maggior parte delle funzionalità di SQL Server Agent, ma non tutte. Per informazioni dettagliate, vedere [Differenze T-SQL tra Istanza gestita del database SQL di Azure e SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Visualizza e modifica le proprietà per le pianificazioni dei processi di [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="options"></a>Opzioni  
**Pianificazioni disponibili**  
Consente di visualizzare l'elenco delle pianificazioni disponibili per questo utente. Si noti che un processo e una pianificazione devono appartenere allo stesso proprietario. Nell'elenco sono pertanto incluse solo le pianificazioni appartenenti al proprietario del processo.  
  
**Nome**  
Consente di visualizzare il nome della pianificazione.  
  
**Abilitata**  
Selezionare questa opzione per abilitare la pianificazione.  
  
**Descrizione**  
Descrive le condizioni nelle quali la pianificazione esegue il processo.  
  
**Processi nella pianificazione**  
Consente di visualizzare l'elenco dei numeri di processo collegati alla pianificazione. Fare clic su un numero per visualizzare le proprietà del processo.  
  
**Nuova**  
Fare clic su questo pulsante per creare una nuova pianificazione.  
  
**Elimina**  
Fare clic su questo pulsante per eliminare la pianificazione selezionata.  
  
**Proprietà**  
Fare clic su questo pulsante per modificare le proprietà della pianificazione selezionata.  
  
## <a name="see-also"></a>Vedere anche  
[Creazione e collegamento di pianificazioni ai processi](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
  
