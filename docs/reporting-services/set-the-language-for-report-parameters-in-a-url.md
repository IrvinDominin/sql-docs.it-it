---
title: "Impostare la lingua per i parametri del report in un URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modifica delle impostazioni della lingua del report"
  - "server di report [Reporting Services], impostazioni della lingua"
  - "lingue [Reporting Services]"
  - "accesso con URL [Reporting Services], override della lingua"
  - "considerazioni sulle funzionalità internazionali [Reporting Services]"
  - "considerazioni globali [Reporting Services]"
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
caps.latest.revision: 29
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 29
---
# Impostare la lingua per i parametri del report in un URL
  Il parametro di accesso con URL *rs:ParameterLanguage* consente di risolvere un problema di interpretazione dei parametri del report con distinzione delle impostazioni cultura, come date, ore, valuta e numeri, in base alla lingua del browser. Con *rs:ParameterLanguage* l'URL viene ora interpretato in modo indipendente dal browser. Se, ad esempio, per il server di report sono definite le impostazioni internazionali per il tedesco, ma un utente accede a un report tramite un URL utilizzando un browser che è impostato su Inglese (Stati Uniti), i valori dei parametri passati a un server di report vengono interpretati in modo errato.  
  
 Considerare il seguente URL che rimanda a un report:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 In questo caso il server, in esecuzione in base alle impostazioni cultura "de-de", genera un URL tramite una sottoscrizione di posta elettronica o un collegamento ipertestuale. Il collegamento ipertestuale indica che i parametri del report devono essere interpretati con una data di inizio del 4 ottobre 2008 e una data di fine dell'11 ottobre 2008, in base agli standard di data/ora per il tedesco. Se tuttavia un utente accede all'URL tramite un browser impostato su "en-us", il server interpreta i valori come il 10 aprile 2008 e  10 novembre 2008, in base agli standard di data/ora per l'inglese degli Stati Uniti. Per risolvere il problema, è possibile usare *rs:ParameterLanguage* per eseguire l'override della lingua del browser per l'interpretazione dei parametri:  
  
```  
http://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 Oltre ai valori **true** e **false**, per il parametro di accesso con URL *rc:Parameters* è ora possibile passare il valore **Collapsed**. Quando si usa *rc:Parameters*=**Collapsed** in un URL, l'area dei messaggi di richiesta dei parametri del visualizzatore HTML viene compressa e non è più visualizzata, ma l'utente può comunque scegliere di visualizzarla. Il valore **false** consente di rimuovere l'area dei messaggi di richiesta dei parametri dalla barra degli strumenti del visualizzatore HTML, in modo che non sia più disponibile per l'utente finale.  
  
## Vedere anche  
 [Accesso con URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Riferimento ai parametri di accesso con URL](../reporting-services/url-access-parameter-reference.md)  
  
  