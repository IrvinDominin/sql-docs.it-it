---
title: 'Lezione 4: Contrassegna come tabella data | Documenti Microsoft'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77f29250621485f5606a0bf33615e8d15eb7d80b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34019698"
---
# <a name="lesson-3-mark-as-date-table"></a>Lezione 3: Contrassegna come tabella data
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

Nella Lezione 2: Aggiungere dati è stata importata una tabella delle dimensioni denominata DimDate. Mentre nel modello questa tabella è denominata DimDate, è possibile anche noto come un *tabella data*, in quanto contiene data e ora.  
  
Ogni volta che si utilizzano funzioni di business intelligence DAX nei calcoli, come verranno eseguite quando si creano misure leggermente in un secondo momento, è necessario specificare le proprietà di tabella di dati, che includono un *tabella data* e un identificatore univoco *Data colonna* in tale tabella.
  
In questa lezione si sarà contrassegna la tabella DimDate come il *tabella data* e la colonna Data (nella tabella Date) come il *colonna Data* (identificatore univoco).  

Prima si contrassegna la tabella relativa alla data e la colonna di data, è necessario eseguire una piccola manutenzione per rendere più facile comprendere il modello. Si noterà che la tabella DimDate una colonna denominata **FullDateAlternateKey**. Contiene una riga per ogni giorno in ogni anno di calendario incluso nella tabella. Verrà usato molto in questa colonna nelle formule di misure e nei report. Tuttavia, FullDateAlternateKey non sono in effetti un identificatore valido per questa colonna. È il nome **data**, rendendo più semplice identificare e includere nelle formule. Quando possibile, è consigliabile rinominare gli oggetti come tabelle e colonne per renderle più facilmente identificabili nel client di creazione report di applicazioni, quali Power BI ed Excel. 
  
Tempo stimato per il completamento della lezione: **3 minuti**  
  
## <a name="prerequisites"></a>Prerequisiti  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 2: aggiungere dati](../analysis-services/lesson-2-add-data.md). 

### <a name="to-rename-the-fulldatealternatekey-column"></a>Per rinominare la colonna FullDateAlternateKey

1.  In Progettazione modelli fare clic su di **DimDate** tabella.

2.  Fare doppio clic sull'intestazione per il **FullDateAlternateKey** colonna e quindi rinominarlo **data**.

  
### <a name="to-set-mark-as-date-table"></a>Per impostare Contrassegna come tabella data  
  
1.  Selezionare la colonna **Data** , quindi nella finestra **Proprietà** verificare che **Data**sia selezionata in  **Tipo di dati** .  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**.  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare la colonna **Data** come identificatore univoco. Verrà in genere selezionato per impostazione predefinita. Scegliere **OK**. 

    ![come tabulare-lesson3-data-tabella-](../analysis-services/media/as-tabular-lesson3-date-table.png)
  

## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 4: creare relazioni](../analysis-services/lesson-4-create-relationships.md).
  
