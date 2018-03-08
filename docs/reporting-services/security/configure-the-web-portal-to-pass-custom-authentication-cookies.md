---
title: Configurare il portale Web per il passaggio di cookie di autenticazione personalizzati | Microsoft Docs
ms.custom: 
ms.date: 04/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
caps.latest.revision: "18"
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 083b458f0800fc560822f2ae933fd3b0503979d2
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="configure-the-web-portal-to-pass-custom-authentication-cookies"></a>Configurare il portale Web per il passaggio di cookie di autenticazione personalizzati

Se si sta usando un'estensione di autenticazione personalizzata, è necessario configurare il portale Web per la trasmissione di cookie di autenticazione personalizzati. In caso contrario, il portale Web trasmetterà i cookie solo mediante richieste HTTP specifiche del server di report. Se si desidera trasmettere ulteriori cookie, è necessario modificare il file RSReportServer.Config.

## <a name="modifying-the-rsreportserverconfig-file"></a>Modifica del file RSReportServer.config

È possibile consentire a [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] di trasmettere altri cookie al server di report aggiungendo un elemento \<**PassThroughCookies**> alle impostazioni di configurazione del portale Web nel file RSReportServer.config. La trasmissione di cookie aggiuntivi è utile in una soluzione di autenticazione Single Sign-On che, insieme ai cookie di autenticazione del server di report, richiede anche cookie di un sistema di autenticazione di terze parti.

Per consentire la trasmissione di altri cookie tramite richieste HTTP quando si usa il portale Web, impostare gli elementi seguenti nel file RSReportServer.config:
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>Vedere anche

[Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md)   
[File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
[Panoramica sulle estensioni di sicurezza](../../reporting-services/extensions/security-extension/security-extensions-overview.md)   
[Configurare e amministrare un server di report &#40;modalità nativa SSRS&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
