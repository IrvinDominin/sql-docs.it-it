---
title: "Aggiunta di grafici sparkline e barre dei dati (Generatore report e SSRS) | Microsoft Docs"
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
ms.assetid: 0b297c2e-d48b-41b0-aabd-29680cdcdb05
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Aggiunta di grafici sparkline e barre dei dati (Generatore report e SSRS)
  I grafici sparkline e le barre dei dati sono grafici di riserva di piccole dimensioni contenenti numerose informazioni poco dettagliate. Per altre informazioni, vedere [Grafici sparkline e barre dei dati &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/sparklines-and-data-bars-report-builder-and-ssrs.md).  
  
 Nei report impaginati di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] i grafici sparkline e le barre dei dati vengono posizionati generalmente nelle celle di una tabella o di una matrice. In ogni grafico sparkline di solito viene visualizzata una sola serie. Le barre dei dati possono includere più punti dati. L'influenza dei grafici sparkline e delle barre dei dati deriva dal ripetersi delle informazioni relative alla serie per ogni riga della tabella o matrice.  
  
## Per aggiungere grafici sparkline o barre dei dati a una tabella o a una matrice  
  
1.  Se questa operazione non è già stata eseguita, creare una [tabella](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) o una [matrice](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md) con i dati che si vuole visualizzare.  
  
2.  Inserire una colonna nella tabella o nella matrice. Per altre informazioni, vedere [Inserire o eliminare una colonna &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Scegliere **Grafico sparkline** o **Barra dei dati** nella scheda **Inserisci**e fare clic in una cella della nuova colonna.  
  
    > [!NOTE]  
    >  Non è possibile posizionare grafici sparkline in un gruppo di dettagli in una tabella. Devono essere inseriti in una cella associata a un gruppo.  
  
4.  Nella finestra di dialogo **Modifica tipo di grafico sparkline/barra dei dati** fare clic sul tipo di grafico sparkline o barra dei dati desiderato e quindi scegliere **OK**.  
  
5.  Scegliere il grafico sparkline o la barra dei dati.  
  
     Viene visualizzato il riquadro **Dati grafico** .  
  
6.  Nell'area **Valori** fare clic sul segno più (**+**) di **Aggiungi campi** e selezionare il campo contenente i valori che si vuole inserire in formato grafico.  
  
7.  Nell'area **Gruppi di categorie** fare clic sul segno più (**+**) di **Aggiungi campi** e selezionare il campo contenente i valori in base ai quali si vuole raggruppare.  
  
     In genere per i grafici sparkline e per le barre dei dati, non viene aggiunto un campo all'area **Gruppo serie** in quanto si desidera una sola serie per ogni riga.  
  
## Vedere anche  
 [Grafici &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [Allineare i dati in un grafico di una tabella o matrice &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/align-the-data-in-a-chart-in-a-table-or-matrix-report-builder-and-ssrs.md)  
  
  