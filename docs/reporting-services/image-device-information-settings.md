---
title: "Impostazioni relative alle informazioni sul dispositivo di acquisizione immagini | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "images [Reporting Services], rendering"
  - "impostazioni relative alle informazioni sul dispositivo [Reporting Services], rendering IMAGE"
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
caps.latest.revision: 39
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 39
---
# Impostazioni relative alle informazioni sul dispositivo di acquisizione immagini
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato IMAGE.  
  
|Impostazione|Value|  
|-------------|-----------|  
|**Colonne**|Numero di colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**ColumnSpacing**|Spaziatura delle colonne da impostare per il report. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**DpiX**|Risoluzione orizzontale dell'immagine di output. Il valore predefinito è **96**. Si applica ai formati di output **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**DpiY**|Risoluzione verticale dell'immagine di output. Il valore predefinito è **96**. Si applica ai formati di output **BMP**, **GIF**, **PNG**e **TIFF** .|  
|**EndPage**|Ultima pagina del report di cui eseguire il rendering. Il valore predefinito è il valore di **StartPage**.|  
|**MarginBottom**|Valore in pollici del margine inferiore da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginLeft**|Valore in pollici del margine sinistro da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginRight**|Valore in pollici del margine destro da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**MarginTop**|Valore in pollici del margine superiore da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **1in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**OutputFormat**|Uno dei formati di output supportati di [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]): **BMP**, **EMF**, **GIF**, **JPEG**, **PNG**, o **TIFF**.|  
|**PageHeight**|Altezza di pagina in pollici da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **11in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PageWidth**|Larghezza di pagina in pollici da impostare per il report. È necessario includere un numero intero o un valore decimale seguito da "in", ad esempio **8.5in**. Questo valore ha la priorità sulle impostazioni originali del report.|  
|**PrintDpiX**|Risoluzione orizzontale dell'immagine di output. Il valore predefinito è **300**. Si applica al formato di output Enhanced MetaFile (**EMF**).|  
|**PrintDpiY**|Risoluzione verticale dell'immagine di output. Il valore predefinito è **300**. Si applica al formato di output Enhanced MetaFile (**EMF**).|  
|**StartPage**|Prima pagina del report di cui eseguire il rendering. Il valore **0** indica che viene eseguito il rendering di tutte le pagine. Il valore predefinito è **1**.|  
  
## Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.config.](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  