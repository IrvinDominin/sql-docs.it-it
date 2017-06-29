---
title: Impostazioni dell'estensione di recapito di Reporting Services | Documenti Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML Web service [Reporting Services], delivery extension settings
- Report Server Web service, delivery extension settings
- delivery [Reporting Services]
- network share delivery [Reporting Services]
- file share delivery [Reporting Services]
- e-mail [Reporting Services]
- mailing reports [Reporting Services]
- sharing reports
- extensions [Reporting Services], delivery
- mail [Reporting Services]
- Web service [Reporting Services], delivery extension settings
ms.assetid: 68c31a85-261c-4ec4-b8df-1f9842b46f8a
caps.latest.revision: 36
author: sabotta
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 668c3d31af5f287d7d254c2dc666e20a5f6328fa
ms.contentlocale: it-it
ms.lasthandoff: 06/13/2017

---
# <a name="reporting-services-delivery-extension-settings"></a>Impostazioni delle estensioni per il recapito di Reporting Services
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]include un'estensione per il recapito tramite posta elettronica e un'estensione di recapito condivisione file. Il recapito tramite posta elettronica consente di inviare un report a singoli utenti o gruppi tramite posta elettronica. Il recapito tramite condivisione file consente di inviare automaticamente i report visualizzabili a una condivisione nella rete. È possibile utilizzare una delle estensioni per il recapito supportate con sottoscrizioni standard o con sottoscrizioni guidate dai dati. Le impostazioni di recapito specifiche del tipo di estensione per il recapito vengono passate ogni volta che si chiamano i metodi <xref:ReportService2010.ReportingService2010.CreateSubscription%2A>, <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>, <xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> e <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Per recuperare un elenco di impostazioni per il recapito a livello di programmazione, utilizzare il metodo <xref:ReportService2010.ReportingService2010.GetExtensionSettings%2A>.  
  
> [!NOTE]  
>  Per le impostazioni delle estensioni per il recapito viene fatta distinzione tra maiuscole e minuscole.  
  
## <a name="e-mail-delivery-settings"></a>Impostazioni di recapito tramite posta elettronica  
 Nella tabella seguente sono elencate le impostazioni di recapito tramite posta elettronica per le sottoscrizioni che utilizzano la posta elettronica del server di report.  
  
|Impostazione|Valore|  
|-------------|-----------|  
|**A**|Indirizzo di posta elettronica che è presente il **a** riga del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Obbligatorio.|  
|**CC**|Indirizzo di posta elettronica che è presente il **Cc** riga del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Facoltativa.|  
|**CCN**|Indirizzo di posta elettronica che è presente il **Ccn** riga del messaggio di posta elettronica. Se sono presenti più indirizzi di posta elettronica, vengono separati da un punto e virgola. Facoltativa.|  
|**ReplyTo**|Indirizzo di posta elettronica che verrà visualizzato nel **risposta** intestazione del messaggio di posta elettronica. Il valore deve essere un singolo indirizzo di posta elettronica. Facoltativa.|  
|**Includi report**|Valore che indica se includere il report nel recapito tramite posta elettronica. Il valore **true** indica che il report viene recapitato nel corpo del messaggio di posta elettronica.|  
|**RenderFormat**|Nome dell'estensione per il rendering da utilizzare per generare il report visualizzabile. Il nome deve corrispondere a una delle estensioni per il rendering visibili installate nel server di report. Questo valore è obbligatorio se il **Includi report** impostazione è impostata su un valore di **true**.|  
|**Priorità**|Priorità per l'invio del messaggio di posta elettronica. I valori validi sono **bassa**, **normale**, e **elevata**. Il valore predefinito è **normale**.|  
|**Oggetto**|Testo nella riga dell'oggetto del messaggio di posta elettronica.|  
|**Commentoo**|Testo incluso nel corpo del messaggio di posta elettronica.|  
|**IncludeLink**|Valore che indica se includere un collegamento al report nel corpo del messaggio di posta elettronica.|  
  
## <a name="file-share-delivery-settings"></a>Impostazioni di recapito tramite condivisione file  
 Nella tabella seguente sono elencate le impostazioni di recapito tramite condivisione file per le sottoscrizioni.  
  
|Impostazione|Valore|  
|-------------|-----------|  
|**NOME FILE**|Nome del file salvato nel disco.|  
|**FILEEXTN**|Indica se includere un'estensione di file per il report visualizzabile. Il valore può essere **true** o **false**.|  
|**PERCORSO**|Percorso della cartella o percorso della condivisione file UNC in cui salvare il report.|  
|**RENDER_FORMAT**|Formato del report da salvare nel disco.|  
|**NOME UTENTE**|Nome utente necessario per accedere al disco o alla risorsa di rete.|  
|**PASSWORD**|Password necessaria per accedere al disco o alla risorsa di rete.|  
|**WRITEMODE**|Modalità di scrittura da utilizzare per accedere al disco. I valori validi sono **Nessuno**, **sovrascrittura**, e **AutoIncrement**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico &#40; SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)   
 [Creazione di applicazioni mediante il servizio Web e .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  