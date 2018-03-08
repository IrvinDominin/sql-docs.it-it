---
title: Integrazione di Reporting Services nelle applicazioni | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: application-integration
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0185a0cb501242355d99369f3084eaa6f6a2e3da
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="integrating-reporting-services-into-applications"></a>Integrazione di Reporting Services nelle applicazioni

[!INCLUDE [ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-2017](../../includes/ssrs-appliesto-not-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../../includes/ssrs-appliesto-not-pbirs.md)]

  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è una piattaforma di creazione di report aperta ed estendibile progettata per fornire agli sviluppatori un set completo di API per lo sviluppo di soluzioni.

> [!NOTE]
> A partire da SQL Server 2017 Reporting Services, è disponibile l'accesso all'API REST per lo sviluppo di soluzioni. L'accesso all'API SOAP è stato deprecato. Per altre informazioni, vedere [Sviluppo con le API REST per Reporting Services](../developer/rest-api.md).
  
 Sono disponibili tre opzioni per l'integrazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni personalizzate: il servizio Web ReportServer, anche noto come API SOAP di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], i controlli ReportViewer per [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e l'accesso con URL. Ogni opzione fornisce un approccio diverso per l'integrazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni.
  
## <a name="report-server-web-service"></a>Servizio web ReportServer

 Il servizio Web ReportServer è l'interfaccia principale per lo sviluppo in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Sia che si sviluppi codice per gestire il catalogo di report o che si sviluppi codice per il rendering dei report in un formato supportato, il servizio Web espone tutti i metodi necessari per integrare [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni. Un esempio di tale applicazione è costituito da Gestione report, incluso in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], che usa il servizio Web per la gestione del database del server di report.  
  
## <a name="reportviewer-controls-for-visual-studio"></a>Controlli ReportViewer per Visual Studio

 I controlli ReportViewer disponibili per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vengono usati per l'integrazione delle funzionalità di visualizzazione dei report nelle applicazioni. Sono disponibili due controlli, uno per le applicazioni basate su Windows Form e uno per le applicazioni Web Form. Ogni controllo fornisce funzionalità per la visualizzazione dei report distribuiti in un server di report e consente di eseguire il rendering dei report presenti in un ambiente in cui non è stato installato un server di report.  
  
## <a name="url-access"></a>accesso con URL  
 L'accesso con URL rappresenta un'altra opzione per l'integrazione delle funzionalità di visualizzazione dei report nelle applicazioni se non sono disponibili i controlli ReportViewer. L'accesso con URL è inoltre utile per inviare agli utenti collegamenti ai report tramite posta elettronica.  
  
## <a name="in-this-section"></a>Contenuto della sezione

 [Integrazione di Reporting Services tramite SOAP](../../reporting-services/application-integration/integrating-reporting-services-using-soap.md)  
 Viene descritto come integrare le funzionalità di navigazione e gestione dei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni aziendali esistenti utilizzando il servizio Web ReportServer.  
  
 [Integrazione di Reporting Services tramite i controlli ReportViewer](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md)  
 Viene descritto come integrare le funzionalità di visualizzazione dei report nelle applicazioni esistenti utilizzando i controlli ReportViewer.  
  
 [Integrazione di Reporting Services tramite l'accesso con URL](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)  
 Viene descritto come integrare le funzionalità di navigazione dei report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nelle applicazioni esistenti utilizzando l'accesso con URL.  
  
## <a name="next-steps"></a>Passaggi successivi

Per scegliere tra l'accesso con URL o le API SOAP, vedere [Scelta tra accesso con URL e SOAP in Reporting Services](choosing-between-url-access-and-soap.md).

Per informazioni sull'API REST di Reporting Services per SQL Server 2017, vedere [Sviluppo con le API REST per Reporting Services](../developer/rest-api.md).

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
