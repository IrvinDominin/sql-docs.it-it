---
title: 'Analysis Services tutorial-lezione 3: contrassegna come tabella data | Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 282103baa0283e46e31b9ffe6b837e90e4bfac3c
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/27/2018
ms.locfileid: "43069398"
---
# <a name="mark-as-date-table"></a>Contrassegna come tabella data

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

Nella lezione 2: Ottenere i dati, è importata una tabella delle dimensioni denominata **DimDate**. Mentre nel modello questa tabella è denominata DimDate, può anche essere nota come un *tabella data*, perché contiene dati di data e ora.  
  
Quando si usano funzioni di business intelligence DAX, ad esempio quando si crea le misure in un secondo momento, è necessario specificare le proprietà che includono un *tabella data* e un identificatore univoco *colonna Data* in tale tabella.
  
In questa lezione, si contrassegna il **DimDate** tabella come i *tabella data* e il **data** colonna (nella tabella Date) come il *colonna delle Date* (univoco identificatore).  

Prima di contrassegnare la tabella relativa alla data e la colonna di date, è il momento giusto per eseguire alcune attività di manutenzione per rendere più facile da comprendere il modello. Si noti che nella tabella DimDate una colonna denominata **FullDateAlternateKey**. Questa colonna contiene una riga per ogni giorno dell'anno di calendario incluso nella tabella. Questo articolo è usare molto nelle formule per le misure e nei report. Tuttavia, FullDateAlternateKey non è davvero un buon identificatore per questa colonna. Rinominarlo **data**, rendendo più semplice identificare e includere nelle formule. Quando possibile, è consigliabile rinominare gli oggetti, ad esempio tabelle e colonne per renderle più facilmente identificabili in SSDT e reporting delle applicazioni client. 
  
Tempo stimato per il completamento della lezione: **tre minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  

Questo articolo fa parte di un'esercitazione di modellazione tabulare, che deve essere completata nell'ordine. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 2: ottenere i dati](../tutorial-tabular-1400/as-lesson-2-get-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Per rinominare la colonna FullDateAlternateKey

1.  In Progettazione modelli, scegliere il **DimDate** tabella.

2.  Fare doppio clic su intestazione per il **FullDateAlternateKey** colonna e quindi rinominarla **data**.

  
### <a name="to-set-mark-as-date-table"></a>Per impostare Contrassegna come tabella data  
  
1.  Selezionare la colonna **Data** , quindi nella finestra **Proprietà** verificare che **Data**sia selezionata in  **Tipo di dati** .  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco. È in genere selezionata per impostazione predefinita. Fare clic su **OK**. 

    ![as-lesson3-date-table](../tutorial-tabular-1400/media/as-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quali sono le operazioni successive?

[Lezione 4: Creare relazioni](../tutorial-tabular-1400/as-lesson-4-create-relationships.md).
  
