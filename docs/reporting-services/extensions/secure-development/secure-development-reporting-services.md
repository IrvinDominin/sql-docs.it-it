---
title: Sviluppo sicuro (Reporting Services) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: extensions
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- development security [Reporting Services]
- security [Reporting Services], development
- security [Reporting Services], strategies
ms.assetid: 12161a6c-b93b-4312-9d27-0c922561eb9b
caps.latest.revision: "15"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1e9152b933bbb6a021b232a7271d412c30169b5d
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="secure-development-reporting-services"></a>Sviluppo sicuro (Reporting Services)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] è un potente sistema di sicurezza che consente l'esecuzione di codice in contesti di sicurezza soggetti a vincoli definiti dall'amministratore. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] usano il sistema di sicurezza di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], noto come sicurezza dall'accesso di codice (o sicurezza basata sull'evidenza). In un sistema con sicurezza dall'accesso di codice un utente può essere considerato attendibile per accedere a una risorsa, ma se il codice eseguito non è attendibile, l'accesso alla risorsa verrà negato.  
  
 A differenza della sicurezza basata su utenti specifici, la sicurezza basata su codice può essere espressa per assembly o dati personalizzati, per il recapito, il rendering e le estensioni di sicurezza sviluppati per [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Il codice dell'estensione può essere eseguito da un numero qualsiasi di utenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ciascuno dei quali non è noto in fase di sviluppo. In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] le estensioni o gli assembly personalizzati richiedono criteri di sicurezza specifici, rappresentati come tipi in [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Per altre informazioni sulla sicurezza dall'accesso di codice, vedere "Sicurezza dall'accesso di codice" nella documentazione di [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 [Sicurezza dall'accesso di codice in Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)  
 Descrive la sicurezza dall'accesso di codice e la configurazione dei criteri per le estensioni e gli assembly personalizzati in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 [Informazioni sui criteri di sicurezza](../../../reporting-services/extensions/secure-development/understanding-security-policies.md)  
 Descrive i diversi tipi di assembly in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e il modo in cui la sicurezza dall'accesso di codice influisce sulle autorizzazioni per il codice.  
  
 [Uso di file di criteri di sicurezza di Reporting Services](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md)  
 Descrive i diversi componenti di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] e i corrispondenti file di configurazione dei criteri.  
  
  
