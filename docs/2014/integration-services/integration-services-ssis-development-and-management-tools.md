---
title: Integration Services (SSIS) e ambienti Studio | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- studio environments [Integration Services]
- tools [Integration Services], Business Intelligence Development Studio
- Business Intelligence Development Studio, Integration Services in
- SQL Server Management Studio [Integration Services]
- SSIS, studio environments
- SQL Server Integration Services, studio environments
- tools [Integration Services], SQL Server Management Studio
ms.assetid: 4eb73e65-d9f3-4ac6-a408-abfa85afc537
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aef82e8a4e60015c8b0ffbf41ab7ec5abf98ed83
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211981"
---
# <a name="integration-services-ssis-and-studio-environments"></a>Integration Services (SSIS) e ambienti Studio
  In[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sono inclusi due strumenti per l'utilizzo di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]:  
  
-   [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] per lo sviluppo di pacchetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] richiesti da una soluzione aziendale. In[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] è disponibile il progetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in cui è possibile creare pacchetti.  
  
-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per la gestione dei pacchetti in un ambiente di produzione.  
  
## <a name="sql-server-data-tools"></a>SQL Server Data Tools  
 In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]è possibile effettuare le attività seguenti:  
  
-   Eseguire l'Importazione/Esportazione guidata di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] per creare pacchetti di base per la copia dei dati da un'origine a una destinazione.  
  
-   Creare pacchetti che includono complessi flussi di controllo, flussi di dati, logica guidata dagli eventi e funzionalità di registrazione.  
  
-   Testare ed eseguire il debug dei pacchetti usando le funzionalità di monitoraggio e risoluzione dei problemi di Progettazione [!INCLUDE[ssIS](../includes/ssis-md.md)] e le funzionalità di debug di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
-   Creare configurazioni che aggiornano le proprietà e gli oggetti dei pacchetti in fase di esecuzione.  
  
-   Creare un'utilità di distribuzione tramite cui installare i pacchetti e le relative dipendenze in altri computer.  
  
-   Salvare copie dei pacchetti nel database msdb di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], nell'archivio pacchetti di [!INCLUDE[ssIS](../includes/ssis-md.md)] e nel file system.  
  
 Per altre informazioni su [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], vedere [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686.aspx).  
  
## <a name="sql-server-management-studio"></a>SQL Server Management Studio  
 In[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] è disponibile il servizio [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] che consente di gestire pacchetti, monitorare i pacchetti in esecuzione e determinare l'impatto e la derivazione dei dati per gli oggetti di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] e [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]è possibile effettuare le attività seguenti:  
  
-   Creare cartelle per organizzare i pacchetti in modo utile all'organizzazione.  
  
-   Eseguire pacchetti archiviati nel computer locale tramite l'Utilità di esecuzione pacchetti.  
  
-   Eseguire l'Utilità di esecuzione pacchetti per generare una riga di comando da usare per l'esecuzione dell'utilità del prompt dei comandi **dtexec** (dtexec.exe).  
  
-   Importare ed esportare pacchetti da e verso il database msdb di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], l'archivio pacchetti [!INCLUDE[ssIS](../includes/ssis-md.md)] e il file system.  
  
