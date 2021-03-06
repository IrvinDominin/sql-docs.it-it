---
title: Finestra di dialogo per la conversione degli elementi del report personalizzati (Generatore report) | Microsoft Docs
ms.date: 08/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-builder
ms.topic: reference
f1_keywords:
- "10008"
helpviewer_keywords:
- CRI
- custom report items
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: dc06ca21a1fa953db107b1c166bc9d05cebd67f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832299"
---
# <a name="convert-cri-dialog-box-report-builder"></a>Finestra di dialogo per la conversione degli elementi del report personalizzati (Generatore report)
  In questo report sono contenuti elementi del report personalizzati con funzionalità non supportate. Gli elementi del report personalizzati sono estensioni del linguaggio RDL (Report Definition Language) che supportano gli oggetti personalizzati che consentono di visualizzare i dati in un report e contengono componenti della fase di progettazione e della fase di esecuzione resi disponibili dai fornitori di software di terze parti.  
  
> [!NOTE]  
>  La scelta di supportare elementi del report personalizzati in un server di report è una decisione che spetta all'amministratore del sistema. Per visualizzare questi elementi, è necessario che i relativi componenti siano installati nel client di creazione dei report, in modo da poter visualizzare in anteprima un report, e nel server di report per visualizzare un report pubblicato o caricato.  
  
 Alcuni elementi del report personalizzati possono essere convertiti in elementi del report con il nuovo formato di definizione. Quando si apre il report, viene richiesto se si desidera eseguire l'aggiornamento. Per decidere se convertire gli elementi personalizzati inclusi nel report, utilizzare le informazioni seguenti:  
  
-   **Sì** Scegliere **Sì** per convertire tutti gli elementi del report personalizzati nel report, laddove possibile. Le funzionalità non supportate negli elementi del report personalizzati non possono essere aggiornate e vengono rimosse dal file di definizione del report. Per l'elenco di funzionalità non supportate, vedere [Aggiornare i report](../../reporting-services/install-windows/upgrade-reports.md). Durante la visualizzazione del report è possibile notare le differenze nella visualizzazione degli elementi del report personalizzati.  
  
-   **No** Scegliere **No** se non si desidera convertire gli elementi del report personalizzati nel report. Gli elementi non possono essere visualizzati da Elaborazione report nella versione corrente. Se l'amministratore del sistema prevede di installare una nuova versione dell'elemento del report personalizzato del fornitore di software di terze parti compatibile con il nuovo formato di definizione del report, è necessario scegliere **No**. Fino a quando non diventano disponibili nuove versioni, gli elementi del report personalizzati vengono visualizzati nel report come una casella di testo vuota con una X rossa.  
  
 In entrambi i casi, il report viene aggiornato al nuovo formato di definizione del report e una copia di backup del report originale viene salvata come *\<Nome report>* `-` Backup.rdl. Se il report viene salvato nello strumento per la creazione dei report, in pratica viene salvato il report aggiornato nel nuovo formato di definizione del report. Se si pubblica il report, esso viene prima salvato nel computer, quindi pubblicato nel server di report. La versione aggiornata del report viene pubblicata nel server di report.  
  
 Se non si salva il report, il report originale resta immutato. Non è tuttavia possibile modificare tale report in una versione successiva di [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] o in un ambiente di creazione di report in cui viene utilizzato questo formato di definizione del report. È possibile continuare a eseguire la versione originale del report caricandolo in un server di report [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] o versioni successive tramite Gestione report. Per altre informazioni, vedere [Caricare un file o un report &#40;Gestione report&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md).  
  
 Per i report che vengono caricati anziché pubblicati in un server di report, Elaborazione report determina se è possibile aggiornarli al primo utilizzo. I report non aggiornabili vengono elaborati in modalità di compatibilità con le versioni precedenti e continuano a essere visualizzati come nella versione precedente di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per altre informazioni, vedere [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md).  
  
 Per identificare il formato di definizione del report corrente per un report, per un server di report o per l'ambiente di creazione dei report, vedere [Individuare la versione dello schema di definizione del report &#40;SSRS&#41;](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md).  

  
  
