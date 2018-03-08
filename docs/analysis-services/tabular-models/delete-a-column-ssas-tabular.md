---
title: Eliminare una colonna | Documenti Microsoft
ms.custom: 
ms.date: 02/22/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 703db83b-e554-450e-813e-23ad08c1cdad
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c18504b3e6430807f124938b60d7f022a8050379
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="delete-a-column"></a>Eliminare una colonna 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
In questo articolo viene descritto come eliminare una colonna da una tabella del modello tabulare.  
  
## <a name="delete-a-model-table-column"></a>Eliminare una colonna dalla tabella del modello  
  
> [!NOTE]  
>  L'eliminazione di una colonna da una tabella del modello non elimina la colonna da una definizione della query della partizione. Se la colonna che si desidera eliminare fa parte di una partizione, è necessario eliminare manualmente la colonna dalla definizione della query della partizione. Se non si elimina la colonna dalla definizione della query della partizione, durante le operazioni di elaborazione verranno eseguite query sulla colonna e restituiti dati che tuttavia non saranno popolati nella tabella del modello. Per ulteriori informazioni, vedere [partizioni](../../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
#### <a name="to-delete-a-model-table-column"></a>Per eliminare una colonna dalla tabella del modello  
  
-   In Progettazione modelli, nella tabella contenente la colonna che si desidera eliminare, fare clic con il pulsante destro del mouse su tale colonna, quindi scegliere **Elimina**.  
  
#### <a name="to-delete-a-model-table-column-by-using-the-table-properties-dialog-box"></a>Per eliminare una colonna dalla tabella del modello tramite la finestra di dialogo Proprietà tabella  
  
1.  In Progettazione modelli fare clic sulla tabella contenente la colonna che si desidera eliminare, quindi scegliere **Proprietà tabella** dal menu  **Tabella**.  
  
2.  In **Nomi colonne da**selezionare **Modello** (*per usare nomi delle colonna della tabella del modello, se diversi dall'origine*).  
  
3.  Nella finestra di anteprima della tabella nella finestra di dialogo **Modifica proprietà tabella** deselezionare la colonna che si desidera eliminare, quindi scegliere **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere colonne a una tabella](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)   
 [Partizioni](../../analysis-services/tabular-models/partitions-ssas-tabular.md)  
  
  
