---
title: Aggiungere un'immagine con associazione a dati (Generatore report e SSRS) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
caps.latest.revision: "8"
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 4199db348aa0c6537e33471e6e5912cddba7d685
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Aggiungere un'immagine con associazione a dati (Generatore report e SSRS)
  Un report può includere un riferimento a un'immagine archiviata in un database. Tale immagine è nota come *immagine con associazione a dati*. Le immagini visualizzate insieme ai nomi di prodotti in un catalogo sono esempi di immagini con associazione a dati.  
  
 Per aggiungere un'immagine con associazione a dati a un'intestazione di pagina o un piè di pagina, è necessario eseguire ulteriori operazioni. Per altre informazioni, vedere [Intestazioni di pagina e piè di pagina &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Per aggiungere un'immagine con associazione a dati  
  
1.  Nella visualizzazione di progettazione report creare una tabella con una connessione all'origine dati e un set di dati con un campo contenente dati immagine binari. Per altre informazioni, vedere [Tabelle &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md).  
  
2.  Inserire una colonna nella tabella. Per altre informazioni, vedere [Inserire o eliminare una colonna &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Scegliere **Immagine** dal menu **Inserisci**, quindi fare clic nella riga di dati della nuova colonna.  
  
4.  Nella pagina Generale della finestra di dialogo **Proprietà immagine** digitare un nome nella casella di testo **Nome** o accettare il nome predefinito.  
  
5.  (Facoltativo) Nella casella di testo **Descrizione comando** digitare il testo da visualizzare quando il puntatore del mouse viene posizionato nel report sottoposto a rendering per HTML.  
  
6.  In **Selezionare l'origine dell'immagine**selezionare **Database**.  
  
7.  In **Utilizzare questo campo**selezionare il campo che contiene le immagini nel report.  
  
8.  In **Utilizzare questo tipo MIME**selezionare il tipo MIME, o il formato di file, dell'immagine, ad esempio bmp.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Nell'area di progettazione del report verrà visualizzato un segnaposto dell'immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [Immagini &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/images-report-builder-and-ssrs.md)   
 [Incorporare un'immagine in un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Aggiungere un'immagine esterna &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-an-external-image-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà immagine, Generale &#40;Generatore report e SSRS&#41;](http://msdn.microsoft.com/library/c2218b93-f7fe-46ef-995f-d7dadf9752ec)  
  
  
