---
title: Prerequisiti per le esercitazioni (Generatore report) | Microsoft Docs
ms.custom: 
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.service: 
ms.component: reporting-services
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
caps.latest.revision: "11"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 63dd6f1be616f092e689f5e1ce7ff2ed12e3ece6
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="prerequisites-for-tutorials-report-builder"></a>Prerequisiti per le esercitazioni (Generatore report)

Per eseguire le esercitazioni di Generatore report è necessario essere in grado di visualizzare e salvare i report impaginati di [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] in un server di report o in un sito di SharePoint integrato in un server di report. Per quanto riguarda i dati, in tutte le esercitazioni vengono usate query letterali che devono essere elaborate da un'istanza di SQL Server.  
  
Se non si dispone dell'accesso a un server di report, a un sito o a un'origine dati, sarà possibile apprendere l'utilizzo di Generatore report attraverso la compilazione di un report offline. Vedere [Esercitazione: Creare un report grafico rapido offline &#40;Generatore report&#41;](../reporting-services/report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md).  

## <a name="requirements"></a>Requisiti

Per completare le esercitazioni di Generatore report, è necessario soddisfare i requisiti seguenti:  
  
-   Accedere al Generatore report. È possibile eseguire Generatore report da un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] o un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] in modalità integrata SharePoint. Nei diversi tipi di server l'unica differenza riguarda il primo passaggio, ovvero l'apertura di Generatore report.  
  
    In un server di report selezionare **Nuovo** > **Report impaginato**.
  
    In un server di report in modalità integrata SharePoint, nella scheda **Documenti** selezionare **Nuovo documento**, quindi selezionare **Report di Generatore report**nell'elenco a discesa. Ad esempio, `http://<servername>/sites/mySite/reports`. L'amministratore di SharePoint deve abilitare la caratteristica Report di Generatore report per ogni raccolta documenti.  
  
-   URL di un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] o di un sito di SharePoint integrato con un server di report di [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] . È necessario disporre dell'autorizzazione per il salvataggio e la visualizzazione di report, origini dati condivise, set di dati condivisi, parti di report e modelli. Per impostazione predefinita, l'URL per un server di report è `http://<servername>/reportserver`. Per impostazione predefinita, l'URL per un sito SharePoint è `http://<sitename>` o `http://<server>/site`.  
  
-   Nome di un'istanza di SQL Server e credenziali sufficienti per l'accesso in sola lettura a qualsiasi database. Per le query del set di dati delle esercitazioni vengono usati dati letterali, ma per restituire i metadati necessari per un set di dati del report ogni query deve essere elaborata da un'istanza di SQL Server. Ad esempio, nella stringa di connessione seguente viene specificato solo un server: `data source=<servername>`. È necessario disporre dell'accesso in lettura al database predefinito assegnato all'utente dall'amministratore di sistema che concede l'autorizzazione per l'accesso al server. È inoltre possibile specificare un database, come illustrato nella stringa di connessione seguente: `data source=<servername>;initial catalog=<database>`.  
  
-   Per l'[Esercitazione: Report mappa (Generatore report)](Tutorial:%20Map%20Report%20\(Report%20Builder\).md), è necessario configurare il server di report affinché supporti le mappe Bing come sfondo. Per altre informazioni, vedere [Pianificare il supporto dei report mappa](http://msdn.microsoft.com/en-us/5ddc97a7-7ee5-475d-bc49-3b814dce7e19).   

-   L'[Esercitazione: Creazione di report drill-through e report principali (Generatore report)](Tutorial:%20Creating%20Drillthrough%20and%20Main%20Reports%20\(Report%20Builder\).md) richiede l'accesso al cubo Contoso Sales. Per altre informazioni, vedere l'esercitazione. 
  
L'amministratore del server di report deve concedere le autorizzazioni necessarie per il server di report, configurare i percorsi delle cartelle [!INCLUDE[ssRSnoversion_md](../includes/ssrsnoversion-md.md)] e configurare le opzioni predefinite di Generatore report. Per altre informazioni, vedere [Installare e disinstallare Generatore report](http://msdn.microsoft.com/library/2c9a5814-17bf-4947-8fb3-6269e7caa416).  

## <a name="next-steps"></a>Passaggi successivi

[Esercitazioni di Generatore report](../reporting-services/report-builder-tutorials.md)  

Altre domande? [Visitare il forum su Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
