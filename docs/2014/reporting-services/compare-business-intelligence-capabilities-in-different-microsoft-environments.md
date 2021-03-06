---
title: Confrontare le funzionalità di Business Intelligence In diversi ambienti Microsoft | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 1fb759ee-8172-4c4c-9f7d-49af2c731006
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: dfe97b4cab555b5da6224edef97c73958bb362b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144373"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Confrontare le funzionalità di Business Intelligence in diversi ambienti Microsoft
  Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence può essere distribuita in numerosi ambienti diversi, tra cui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] con SharePoint Server, SharePoint Online e Power BI per Office 365. In questo argomento vengono confrontati i componenti e le funzionalità supportati in ogni ambiente.  
  
 Per altre informazioni sul confronto tra SharePoint Server e SharePoint Online, vedere [Confrontare piani e opzioni di SharePoint](http://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Creare e gestire report e dashboard di Business Intelligence  
  
||SQL Server 2014 e SharePoint Server 2013|SharePoint Online Piano 2|Power BI per Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Siti di Business Intelligence|Raccolta [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]|no|Sito di Power BI|  
|Amministrazione dei dati e gestione e condivisione delle query|no|no|Sì  **<sup>1</sup>**|  
|Integrazione con Master Data Services (MDS) e Data Quality Services (DQS)|Sì|no|no|  
|Pianificazione dell'aggiornamento dati|Sì, ma non sono supportate le cartelle di lavoro che contengono dati di Power Query|no|Sì|  
|Query in linguaggio naturale (domande e risposte)|no|no|Sì  **<sup>2</sup>**|  
|Previsione predittiva|no|no|Sì  **<sup>3</sup>**|  
|Integrazione di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|Sì|no|no|  
|Integrazione di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] (multidimensionale e tabulare)|Sì|no|no|  
|Esportazione di dashboard interattivi di Power View nelle presentazioni di PowerPoint|Sì|no|no|  
|Creazione di dashboard basati su browser|Sì|no|no|  
|Monitoraggio dell'utilizzo|Sì|no|Sì|  
|Sicurezza del basata su riga sfrutta [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cubi|Sì|no|no|  
  
 **<sup>1</sup>**[informazioni sul ruolo degli amministratori dei dati nella gestione dei dati](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) e [Video: gestione delle informazioni di BI e amministrazione dei dati di Power](https://www.youtube.com/watch?v=8dHOj68ts7c).    
  
 **<sup>2</sup>**[power BI domande e risposte: ottimizzare una cartella di lavoro di Power BI (modellazione cloud)](https://support.office.com/article/Power-BI-Q-A-Optimize-a-Power-BI-workbook-cloud-modeling--96dc5941-d0f1-44e2-9d9d-c038a3a55849?ui=en-US&rs=en-US&ad=US).    
  
 **<sup>3</sup>**[Introduzione alle nuove funzionalità di previsione in Power View per Office 365](http://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).    
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Visualizzare ed esplorare dati, report e dashboard di Business Intelligence  
  
||SQL Server 2014 e SharePoint Server 2013|SharePoint Online Piano 2|Power BI per Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Visualizzazione delle cartelle di lavoro di Microsoft Excel in un browser|Sì, se le dimensioni della cartella di lavoro sono inferiori a 2 GB|Sì, se le dimensioni della cartella di lavoro sono inferiori a 10 MB|Sì, se le dimensioni della cartella di lavoro sono inferiori a 250 MB|  
|Esplorazione dei dati basati su browser in HTML5|no|no|Sì|  
|App di Business Intelligence per dispositivi mobili per accedere a report e dashboard in remoto|no|no|Sì  **<sup>1</sup>**|  
|Cartella di lavoro di Excel con [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] come origine dati  **<sup>2</sup>**|Sì|no|no|  
|Possibilità di usare le funzionalità in versioni e browser diversi|Sì, per le visualizzazioni non relative a Power View  **<sup>3</sup>**|Sì, per la cartella di lavoro di dimensioni inferiori a 10 MB  **<sup>3</sup>**|Sì  **<sup>3</sup>**|  
  
 **<sup>1</sup>**[Microsoft Power BI](http://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).    
  
 **<sup>2</sup>**[cartelle di lavoro di PowerPivot come origine dati  ](http://blogs.technet.com/b/excel_services__powerpivot_for_sharepoint_support_blog/archive/2013/02/15/powerpivot-workbook-as-a-data-source.aspx)  
  
 **<sup>3</sup>**[supporto mobile tra strumenti di Business Intelligence (BI)](http://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) e [Planning for Reporting Services e supporto Browser per Power View (Reporting Services 2014)](http://msdn.microsoft.com/library/ms156511.aspx).    
  
## <a name="more-information"></a>Altre informazioni  
  
-   [Funzionalità di business intelligence in Excel, SharePoint Online e Power BI per Office 365](https://technet.microsoft.com/en-us/library/dn198235.aspx).  
  
-   Per informazioni sui requisiti per l'uso dei sinonimi, vedere [Aggiungere sinonimi a un modello di dati di Excel in Power Pivot](https://support.office.com/Article/Add-synonyms-to-a-Power-Pivot-Excel-data-model-345f4f5b-5ec2-4998-bc46-a26bdc0810b6?ui=en-US&rs=en-US&ad=US).  
  
-   [Office Online - Scegliere un social network aziendale: Yammer o Newsfeed?](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
-   [Power BI per Office 365](http://www.microsoft.com/powerbi/default.aspx)  
  
-   [Prezzi di Power BI](http://www.microsoft.com/powerBI/pricing.aspx)  
  
-   [Confronto tra un sito Centro business intelligence e i siti Power BI per Office 365](http://technet.microsoft.com/library/dn394343\(v=office.15\).aspx)  
  
-   [Introduzione a strumenti di analisi e creazione di report di Microsoft BI](http://go.microsoft.com/fwlink/p/?LinkId=617093)  
  
## <a name="community-content"></a>Contenuto della community  
 [Microsoft BI in modalità self-service in locale e nel cloud](http://businessintelligist.com/2014/02/07/microsoft-self-service-bi-on-premise-vs-could/)  
  
  
