---
title: Sicurezza e protezione di Reporting Services | Microsoft Docs
ms.custom: 
ms.date: 08/26/2016
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
- security [Reporting Services]
- Reporting Services, security
ms.assetid: 270075c5-bf12-4467-a775-abbda3d954a5
caps.latest.revision: "21"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 0dc30f8152d5d92a186c5357f029cf98cf42fc5d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="reporting-services-security-and-protection"></a>Sicurezza e protezione di Reporting Services
  È possibile usare le informazioni contenute in questa sezione per ottenere altre informazioni sulle caratteristiche di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Questa sezione descrive inoltre i modelli di autorizzazione e i provider di autenticazione supportati in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="extended-protection-for-authentication"></a>Protezione estesa per l'autenticazione  
 A partire da [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], è disponibile il supporto per la protezione estesa per l'autenticazione. La caratteristica di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'uso del binding di canale e dell'associazione al servizio per migliorare la protezione dell'autenticazione. Le funzionalità di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere utilizzate con un sistema operativo che supporti la protezione estesa. Per altre informazioni, vedere [Protezione estesa per l'autenticazione con Reporting Services](../../reporting-services/security/extended-protection-for-authentication-with-reporting-services.md).  
  
## <a name="authentication-and-authorization"></a>Autenticazione e autorizzazione  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] offre diversi tipi di autenticazione per utenti e applicazioni client da autenticare con il server di report. L'utilizzo del tipo di autenticazione corretto per il server di report consente all'organizzazione di ottenere il livello di sicurezza appropriato richiesto dall'organizzazione. Per altre informazioni, vedere [Autenticazione con il server di report](../../reporting-services/security/authentication-with-the-report-server.md).  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] usa inoltre ruoli e autorizzazioni per controllare l'accesso dell'utente al contenuto nel catalogo del server di report (in altre parole chi può accedere a che cosa e in che modo può accedervi). Per altre informazioni, vedere [Ruoli e autorizzazioni &#40;Reporting Services&#41;](../../reporting-services/security/roles-and-permissions-reporting-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descrizioni delle attività|Collegamenti|  
|-----------------------|-----------|  
|Configurare Secure Socket Layer (SSL) per proteggere le connessioni client al server di report.|[Configurare connessioni SSL in un server di report in modalità nativa](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md)|  
  
  
