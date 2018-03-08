---
title: "Proprietà server (pagina Generale) | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: tools
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.reportserver.serverproperties.general.f1
ms.assetid: 23537d52-4356-450f-a671-5921cef2431f
caps.latest.revision: "34"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 974897a7498eb9032bbe43933b9e9931f5969449
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="report-server-properties-general-page"></a>Proprietà del server di report (pagina Generale)
  Questa pagina consente di visualizzare o modificare il titolo utilizzato in Gestione report, abilitare o disabilitare la cartella Report personali, selezionare una definizione di ruolo per la sicurezza della cartella Report personali e abilitare o disabilitare il controllo di stampa client.  
  
 **Per aprire la pagina:**
 1) Start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]
 2) Connettersi a un'istanza del server di report.
 3) Fare clic con il pulsante destro del mouse sul nome del server di report e quindi scegliere **Proprietà**.  
  
 La modalità del server determina le proprietà del server che è possibile impostare. Se si gestisce un server di report configurato per la modalità integrata SharePoint, non è possibile abilitare Report personali o impostare il titolo per il portale Web.  
  
## <a name="options"></a>Opzioni  
 **Nome**  
 Digitare un nome che verrà visualizzato nella parte superiore del portale Web. Per impostazione predefinita, il valore è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Il nome specificato compare solamente in Gestione report.  
  
 **Versione**  
 Questa proprietà è di sola lettura. Specifica la versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in uso.  
  
 **Edizione**  
 Questa proprietà è di sola lettura. Viene specificata l'istanza corrente del server di report. Gestione report non è disponibile in tutte le edizioni di [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per un elenco delle funzionalità supportate dalle edizioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere [Funzionalità supportate dalle edizioni di SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 **Modalità di autenticazione**  
 Questa proprietà è di sola lettura. che identifica i tipi di richieste di autenticazione accettati dall'istanza del server di report. Per modificare la modalità di autenticazione, è necessario modificare il file **RSReportServer.config** . Per altre informazioni, vedere [Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 **URL**  
 Questa proprietà è di sola lettura. che specifica l'URL del servizio Web ReportServer. Questo valore è specificato nello strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Per altre informazioni, vedere [Configurare un URL &#40;Gestione configurazione SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md).  
  
 **Abilita una cartella Report personali per ogni utente**  
 Consente di rendere disponibile agli utenti la cartella **Report personali** . Questa opzione è disponibile solo per i server di report in modalità nativa.  
  
 **Selezionare il ruolo da applicare a ogni cartella Report personali**  
 Consente di specificare una definizione di ruolo da utilizzare per la sicurezza della cartella Report personali. La definizione di ruolo identifica il set delle attività che sono supportate in ogni cartella Report personali.  

  
## <a name="see-also"></a>Vedere anche  
 [Impostare le proprietà di un server di report &#40;Management Studio&#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Eseguire la connessione a un server di report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Abilitare e disabilitare la funzionalità Report personali](../../reporting-services/report-server/enable-and-disable-my-reports.md)   
 [Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Proteggere i report personali](../../reporting-services/security/secure-my-reports.md)  
  
  

