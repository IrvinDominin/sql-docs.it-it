---
title: Requisiti hardware e Software per Reporting Services in modalità SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 27ca12268f34f116b4158533a12b75920265d179
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210531"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Requisiti hardware e software per Reporting Services in modalità SharePoint
  In questo argomento vengono descritti i prerequisiti, i requisiti hardware e le considerazioni sull'installazione per [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in esecuzione in modalità SharePoint. Dal momento la modalità SharePoint di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] richiede un server SharePoint, la maggior parte dei requisiti sono basati sull'ambiente SharePoint. Per i server di report in modalità nativa è consigliabile soddisfare i requisiti hardware e software minimi per l'esecuzione di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Per ulteriori informazioni, vedere [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [Prerequisiti](#bkmk_prereq)  
  
-   [Requisiti del database del server di report](#bkmk_report_server_database)  
  
-   [Requisiti per Power View](#bkmk_powerview)  
  
-   [Altre informazioni](#bkmk_more_information)  
  
##  <a name="bkmk_prereq"></a> Prerequisiti  
  
-   Per le installazioni locali, l'account connesso durante l'installazione di SharePoint e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deve essere un membro del gruppo di amministratori del sistema operativo locale. L'account di configurazione non deve essere un membro del gruppo di amministratori della farm di SharePoint.  
  
     Per ulteriori informazioni, vedere [Autorizzazioni e impostazioni di sicurezza per gli account in SharePoint Server 2013](http://technet.microsoft.com/library/cc678863.aspx).  
  
-   Per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in esecuzione in modalità SharePoint è richiesto il server SharePoint. Per ulteriori informazioni sui requisiti e sulle configurazioni di SharePoint, vedere gli argomenti seguenti:  
  
    -   [Requisiti hardware e software (SharePoint 2013)](http://go.microsoft.com/fwlink/p/?LinkId=256365) (http://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [Gestione e ridimensionamento delle capacità per SharePoint Server 2013](http://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Requisiti software per Business Intelligence (SharePoint 2013)](http://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Requisiti hardware e software (SharePoint Server 2010)](http://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Gestione e ridimensionamento delle capacità per SharePoint Server 2010](http://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   Se si desidera aggiornare l'installazione esistente di SharePoint per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] con [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vedere [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
-   Verificare che il servizio **SharePoint 2013 Administration** venga avviato in Server Manager di Windows.  
  
###  <a name="bkmk_report_server_database"></a> Requisiti del database del server di report  
  
-   In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e nei prodotti e nelle tecnologie SharePoint vengono utilizzati database relazionali di SQL Server per archiviare i dati dell'applicazione.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] richiede un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] di un'edizione di SQL Server compatibile. Per ulteriori informazioni sui requisiti hardware e software, vedere [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Nei prodotti SharePoint può essere utilizzata un'istanza del database esistente. Se non è installata alcuna istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] , tramite il programma di installazione dei prodotti SharePoint viene installato SQL Server Express Edition per i database dell'applicazione SharePoint.  
  
-   L'istanza del server di report non può utilizzare SQL Server Express Edition per il proprio database. Tuttavia, l'istanza di SQL Server Express Edition installata mediante il prodotto SharePoint può esistere in modalità side-by-side con altre eventuali edizioni del motore di database.  
  
##  <a name="bkmk_powerview"></a> Requisiti di [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]  
 Esaminare la [documentazione di Power View](http://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) più aggiornata su Office.Microsoft.com. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] è ora una funzionalità di Microsoft Excel 2013 ed è incluso nel componente aggiuntivo di [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services per Microsoft SharePoint Server 2010 e 2013 Enterprise Edition.  
  
##  <a name="bkmk_more_information"></a> Ulteriori informazioni  
 Per informazioni sulle modifiche di SharePoint, vedere [modifiche da SharePoint 2010 a SharePoint 2013](http://technet.microsoft.com/library/ff607742\(office.15\).aspx) (http://technet.microsoft.com/en-us/library/ff607742(office.15).aspx).  
  
 [Note sulla versione di SQL Server 2014](http://go.microsoft.com/fwlink/?LinkID=296445).  
  
  
