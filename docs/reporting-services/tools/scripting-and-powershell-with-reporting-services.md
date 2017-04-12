---
title: "Script e PowerShell con Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "09/14/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "script [Reporting Services]"
  - "Reporting Services, scripting"
  - "scripting [Reporting Services]"
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 17
---
# Script e PowerShell con Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta un'ampia gamma di scenari di sviluppo e gestione tramite script, tra cui l'utilità della riga di comando rs.exe, i cmdlet PowerShell per server di report in modalità SharePoint, sfruttando il modello a oggetti [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] da PowerShell per la modalità nativa e SharePoint.  
  
-   Gli amministratori possono scrivere script in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] per automatizzare le procedure di distribuzione e gestione dell'installazione di un server di report. Gli amministratori possono anche generare ed eseguire script [!INCLUDE[tsql](../../includes/tsql-md.md)] che consentono di creare, configurare e aggiornare un database del server di report. Gli amministratori possono inoltre utilizzare le caratteristiche script di registrazione e riproduzione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per automatizzare le attività di manutenzione di routine.  
  
-   Gli sviluppatori possono creare applicazioni personalizzate che includono script. È possibile eseguire uno script che effettua chiamate al servizio Web ReportServer. Nello script è possibile scrivere quasi tutte le operazioni che si possono scrivere in codice gestito.  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] supporta lo script .NET [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] come linguaggio di script che può essere elaborato dall'utilità RS.exe, un host di script che viene eseguito nel server di report.  
  
## Cmdlet ed esempi di PowerShell in modalità SharePoint di Reporting Services  
 ![Contenuto correlato di PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.png "Contenuto correlato di PowerShell")  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include i cmdlet [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] per l'amministrazione del server di report.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md) Sono inclusi gli esempi seguenti:  
  
    -   Creare un proxy e un'applicazione di servizio  
  
    -   Rivedere e aggiornare un'estensione per il recapito  
  
    -   Ottenere e impostare le proprietà del database dell'applicazione Reporting Service, ad esempio timeout database  
  
    -   Elencare le estensioni per i dati  
  
## Modello a oggetti di Reporting Services ed esempi di Powershell  
 ![Contenuto correlato di PowerShell](../../analysis-services/instances/install-windows/media/rs-powershellicon.png "Contenuto correlato di PowerShell")  
  
 Le chiamate del modello a oggetti principale di PowerShell valide in generale per la modalità SharePoint e nativa, ad esempio l'attività di migrazione, l'attività di sottoscrizione ed esempi più correlati per le sottoscrizioni, funzionano in SQL15.  
  
-   [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../reporting-services/subscriptions/manage subscription owners and run subscription - powershell.md) (Usare PowerShell per modificare ed elencare i proprietari di sottoscrizioni di Reporting Services ed eseguire una sottoscrizione).  
  
-   [Usare PowerShell per creare una VM di Azure con un server di report in modalità nativa](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   Vedere la sezione "Accedere alle classi WMI utilizzando PowerShell" in [Access the Reporting Services WMI Provider](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md).  
  
-   [Come amministrare SSRS con PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell).  
  
## Esempi di script RS.exe  
  
-   [Script di esempio rs.exe di Reporting Services per la copia di contenuto tra server di report](../../reporting-services/tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
-   Per altri esempi di script, applicazioni ed estensioni, vedere gli [esempi di prodotti di Reporting Services di SQL Server](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## Vedere anche  
 [Utilità RS.exe &#40;SSRS&#41;](../../reporting-services/tools/rs-exe-utility-ssrs.md)   
 [Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
 [Eseguire lo script con l'utilità rs.exe e il servizio Web](../../reporting-services/tools/script-with-the-rs-exe-utility-and-the-web-service.md)  
  
  