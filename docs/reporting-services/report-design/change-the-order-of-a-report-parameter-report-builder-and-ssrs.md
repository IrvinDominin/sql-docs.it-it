---
title: "Modificare l&#39;ordine di un parametro del report (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# Modificare l&#39;ordine di un parametro del report (Generatore report e SSRS)
  Modificare l'ordine dei parametri del report quando un parametro dipendente è elencato prima del parametro da cui dipende. L'ordine dei parametri è importante quando sono presenti parametri di propagazione o quando si desidera indicare il valore predefinito di un parametro prima che gli utenti scelgano i valori per altri parametri. Un parametro dipendente del report contiene un riferimento, nella query dei valori predefiniti o in quella dei valori validi, a un parametro di query che punta a un parametro del report successivo nell'elenco dei parametri del riquadro dei **dati del report** .  
  
 L'ordine con cui i parametri vengono visualizzati nella barra degli strumenti del visualizzatore di report quando viene eseguito il report è determinato dall'ordine dei parametri nel riquadro dei **dati del report** e dalla posizione dei parametri nel riquadro dei parametri personalizzati. Per altre informazioni, vedere [Personalizzare il riquadro dei parametri in un report &#40;Generatore report&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Per modificare l'ordine dei parametri del report  
  
È possibile modificare l'ordine dei parametri del report eseguendo una delle operazioni seguenti:  
  
-   Fare clic su un parametro nel riquadro dei **dati del report** e usare i pulsanti freccia Su e freccia Giù per spostare il parametro in una posizione superiore o inferiore nell'elenco, come mostrato nell'immagine seguente.  Quando si modifica l'ordine del parametro del riquadro dei **dati del report** , viene modificata la posizione del parametro nel riquadro.  
  
     ![Change the order of the parameters in the Report Data pane](../../reporting-services/report-design/media/ssrs-changeorderofparameters-reportdata.png "Change the order of the parameters in the Report Data pane")  
  
-   Nel riquadro dei parametri trascinare il parametro in una nuova colonna o riga del riquadro. Quando si modifica la posizione del parametro nel riquadro, viene modificato l'ordine del parametro nel riquadro dei **dati del report** . Per altre informazioni sullo spostamento dei parametri, vedere [Personalizzare il riquadro dei parametri in un report &#40;Generatore report&#41;](../../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md).  
  
## Vedere anche  
 [Parametri report &#40;Generatore report e Progettazione report&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [Guida di Generatore report per finestre di dialogo, riquadri e procedure guidate](http://msdn.microsoft.com/it-it/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Aggiungere parametri di propagazione a un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiungere un parametro al report &#40;Generatore report&#41;](../../reporting-services/tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Aggiungere filtri per set di dati, aree dati e gruppi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add dataset filters, data region filters, and group filters.md)   
 [Riferimenti alla raccolta dei parametri &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)  
  
  