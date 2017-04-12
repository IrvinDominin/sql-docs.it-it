---
title: "Incorporare un&#39;immagine in un report (Generatore report e SSRS) | Microsoft Docs"
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
f1_keywords: 
  - "sql13.rtp.rptdesigner.embeddedimages.f1"
  - "10060"
ms.assetid: aed77345-5eeb-41f0-96c9-db6b4a11ec6f
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Incorporare un&#39;immagine in un report (Generatore report e SSRS)
  Un report può includere un'immagine incorporata. L'incorporamento di un'immagine assicura che l'immagine sia sempre disponibile per il report, ma può influire sulle dimensioni della definizione del report, ovvero il file che definisce il report. Le immagini incorporate in un report sono elencate nel riquadro dei dati del report.  
  
 È necessario incorporare un'immagine nella definizione del report prima di aggiungerla all'area di progettazione. Per altre informazioni, vedere [Aggiungere un'immagine di sfondo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-background-image-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Per incorporare un'immagine in un report  
  
1.  Nella visualizzazione di progettazione report fare clic su **Immagine** nella scheda **Inserisci**.  
  
2.  Nell'area di progettazione fare clic su una casella, quindi trascinarla fino a raggiungere le dimensioni desiderate per l'immagine.  
  
3.  Nella pagina **Generale** della finestra di dialogo **Proprietà immagine** digitare un nome nella casella di testo **Nome** o accettare il nome predefinito.  
  
4.  (Facoltativo) Nella casella di testo **Descrizione comando** digitare il testo da visualizzare quando il puntatore del mouse viene posizionato sull'immagine nel report visualizzabile.  
  
5.  In **Selezionare l'origine dell'immagine** selezionare **Incorporata**.  
  
6.  Fare clic sul pulsante **Importa** accanto alla casella di testo **Utilizzare questa immagine**.  
  
7.  In **Tipo file**selezionare il tipo di file di immagine, passare al file e quindi fare clic su **Apri**.  
  
8.  Nella finestra di dialogo **Proprietà immagine** scegliere **OK**.  
  
     L'immagine viene visualizzata nella casella disegnata nell'area di progettazione mentre il file viene visualizzato sotto la cartella Immagini nel riquadro dei dati del report.  
  
    > [!NOTE]  
    >  Il tipo MIME, ad esempio bmp, viene derivato automaticamente al momento dell'importazione dell'immagine. Per modificare il tipo MIME, vedere la procedura seguente.  
  
### (Facoltativo) Per modificare il tipo MIME di un'immagine importata  
  
1.  Aprire il report in visualizzazione Progettazione.  
  
2.  Selezionare l'immagine nell'area di progettazione. Nel riquadro **Proprietà** verranno visualizzate le proprietà dell'immagine.  
  
    > [!NOTE]  
    >  Se il riquadro Proprietà non è visualizzato, fare clic su **Proprietà** nella scheda **Visualizza**.  
  
3.  Fare clic nella casella di testo accanto alla proprietà **MIMEType** e selezionare un nuovo tipo MIME nell'elenco a discesa.  
  
## Vedere anche  
 [Immagini &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Aggiungere un'immagine di sfondo &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-a-data-bound-image-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà immagine, Generale &#40;Generatore report e SSRS&#41;](../Topic/Image%20Properties%20Dialog%20Box,%20General%20\(Report%20Builder%20and%20SSRS\).md)  
  
  