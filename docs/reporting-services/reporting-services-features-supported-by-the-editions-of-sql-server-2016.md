---
title: "Funzionalit&#224; di Reporting Services supportate dalle edizioni di SQL Server 2016 | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: 39f03d2d-6e48-4b34-a9d3-07f86313b937
caps.latest.revision: 3
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 3
---
# Funzionalit&#224; di Reporting Services supportate dalle edizioni di SQL Server 2016
In questo argomento vengono forniti i dettagli delle funzionalità supportate dalle diverse edizioni di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
 SQL Server Evaluation Edition è disponibile per un periodo di valutazione di 180 giorni.  
  
 Per le note sulla versione più recenti, vedere [Note sulla versione di SQL Server 2016](../sql-server/sql-server-2016-release-notes.md). Per le ultime informazioni sulle novità, vedere [Novità di Reporting Services (SSRS)](What's%20New%20in%20Reporting%20Services%20\(SSRS\).md).
    
 **Per provare SQL Server 2016**    
    
 > [![Download da Evaluation Center](../analysis-services/media/download.png)](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016) **[Scaricare SQL Server 2016 da Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**    
    
> ![Macchina virtuale di Azure piccola](../analysis-services/media/azure-virtual-machine-small.png) **[Attivare una macchina virtuale con SQL Server 2016 già installato](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)**    

Per le funzionalità supportate dalle edizioni Evaluation e Developer, vedere SQL Server Enterprise Edition.

Per passare alla tabella per una tecnologia SQL Server, fare clic sul relativo collegamento:  

-   [Reporting Services](#SSRS)  
  
-   [Client di Business Intelligence](#BIC)  

##  <a name="SSRS"></a> Reporting Services  
  
|Nome funzionalità|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Report e KPI per dispositivi mobili|Sì||||||Sì|  
|Edizione supportata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per il database del catalogo|Standard o versione successiva|Standard o versione successiva|Web|Express|||Standard o versione successiva|  
|Edizione supportata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per le origini dati|Tutte le edizioni di   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Web|Express|||Tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|  
|Server di report|Sì|Sì|Sì|Sì|||Sì|  
|Progettazione report|Sì|Sì|Sì|Sì|||Sì|  
|Portale Web di Progettazione report|Sì|Sì|Sì|Sì|||Sì|  
|Sicurezza basata sui ruoli|Sì|Sì|Sì|Sì|||Sì|  
|Esportazione in Excel, PowerPoint, Word, PDF e immagini|Sì|Sì|Sì|Sì|||Sì|  
|Misuratori e grafici migliorati|Sì|Sì|Sì|Sì|||Sì|  
|Aggiungere elementi di un report a dashboard di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]|Sì|Sì|Sì|Sì|||Sì|  
|Autenticazione personalizzata|Sì|Sì|Sì|Sì|||Sì|  
|Dati del report come feed di dati|Sì|Sì|Sì|Sì|||Sì|  
|Supporto modelli|Sì|Sì|Sì||||Sì|  
|Creare ruoli personalizzati per la sicurezza basata sui ruoli|Sì|Sì|||||Sì|  
|Sicurezza elemento modello|Sì|Sì|||||Sì|  
|Click-through illimitato|Sì|Sì|||||Sì|  
|Libreria componenti condivisa|Sì|Sì|||||Sì|  
|Sottoscrizioni e pianificazione posta elettronica e condivisione file|Sì|Sì|||||Sì|  
|Cronologia report, esecuzione snapshot e memorizzazione nella cache|Sì|Sì|||||Sì|  
|Integrazione con SharePoint|Sì|Sì|||||Sì|  
|Supporto origini dati remote e non SQL<sup>1</sup>|Sì|Sì|||||Sì|  
|Estensibilità RDCE per il rendering, il recapito e le origini dati|Sì|Sì|||||Sì|  
|Personalizzazione|Sì||||||Sì|  
|Sottoscrizione di report guidate dai dati|Sì||||||Sì|  
|Distribuzione con scalabilità orizzontale (Web farm)|Sì||||||Sì|  
|Avvisi<sup>2</sup>|Sì||||||Sì|  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|Sì||||||Sì|  
  
 <sup>1</sup> Per altre informazioni sulle origini dati supportate in SQL Server 2016 Reporting Services (SSRS), vedere [Origini dei dati supportate da Reporting Services &#40;SSRS&#41;](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup>Richiede Reporting Services in modalità SharePoint. Per altre informazioni, vedere [Installare la modalità SharePoint di Reporting Services](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
## Requisiti dell'edizione server del database del server di report  
 Quando si crea un database del server di report, non tutte le edizioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] possono essere usate per ospitare il database. Nella tabella seguente sono illustrate le edizioni del [!INCLUDE[ssDE](../includes/ssde-md.md)] che è possibile usare per le edizioni specifiche di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
|Per questa edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Edizione dell'istanza del Motore di database da usare per ospitare il database|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Edizioni Enterprise o Standard (locali o remote)|  
|Standard|Edizioni Enterprise o Standard (locali o remote)|  
|Web|Web Edition (solo locale)|  
|Express with Advanced Services|Express with Advanced Services (solo locale).|  
|Copia di valutazione|Copia di valutazione|  
  
##  <a name="BIC"></a> Client di Business Intelligence  
 Le seguenti applicazioni client del software sono disponibili nell'Area download Microsoft e sono disponibili come supporto per la creazione di documenti di Business Intelligence eseguiti in un'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Quando questi documenti vengono ospitati in un ambiente server, usare un'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] supportata per tale tipo di documento. Nella tabella seguente viene indicata l'edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contenente le funzionalità del server richieste per ospitare i documenti creati in queste applicazioni client.  
  
|Nome dello strumento|Enterprise|Standard|Web|Express with Advanced Services|Express with Tools|Express|Sviluppatore|  
|---------------|----------------|--------------|---------|------------------------------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)] (rdl e rds)|Sì|Sì|||||Sì|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] (rsmobile)|Sì||||||Sì|  
|App di Power BI per dispositivi mobili (iOS, Windows 10, Android) (rsmobile)|Sì||||||Sì|  
  
> [!NOTE]  
> 1.  La tabella sopra riportata identifica le edizioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] richieste per abilitare gli strumenti client; le funzionalità possono tuttavia accedere ai dati ospitati in ogni edizione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> 2.  [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] è il punto singolo per la creazione di report per dispositivi mobili. Connettersi a un server di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per accedere alle origini dati e creare report. Pubblicare quindi i report nel server di [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] per consentire l'accesso ad altri utenti dell'organizzazione, nel server o nei dispositivi mobili. È anche possibile usare [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long-md.md)] autonomo con origini dati locali  
> 3.  Se si usa [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] in locale, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] nel cloud o entrambi come soluzione di recapito dei report, è necessaria una sola app per dispositivi mobili per accedere a dashboard e report sui dispositivi mobili. Le app di [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] sono disponibili per il download dall'App Store di Windows, iOS o Android.  

## Vedere anche  
 [Funzionalità supportate dalle edizioni di SQL Server 2016](Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)  
 [Specifiche di prodotto per SQL Server 2016](../Topic/Product%20Specifications%20for%20SQL%20Server%202016.md)   
 [Installazione per SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md) 