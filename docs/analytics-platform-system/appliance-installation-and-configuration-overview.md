---
title: Panoramica di configurazione (Analitica piattaforma System) e di installazione dello strumento
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10934f62-4acf-4ca5-b550-f426ba81fe11
caps.latest.revision: 23
ms.openlocfilehash: df27bb16f24e313f7cb1d7c7f5ced912c0a09e1d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="appliance-installation-and-configuration-overview"></a>Panoramica di configurazione e installazione dello strumento
Descrive gli amministratori di SQL Server PDW appliance tramite i passaggi iniziali per configurare e iniziare a usare i nuovi accessori di SQL Server PDW.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Installare i componenti Hardware  
Il nuovo strumento verrà recapitato su palette di ancoraggio in data center.  
  
> [!IMPORTANT]  
> In alcuni casi, il fornitore verrà Disimballare, rack e collegare il dispositivo per l'utente nel data center. Se in tal caso, queste istruzioni non sono necessari e a cui è possibile ignorare il [3. Configurare l'accessorio](#ConfigureAppliance) sezione riportata di seguito.  
  
Se il fornitore non viene eseguita l'installazione di hardware, è possibile utilizzare la procedura seguente per installare i componenti hardware.  
  
|||  
|-|-|  
|**Attività**|**Description**|  
|Verificare la documentazione|Verificare di aver ricevuto tutte le informazioni e i documenti necessari al fornitore di hardware indipendenti (IHV). Vedere [le informazioni di ottenere il IHV &#40;Analitica Platform System&#41;](information-to-obtain-from-your-ihv.md).|  
|Installare il componente hardware|Verificare che il data center in grado di gestire il dispositivo. Spostare i componenti del dispositivo nel data center. I commutatori di rete, PDU, rack e i cavi. Vedere [installazione Hardware &#40;Analitica Platform System&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. Accensione del dispositivo  
  
|||  
|-|-|  
|**Attività**|**Description**|  
|Accensione del dispositivo|Risparmio energia in ogni nodo del componente accessorio nell'ordine richiesto, in attesa in base alle esigenze per confermare che non si verificano errori.|  
  
## <a name="ConfigureAppliance"></a>3. Configurare il dispositivo  
  
|||  
|-|-|  
|**Attività**|**Description**|  
|||  
|Configurare l'accessorio tramite SQL Server PDW**Configuration Manager**|Utilizzare Gestione configurazione per impostare le password di dispositivo, fusi orari, le impostazioni di rete e del firewall, i certificati di sicurezza, prestazioni e altre impostazioni del dispositivo. Vedere [dello strumento configurazione &#40;Analitica Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Modifiche di configurazione devono essere apportate soltanto utilizzando SQL Server PDW**Configuration Manager**. Le modifiche non esposta tramite **Configuration Manager** non sono supportati. Ad esempio, lo strumento di SQL Server PDW supporta solo l'impostazione della lingua inglese.  
  
## <a name="SoftwareServicing"></a>4. Impostare la manutenzione del Software  
  
|||  
|-|-|  
|**Attività**|**Description**|  
|Applicare gli aggiornamenti di SQL Server PDW|(Facoltativo) Potrebbe essere necessario applicare uno o più aggiornamenti di SQL Server PDW per aggiornare il software di SQL Server PDW alla versione più recente. Vedere [applicare aggiornamenti rapidi di sistema della piattaforma Analitica &#40;Analitica Platform System&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Configurare Windows Server Update Services|Configurare l'accessorio per ricevere gli aggiornamenti da Windows Server Update Services per il supporto di software. Vedere [scaricare e applicare gli aggiornamenti di Microsoft &#40;Analitica Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Passaggi successivi  
Dopo aver completato tutti i passaggi precedenti, il dispositivo è pronto per l'utilizzo. Si o altre persone presso la sede possono procedere con le attività seguenti.  
  
|||  
|-|-|  
|**Attività**|**Description**|  
|Installare i driver di SQL Server PDW e configurare la connettività|Configurare il computer locale per connettersi a SQL Server PDW utilizzando SQL Server Data Tools, sqlcmd, software di business intelligence o altri strumenti. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Creare ruoli del server e di accessi e assegnare le autorizzazioni|Pianificare e creare ruoli di accessi e il server che consentono agli utenti di accedere a SQL Server PDW con le autorizzazioni appropriate. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Configurare il Gateway di gestione dati di Azure|Il Gateway consente agli utenti di Azure di accedere ai dati di punti di accesso locale, l'esposizione dei dati APS quanto più sicura di feed OData. Il Gateway è già installato nel nodo di controllo. Richiedere a Microsoft per assistenza con la configurazione.|  
|Query di monitoraggio e gli utenti di dispositivo|Utilizzare la Console di amministrazione e altre risorse per monitorare le query e gli utenti di dispositivo. Vedere [monitorare il dispositivo tramite la Console di amministrazione &#40;Analitica Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Caricare i dati in SQL Server PDW|Caricare i dati all'applicazione. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Creare un piano di ripristino di emergenza|Pianificare come si desidera proteggere i dati da errori hardware o la sovrascrittura di dati. Creare un piano di backup regolari utilizzando i piani e ripristino in caso di danneggiamento dei dati o di perdita. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Monitoraggio del dispositivo|Monitoraggio di stato dello strumento, integrità e prestazioni utilizzando viste di sistema, log e la Console di amministrazione. Correggere o segnalare gli eventuali problemi. Vedere [lo stato di integrità dello strumento di monitoraggio &#40;Analitica Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
