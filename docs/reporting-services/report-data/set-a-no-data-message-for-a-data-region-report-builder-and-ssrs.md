---
title: "Impostare una propriet&#224; NoDataMessage per un&#39;area dati (Generatore report e SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# Impostare una propriet&#224; NoDataMessage per un&#39;area dati (Generatore report e SSRS)
  Per specificare il testo da visualizzare nel report visualizzabile al posto di un'area dati senza dati, impostare la proprietà NoRowsMessage di un'area dati tabella, matrice o elenco, la proprietà NoDataMessage di un'area dati del grafico e la proprietà NoDataText per la scala dei colori per una mappa. In fase di esecuzione Elaborazione report esegue la query per ogni set di dati in un report. Tale query non può restituire alcun set di risultati. Per un'area dati associata a un set di dati vuoto, è possibile specificare il testo da visualizzare anziché visualizzare un'area dati vuota. È anche possibile impostare la proprietà NoRowsMessage per un sottoreport quando in nessun set di dati del sottoreport sono presenti dati in fase di esecuzione.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per impostare la proprietà NoRowsMessage di una tabella, una matrice o un elenco  
  
1.  Nella visualizzazione Progettazione fare clic sull'area dati tabella, matrice o elenco o sul sottoreport nell'area di progettazione per selezionare l'elemento desiderato. Nel riquadro Proprietà vengono visualizzate le proprietà relative all'elemento selezionato.  
  
2.  Nel riquadro Proprietà digitare il testo da visualizzare come messaggio nel campo relativo alla proprietà **NoRowsMessage** .  
  
     In alternativa, nell'elenco a discesa fare clic su **Espressione** per aprire la finestra di dialogo **Espressione** e creare un'espressione.  
  
### Per impostare la proprietà NoDataMessage di un grafico  
  
1.  Nella visualizzazione Progettazione fare clic sul grafico nell'area di progettazione per selezionarlo. Nel riquadro Proprietà vengono visualizzate le proprietà relative all'elemento selezionato.  
  
2.  Nel riquadro Proprietà espandere il nodo **NoDataMessage**.  
  
3.  In **Didascalia**digitare il testo da visualizzare come messaggio nel campo della proprietà **NoDataMessage** .  
  
     In alternativa, nell'elenco a discesa fare clic su **Espressione** per aprire la finestra di dialogo **Espressione** e creare un'espressione.  
  
### Per impostare la proprietà NoRowsMessage di un sottoreport  
  
1.  Nella visualizzazione Progettazione fare clic sul sottoreport nell'area di progettazione per selezionarlo. Nel riquadro Proprietà vengono visualizzate le proprietà relative all'elemento selezionato.  
  
2.  Nel riquadro Proprietà digitare il testo da visualizzare come messaggio nel campo relativo alla proprietà **NoRowsMessage** .  
  
     In alternativa, nell'elenco a discesa fare clic su **Espressione** per aprire la finestra di dialogo **Espressione** e creare un'espressione.  
  
### Per impostare la proprietà NoDataText per una scala dei colori per una mappa  
  
1.  Nella visualizzazione Progettazione fare clic sulla scala dei colori nella mappa per selezionarla. Nel riquadro Proprietà vengono visualizzate le proprietà relative all'elemento selezionato.  
  
2.  Nel riquadro Proprietà, in **NoDataText**digitare il testo che si desidera visualizzare come un'etichetta per i colori senza valore di dati.  
  
     In alternativa, nell'elenco a discesa fare clic su **Espressione** per aprire la finestra di dialogo **Espressione** e creare un'espressione.  
  
## Vedere anche  
 [Sottoreport &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)   
 [Tabelle, matrici ed elenchi &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Mappe &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Sottoreport &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/subreports-report-builder-and-ssrs.md)  
  
  