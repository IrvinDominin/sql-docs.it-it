---
title: "Propriet&#224; della cache dei file | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Income - proprietà"
  - "InitialBonus - proprietà"
  - "PercentScanPerPrice - proprietà"
  - "FileStore - proprietà"
  - "BackgroundTrimCost - proprietà"
  - "Tax - proprietà"
  - "PerformanceTrace - proprietà"
  - "MinimumBalance - proprietà"
  - "UnbufferedThreshold - proprietà"
  - "BackgroundTrimAmount - proprietà"
  - "MaximumBalance - proprietà"
  - "MemoryLimitMin - proprietà"
  - "MemoryLimit - proprietà"
ms.assetid: 580cf0aa-7425-4d48-aa8d-128f5b488fcd
caps.latest.revision: 19
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Propriet&#224; della cache dei file
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supporta le proprietà della cache dei file del server elencate nelle tabelle seguenti. Si tratta di proprietà avanzate, che vanno modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Per altre informazioni sulle proprietà aggiuntive del server e sulla relativa impostazione, vedere [Proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Si applica a:** modalità server multidimensionale e tabulare  
  
## Proprietà  
 **MemoryLimit**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryLimitMin**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PercentScanPerPrice**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **PerformanceTrace**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **RandomFileAccessMode**  
 Proprietà booleana che indica se l'accesso ai file del database e ai file memorizzati nella cache viene eseguito nella modalità di accesso file causale. Questa proprietà è disattivata per impostazione predefinita. Per impostazione predefinita, in Analysis Services non viene impostato il flag di accesso ai file causale quando si aprono file di dati della partizione per l'accesso in lettura.  
  
 Nei sistemi di fascia alta, in particolare quelli che dispongono di grandi risorse di memoria e più nodi NUMA, l'utilizzo dell'accesso ai file causale può essere vantaggioso. Nella modalità di accesso causale, le operazioni di mapping delle pagine che leggono dati dal disco nella cache del file system vengono ignorate da Windows, abbassando pertanto la contesa sulla cache.  
  
 Sarà necessario eseguire test di confronto per determinare se le prestazioni di esecuzione delle query vengono migliorate a seguito della modifica di questa proprietà. Per le procedure consigliate su come eseguire test di confronto, inclusi la cancellazione della cache e il modo di evitare errori comuni, vedere la pagina relativa alla [Guida operativa di SQL Server 2008 R2 Analysis Services](http://go.microsoft.com/fwlink/?LinkID=225539). Per altre informazioni sui compromessi di uso di questa proprietà, vedere [http://support.microsoft.com/kb/2549369](http://support.microsoft.com/kb/2549369).  
  
 Per visualizzare o modificare questa proprietà in Management Studio, abilitare l'elenco delle proprietà avanzate nella pagina delle proprietà del server. Per cambiare la proprietà, è anche possibile utilizzare il file msmdsrv.ini. Dopo aver impostato questa proprietà, si consiglia di riavviare il server; in caso contrario, l'accesso ai file già aperti continuerà a essere eseguito nella modalità precedente.  
  
 **UnbufferedThreshold**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Categoria Memory Model  
 **MemoryModel\Tax**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\Income**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MaximumBalance**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\MinimumBalance**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 **MemoryModel\InitialBonus**  
 Proprietà avanzata che deve essere modificata solo sotto la supervisione del servizio di supporto tecnico [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## Vedere anche  
 [proprietà server in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Determinare la modalità server di un'istanza di Analysis Services](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  