---
title: "Impostazioni relative alle informazioni sul dispositivo XML | Microsoft Docs"
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
  - "XML [Reporting Services], rendering"
  - "impostazioni relative alle informazioni sul dispositivo [Reporting Services], rendering PDF"
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# Impostazioni relative alle informazioni sul dispositivo XML
  Nella tabella seguente sono elencate le impostazioni relative alle informazioni sul dispositivo per il rendering nel formato XML.  
  
|Impostazione|Valori|Dettagli|  
|-------------|------------|-------------|  
|**XSLT**|Percorso nello spazio dei nomi del server di report di una trasformazione XSLT da applicare al file XML, ad esempio **/Transforms/myxslt**.|Il file con estensione xsl deve essere una risorsa pubblicata nel server di report ed è necessario accedervi tramite un percorso di un elemento del server di report. Il valore di questa impostazione viene applicato dopo qualsiasi trasformazione XSLT specificata nel report. Se viene applicata l'impostazione **XSLT** , l'impostazione **OmitSchema** viene ignorata.|  
|**MIMEType**|Tipo MIME (Multipurpose Internet Mail Extensions) del file XML.||  
|**UseFormattedValues**|**true**<br /><br /> **false**|Indica se eseguire il rendering del valore formattato di una casella di testo quando vengono generati i dati XML.<br /><br /> Il valore false indica che viene utilizzato il valore sottostante della casella di testo.|  
|**Indented**|**true**<br /><br /> **false**|Indica se generare codice XML con rientro. Il valore predefinito **false** genera codice XML compresso senza rientro.|  
|**OmitNamespace**|**true**<br /><br /> **false**|Indica se omettere lo spazio dei nomi predefinito dai dati XML.<br /><br /> Se true, i dati XML non specificano uno spazio dei nomi predefinito.<br /><br /> Se false, i dati XML specificano uno spazio dei nomi predefinito con il valore della proprietà DataSchema del report. L'impostazione predefinita della proprietà DataSchema corrisponde al nome del report.<br /><br /> Il valore predefinito è **false**.|  
|**OmitSchema**|**true**<br /><br /> **false**|Indica se omettere la posizione dello schema dai dati XML. Il percorso è l'attributo SchemaLocation.<br /><br /> Il valore predefinito di OmitSchema dipende dal valore di OmitNamespace:<br /><br /> Se OmitNamespace = False, OmitSchema = **False** per impostazione predefinita. L'utente può eseguire l'override dell'impostazione predefinita impostando OmitSchema = True.<br /><br /> Se OmitNamespace = True, OmitSchema funzionerà come **True** indipendentemente dal valore configurato in modo esplicito per OmitSchema.|  
|**Codifica**|Il nome IANA (Internet Assigned Numbers Authority) di una codifica dei caratteri supportata da .NET Framework.|Il valore predefinito è **UTF-8**. Esempi di altri valori includono ASCII, UTF-7 e UTF-16.|  
|**FileExtension**|Estensione di file da utilizzare per il file generato.||  
|**Schema**|Il valore **true** indica che viene eseguito il rendering di un elemento XML Schema. Il valore predefinito è **false**.|Indica se viene eseguito il rendering di XSD (XML Schema Definition) o dei dati XML effettivi.|  
  
## Vedere anche  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Passaggio delle impostazioni relative alle informazioni sul dispositivo alle estensioni per il rendering](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Personalizzare i parametri di estensione per il rendering in RSReportServer.config.](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Guida di riferimento tecnico &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  