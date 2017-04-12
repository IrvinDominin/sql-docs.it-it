---
title: "Requisiti dell&#39;applicazione Web (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "Master Data Services"
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
caps.latest.revision: 40
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 38
---
# Requisiti dell&#39;applicazione Web (Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] è un'applicazione Web ospitata da Internet Information Services (IIS). [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] funziona solo in Internet Explorer (IE) 9 o versioni successive. IE 8 e le versioni precedenti, Microsoft Edge e Chrome non sono supportati.  
  
 Utilizzare [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] per creare e configurare l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] . [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] IIS viene configurato nel computer locale, rappresentando pertanto la soluzione ottimale per le attività di configurazione Web iniziali. Configurare ad esempio un ambiente [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] con una singola applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] oppure configurare la prima applicazione Web in una distribuzione con scalabilità orizzontale di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]. Utilizzare gli strumenti di IIS per eseguire le attività più complesse, ad esempio la configurazione di più server Web in una distribuzione con scalabilità orizzontale.  
  
> [!NOTE]  
>  Tutti i computer in cui si installano componenti di [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] devono essere dotati di licenza appropriata. Per ulteriori informazioni, fare riferimento al Contratto di licenza.  
  
## Requisiti  
  
### Sistema operativo  
 Prima di installare [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], esaminare i requisiti seguenti:    
    
-   [Requisiti hardware e software per l'installazione di SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server-2016.md)    
  
### Microsoft Silverlight  
 Per funzionare nell'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] , è necessario installare Silverlight 5 nel computer client. Se non si dispone della versione richiesta di Silverlight, sarà necessario installarla quando si passa a un'area dell'applicazione Web in cui è necessaria. Silverlight 5 può essere installato da [qui](http://go.microsoft.com/fwlink/?LinkId=243096).  
  
### Ruolo e servizi ruolo  
 In Windows Server 2012 o Windows Server 2012 R2 è possibile usare **Server Manager**, disponibile in Microsoft Management Console (MMC), per installare il ruolo **Server Web (IIS)** e i servizi ruolo necessari.  
 
 
> [!IMPORTANT]  
>La funzionalità **Compressione contenuto dinamico** è abilitata per impostazione predefinita. Questo riduce in modo significativo le dimensioni della risposta XML e salva le operazioni I/O di rete, anche se aumenta l'utilizzo della CPU.  Per altre informazioni, vedere **[CTP 2.0] Prestazioni migliorate ** in [Novità in Master Data Services &#40;MDS&#41;](../../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
||  
|-|  
|Internet Information Services<br /><br /> Strumenti di gestione Web<br /><br /> Console di gestione IIS<br /><br /> Servizi Web<br /><br /> Sviluppo applicazioni<br /><br /> Estendibilità .NET 3.5<br /><br /> Estendibilità .NET 4.5<br /><br /> ASP.NET 3.5<br /><br /> ASP.NET 4.5<br /><br /> Estensioni ISAPI<br /><br /> Filtri ISAPI<br /><br /> Funzionalità HTTP comuni<br /><br /> Documento predefinito<br /><br /> Esplorazione directory<br /><br /> Errori HTTP<br /><br /> Contenuto statico<br /><br /> [Nota: non installare la pubblicazione WebDAV]<br /><br /> Integrità e diagnostica<br /><br /> Registrazione HTTP<br /><br /> Monitoraggio richieste<br /><br /> Prestazioni<br /><br /> Compressione contenuto statico<br /><br /> Sicurezza<br /><br /> Filtro richieste<br /><br /> Autenticazione di Windows|  
  
### Funzionalità 
 In Windows Server 2012 e Windows Server 2012 R2 è possibile usare **Server Manager** per installare le funzionalità necessarie seguenti.  
  
||  
|-|  
|.NET Framework 3.5 (inclusi .NET 2.0 e 3.0)<br /><br /> .NET Framework 4.5 Advanced Services<br /><br /> ASP.NET 4.5<br /><br /> WCF Services<br /><br /> Attivazione HTTP [Nota: operazione necessaria.]<br /><br /> Condivisione porta TCP<br /><br /> Servizio Attivazione processo Windows<br /><br /> Modello di processo<br /><br /> Ambiente .NET<br /><br /> API di configurazione|  
  
 Di seguito viene mostrato uno script di PowerShell di esempio per aggiungere i ruoli e le funzionalità del server richiesti. I ruoli e le funzionalità del server richiesti variano a seconda dell'ambiente.  
  
```powershell  
Install-WindowsFeature Web-Mgmt-Console, AS-NET-Framework, Web-Asp-Net, Web-Asp-Net45, Web-Default-Doc, Web-Dir-Browsing, Web-Http-Errors, Web-Static-Content, Web-Http-Logging, Web-Request-Monitor, Web-Stat-Compression, Web-Filtering, Web-Windows-Auth, NET-Framework-Core, WAS-Process-Model, WAS-NET-Environment, WAS-Config-APIs  
  
Install-WindowsFeature Web-App-Dev, NET-Framework-45-Features -IncludeAllSubFeature –Restart  
```  
  
 Per altre informazioni sul comando di PowerShell, vedere [Install-WindowsFeature](https://technet.microsoft.com/library/jj205467).  
  
### Account e autorizzazioni  
  
|Tipo|Descrizione|  
|----------|-----------------|  
|Account di Windows|È necessario accedere al computer server Web con un account di Windows che disponga dell'autorizzazione per configurare ruoli di Windows, servizi ruolo e funzionalità e per creare e gestire pool di applicazioni, siti Web e applicazioni Web in IIS sul computer locale.|  
|Account servizio|Quando si crea l'applicazione Web [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], è necessario specificare un'identità per il pool di applicazioni in cui viene eseguita l'applicazione. Questo account può essere diverso dall'account del servizio che è stato specificato durante la creazione del database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].<br /><br /> Questa identità deve essere un account utente di dominio e viene aggiunta al ruolo di database mds_exec nel database [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] per consentirne l'accesso. Per altre informazioni, vedere [Account di accesso, utenti e ruoli di database &#40;Master Data Services&#41;](../../master-data-services/database-logins-users-and-roles-master-data-services.md). Questo account viene aggiunto anche a un gruppo di Windows [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)], **MDS_ServiceAccounts**, a cui viene concessa l'autorizzazione per la directory di compilazione temporanea, **MDSTempDir**, nel file system. Per altre informazioni, vedere [Autorizzazioni per file e cartelle &#40;Master Data Services&#41;](../../master-data-services/folder-and-file-permissions-master-data-services.md).|  
  
## Vedere anche  
 [Installazione di Master Data Services](../../master-data-services/install-windows/install-master-data-services.md)   
 [Master Data Services](../../sql-server/media/master-data-services.png)       
 [Creare un'applicazione Web Gestione dati master &#40;Master Data Services&#41;](../../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)   
 [Pagina Configurazione Web &#40;Gestione configurazione Master Data Services&#41;](../../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
  