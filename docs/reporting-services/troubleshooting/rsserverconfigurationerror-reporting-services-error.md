---
title: rsServerConfigurationError - Errore di Reporting Services | Microsoft Docs
ms.custom: 
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: troubleshooting
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
caps.latest.revision: "12"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: a9be3ec02215fec315f9972726ca0ea15e20ffd1
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Errore di Reporting Services
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|rsServerConfiguration|  
|Origine evento|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Componente|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Testo del messaggio|Il server di report ha rilevato un errore di configurazione.|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore è generico e si verifica quando le impostazioni di configurazione del server di report o di uno strumento di creazione dei report non sono valide. All'errore è generalmente associato un secondo messaggio che indica la causa effettiva dell'errore stesso.  
  
 Nell'elenco seguente vengono riepilogate le possibili cause:  
  
-   Il file RSReportServer.config o RSReportDesigner.config non può essere trovato o letto.  
  
-   Gli elementi XML nel file di configurazione mancano o non sono validi.  
  
-   I valori per uno o più elementi XML mancano o non sono validi.  
  
-   Le impostazioni del Registro di sistema non sono valide.  
  
## <a name="user-action"></a>Azione dell'utente  
 Se questo errore inizia a verificarsi dopo che il file di configurazione è stato modificato manualmente, rimuovere le modifiche e immettere il valore precedente o ripristinare una versione precedente se è disponibile un backup.  
  
 Per rivedere informazioni aggiuntive sul messaggio di errore associate all'errore **rsServerConfiguration**, rivedere i file di log di traccia del server di report, disponibili in \Microsoft SQL Server\MSRS12.\<nomeistanza >\Reporting Services\LogFiles. Per altre informazioni, vedere [File di log e origini di Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Solo interno  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione di Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Modificare un file di configurazione di Reporting Services &#40;RSreportserver.config&#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
