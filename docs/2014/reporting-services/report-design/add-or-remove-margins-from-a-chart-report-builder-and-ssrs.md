---
title: Aggiungere o rimuovere i margini da un grafico (Generatore report e SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1dce4183ff7e873fd16ac3df8a346a600c7cb0dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105831"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>Aggiungere o rimuovere i margini da un grafico (Generatore report e SSRS)
  Nei tipi di grafico istogramma e a dispersione vengono automaticamente aggiunti margini laterali alle estremità dell'asse X. Nei tipi di grafico a barre vengono automaticamente aggiunti margini laterali alle estremità dell'asse Y. In tutti gli altri tipi di grafico non vengono aggiunti margini laterali. Non è possibile modificare le dimensioni del margine.  
  
 Questo argomento non è applicabile per grafici a torta, ad anello, a imbuto o a piramide.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a>Per abilitare o disabilitare i margini laterali  
  
1.  Fare clic con il pulsante destro del mouse sull'asse e selezionare **Proprietà asse**. Verrà visualizzata la finestra di dialogo **Proprietà asse verticale** o **orizzontale** .  
  
2.  Nella pagina **Opzioni asse** impostare la proprietà **Margini laterali** :  
  
    -   **Automatico** Il grafico determinerà se aggiungere o meno un margine laterale in base al tipo di grafico.  
  
    -   **Disabilitato** I grafici a barre, a dispersione e gli istogrammi non disporranno di margini laterali.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione delle etichette degli assi in un grafico &#40;Generatore report e SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà asse, Opzioni asse &#40;Generatore report e SSRS&#41;](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [Specificare un intervallo dell'asse &#40;Generatore report e SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Formattazione delle etichette degli assi come date o valute &#40;Generatore report e SSRSSSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Grafici &#40;Report e SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
