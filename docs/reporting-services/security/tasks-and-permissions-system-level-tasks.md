---
title: "Attività a livello di sistema | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: security
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
caps.latest.revision: "36"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 035467f28ebd5e5b8cd6a2269688d1b65db09874
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="tasks-and-permissions---system-level-tasks"></a>Attività e autorizzazioni - attività a livello di sistema
  Un'attività a livello di sistema è una raccolta di autorizzazioni correlate alle operazioni eseguibili per l'intero sito del server di report. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] include anche attività a livello di elemento applicabili a elementi specifici. Per altre informazioni, vedere [Attività a livello di elemento](../../reporting-services/security/tasks-and-permissions-item-level-tasks.md). Per ulteriori informazioni sulle attività e le autorizzazioni in generale, vedere [Tasks and Permissions](../../reporting-services/security/tasks-and-permissions.md).  
  
> [!NOTE]  
>  Se si gestiscono queste attività a livello di programmazione, è necessario utilizzare metodi che supportano attività a livello di sistema. Per altre informazioni, vedere <xref:ReportService2010.ReportingService2010.ListTasks%2A> e <xref:ReportService2010.ReportingService2010.ListRoles%2A>.  
  
## <a name="permissions-in-system-level-tasks"></a>Autorizzazioni nelle attività a livello di sistema  
 Nella tabella seguente vengono indicate le autorizzazioni per ogni attività a livello di sistema. L'elenco delle autorizzazioni è puramente informativo e ha lo scopo di fornire una descrizione precisa delle funzionalità disponibili tramite ogni attività.  
  
|Attività|Autorizzazioni|  
|----------|-----------------|  
|Esecuzione delle definizioni dei report|Esecuzione delle definizioni dei report (il nome dell'autorizzazione e il nome dell'attività sono identici)|  
|Generazione di eventi|Generazione di eventi|  
|Gestisci processi|Lettura delle proprietà di sistema<br /><br /> Aggiornamento delle proprietà di sistema|  
|Gestione delle proprietà del server di report|Lettura delle proprietà di sistema<br /><br /> Aggiornamento delle proprietà di sistema|  
|Gestione di ruoli|Creazione di ruoli<br /><br /> Eliminazione di ruoli<br /><br /> Lettura delle proprietà di ruolo<br /><br /> Aggiornamento delle proprietà di ruolo|  
|Gestione di pianificazioni condivise|Creazione di pianificazioni|  
|Gestione della sicurezza del server di report|Lettura dei criteri di sicurezza del sistema<br /><br /> Aggiornamento dei criteri di sicurezza del sistema|  
|Visualizzazione delle proprietà del server di report|Lettura delle proprietà di sistema|  
|Visualizzazione di pianificazioni condivise|Lettura di pianificazioni|  
  
## <a name="see-also"></a>Vedere anche  
 [Concessione di autorizzazioni in un server di report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
