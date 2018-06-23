---
title: Nascondere o bloccare colonne (SSAS tabulare) | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a83b824fc6e2079c5c1db1ac9c673f9e42f7568e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067463"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a>Nascondere o bloccare colonne (SSAS tabulare)
  In Progettazione modelli, se in una tabella sono presenti colonne che non si desidera visualizzare, è possibile nasconderle temporaneamente. Nascondendo una colonna si ottiene maggiore spazio sullo schermo per aggiungerne di nuove o per utilizzare solo le colonne di dati rilevanti. È possibile nascondere e scoprire colonne dal menu **Colonna** in Progettazione modelli e dal menu di scelta rapida disponibile in ogni intestazione di colonna. Per mantenere visibile un'area di un modello durante lo scorrimento a un'altra area del modello, è possibile bloccare colonne specifiche in un'area.  
  
> [!IMPORTANT]  
>  La possibilità di nascondere colonne non dovrebbe essere utilizzata per la sicurezza dei dati, ma solo per semplificare e abbreviare l'elenco di colonne visibili in Progettazione modelli o nei report. Per proteggere i dati, è possibile definire ruoli di sicurezza. I ruoli possono limitare la visualizzazione di metadati e dati in base agli oggetti definiti nel ruolo. Per altre informazioni, vedere [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).  
  
 Quando si nasconde una colonna, è possibile scegliere se nasconderla mentre si lavora in Progettazione modelli o nei report. Se si nascondono tutte le colonne, l'intera tabella appare vuota in Progettazione modelli.  
  
> [!NOTE]  
>  Se sono molte le colonne da nascondere, è possibile creare una prospettiva anziché nascondere e scoprire colonne. Una prospettiva è una vista personalizzata dei dati tramite cui si semplifica l'utilizzo di un subset di dati correlati. Per altre informazioni, vedere [Creare e gestire prospettive &#40;SSAS tabulare&#41;](perspectives-ssas-tabular.md)  
  
### <a name="to-hide-an-individual-column"></a>Per nascondere una singola colonna  
  
1.  In Progettazione modelli selezionare la tabella contenente la colonna che si desidera nascondere.  
  
2.  Fare clic con il pulsante destro del mouse sulla colonna, selezionare **Nascondi colonne**, quindi fare clic su **Da finestra progettazione e report**, **Da report**oppure su **Da finestra di progettazione**.  
  
### <a name="to-hide-multiple-columns"></a>Per nascondere più colonne  
  
1.  In Progettazione modelli selezionare la tabella contenente le colonne che si desidera nascondere.  
  
2.  Fare clic sul menu **Colonne** , quindi scegliere **Nascondi e scopri**.  
  
3.  Nella finestra di dialogo **Nascondi e scopri colonne** individuare ogni colonna che si desidera nascondere, quindi deselezionare una o entrambe le opzioni **In Designer** (Nella finestra di progettazione) e **In Reports**(Nei report).  
  
4.  Fare clic su **OK**.  
  
### <a name="to-freeze-columns"></a>Per bloccare le colonne  
  
1.  In Progettazione modelli selezionare la tabella contenente le colonne che si desidera bloccare.  
  
2.  Selezionare una o più colonne da bloccare.  
  
3.  Fare clic sul menu **Colonne** , quindi scegliere **Blocca**.  
  
    > [!NOTE]  
    >  Quando una colonna viene bloccata, viene spostata a sinistra della tabella (o davanti) nella finestra di progettazione. Se sbloccata, la colonna non torna nella relativa posizione originale.  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle e colonne &#40;tabulare di SSAS&#41;](tables-and-columns-ssas-tabular.md)   
 [Prospettive &#40;tabulare di SSAS&#41;](perspectives-ssas-tabular.md)   
 [Ruoli &#40;tabulare di SSAS&#41;](roles-ssas-tabular.md)  
  
  