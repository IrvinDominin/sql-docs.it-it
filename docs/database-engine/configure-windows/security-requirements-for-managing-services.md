---
title: "Requisiti di sicurezza per la gestione dei servizi | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizio SQL Server Agent, sicurezza"
  - "servizi [SQL Server], sicurezza"
  - "servizi SQL Server, sicurezza"
  - "provider WMI [SQL Server]"
  - "configurazione server [SQL Server]"
  - "sicurezza [SQL Server], servizi"
  - "servizi [SQL Server], WMI"
ms.assetid: 1874a317-ddb2-425d-98d9-b53e1be6fc6a
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Requisiti di sicurezza per la gestione dei servizi
  Per gestire i servizi [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, usare Gestione configurazione SQL Server o [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Gestire i servizi su server del cluster tramite Amministrazione cluster.  
  
 Per gestire il servizio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e impostare le opzioni di configurazione del server, è necessario essere membri del ruolo predefinito del server **serveradmin** o **sysadmin**. I membri del gruppo **Administrators** di Windows possono avviare e arrestare i servizi e configurare le opzioni server disponibili in Windows.  
  
> [!NOTE]  
>  Per un corretto funzionamento, è necessario che gli account utilizzati per i servizi siano configurati con dominio, file system e autorizzazioni per il Registro di sistema appropriati. Per informazioni sulle autorizzazioni necessarie, vedere [Configurare account di servizio e autorizzazioni di Windows](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
## Strumentazione gestione Windows (WMI)  
 Per visualizzare e modificare alcune delle proprietà del server in Gestione configurazione SQL Server e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] viene utilizzato il servizio Strumentazione gestione Windows (WMI). Per gestire i servizi e ottenere informazioni sullo stato dei servizi, è necessario che l'utente sia autorizzato ad accedere all'oggetto WMI. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] WMI viene utilizzato dalle proprietà del server seguenti:  
  
-   Avvio automatico servizi  
  
-   Parametri di avvio  
  
-   Sicurezza  
  
-   Impostazioni varie  
  
## Attività correlate  
 [Configurazione di WMI per mostrare lo stato del server in Strumenti SQL Server](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
## Contenuto correlato  
 [Concetti relativi al provider WMI per Gestione configurazione](../Topic/WMI%20Provider%20for%20Configuration%20Management%20Concepts.md)  
  
  