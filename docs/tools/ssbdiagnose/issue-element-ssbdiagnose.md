---
title: "Elemento Issue (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "elemento Issue"
  - "formato file di output XML [ssbdiagnose], elemento Issue"
  - "ssbdiagnose"
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Elemento Issue (ssbdiagnose)
  Segnala un problema rilevato dall'utilità **ssbdiagnose** . Nel file di output XML di **ssbdiagnose** è presente un solo elemento Issue per ogni problema segnalato.  
  
## Sintassi  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## Attributi elemento  
  
|Attribute|Descrizione|  
|---------------|-----------------|  
|**tipo**|Identifica la categoria del problema segnalato dall'elemento Issue:<br /><br /> **"Diagnosis"** segnala un problema di configurazione rilevato quando si analizza una configurazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)] .<br /><br /> **"Problem"** segnala un problema che ha impedito a **ssbdiagnose** di completare l'analisi. Correggere il problema ed eseguire di nuovo **ssbdiagnose**.<br /><br /> **"Event"** segnala un evento di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] rilevato quando si esegue un controllo **-RUNTIME**. Gli eventi vengono segnalati solo se è specificata l'opzione **-SHOWEVENTS**.|  
|**codice**|Identifica il numero di errore relativo al messaggio.|  
|**server**|Identifica l'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] in cui è stato rilevato il problema. Se il problema si è verificato in un'istanza predefinita, l'attributo server è costituito solo del nome del computer, mentre se il problema si è verificato in un'istanza denominata, il formato dell'attributo server è NomeComputer\NomeIstanza.|  
|**database**|Identifica il nome dell'istanza del database in cui è stato rilevato il problema.|  
|**oggetto**|Identifica il nome dell'istanza dell'oggetto in cui è stato rilevato il problema. Se il problema si è verificato a livello di istanza o di database, l'attributo dell'oggetto ripete il nome dell'istanza o del database.|  
  
## Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|**Tipo di dati e lunghezza**|**string**, lunghezza illimitata.|  
|**Valore**|Restituisce il testo del messaggio di errore.|  
|**Occorrenza**|Una volta per ogni errore segnalato.|  
  
## Relazioni elemento  
  
|Relazione|Elementi|  
|------------------|--------------|  
|**Elemento padre**|[Elemento DiagnosticInformation &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**Elementi figlio**|Nessuno|  
  
## Esempio  
 Questo elemento segnala un errore 1102 per un database che non dispone di una chiave master, in cui l'errore è stato rilevato quando è stata analizzata una configurazione di [!INCLUDE[ssSB](../../includes/sssb-md.md)].  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## Vedere anche  
 [Utilità ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  