---
title: Aggiungere un'immagine con associazione a dati (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: df4c38d4-bfcc-41c4-aa6d-952ca6fd7a2e
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c66e586e94dd1b86dbd079e692b0f7a8b72b1c55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37230741"
---
# <a name="add-a-data-bound-image-report-builder-and-ssrs"></a>Aggiungere un'immagine con associazione a dati (Generatore report e SSRS)
  Un report può includere un riferimento a un'immagine archiviata in un database. Tale immagine è nota come *immagine con associazione a dati*. Le immagini visualizzate insieme ai nomi di prodotti in un catalogo sono esempi di immagini con associazione a dati.  
  
 Per aggiungere un'immagine con associazione a dati a un'intestazione di pagina o un piè di pagina, è necessario eseguire ulteriori operazioni. Per altre informazioni, vedere [Intestazioni di pagina e piè di pagina &#40;Generatore report e SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-data-bound-image"></a>Per aggiungere un'immagine con associazione a dati  
  
1.  Nella visualizzazione di progettazione report creare una tabella con una connessione all'origine dati e un set di dati con un campo contenente dati immagine binari. Per altre informazioni, vedere [Tabelle &#40;Generatore report e SSRS&#41;](tables-report-builder-and-ssrs.md).  
  
2.  Inserire una colonna nella tabella. Per altre informazioni, vedere [Inserire o eliminare una colonna &#40;Generatore report e SSRS&#41;](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Scegliere **Immagine** dal menu **Inserisci**, quindi fare clic nella riga di dati della nuova colonna.  
  
4.  Nella pagina Generale della finestra di dialogo **Proprietà immagine** digitare un nome nella casella di testo **Nome** o accettare il nome predefinito.  
  
5.  (Facoltativo) Nella casella di testo **Descrizione comando** digitare il testo da visualizzare quando il puntatore del mouse viene posizionato nel report sottoposto a rendering per HTML.  
  
6.  In **Selezionare l'origine dell'immagine**selezionare **Database**.  
  
7.  In **Utilizzare questo campo**selezionare il campo che contiene le immagini nel report.  
  
8.  In **Utilizzare questo tipo MIME**selezionare il tipo MIME, o il formato di file, dell'immagine, ad esempio bmp.  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Nell'area di progettazione del report verrà visualizzato un segnaposto dell'immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [Immagini &#40;Report e SSRS&#41;](images-report-builder-and-ssrs.md)   
 [Incorporare un'immagine in un Report &#40;Report e SSRS&#41;](embed-an-image-in-a-report-report-builder-and-ssrs.md)   
 [Aggiungere un'immagine esterna &#40;Report e SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà immagine, Generale &#40;Generatore report e SSRS&#41;](../image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
