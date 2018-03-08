---
title: 'Lezione 6: Creare colonne calcolate | Documenti Microsoft'
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: d126766a-5699-4e9f-8213-8c7eea0fc14e
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 58d361452f134976b7f90ce983b3bc5b7ba28d46
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-5-create-calculated-columns"></a>Lezione 5: Creare colonne calcolate
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In questa lezione verranno creati nuovi dati nel modello aggiungendo colonne calcolate. Una colonna calcolata è basata sui dati già presenti nel modello. Per ulteriori informazioni, vedere [colonne calcolate](../analysis-services/tabular-models/ssas-calculated-columns.md).  
  
Verranno create cinque nuove colonne calcolate in tre tabelle diverse. I passaggi sono leggermente diversi per ogni attività. L'obiettivo è quello di mostrare che vi sono diversi metodi per creare nuove colonne, rinominarle e collocarle in diverse posizioni in una tabella.  
  
Tempo stimato per il completamento della lezione: **15 minuti**  
  
## <a name="prerequisites"></a>Prerequisites  
Questo argomento fa parte di un'esercitazione relativa alla modellazione tabulare che deve essere completata nell'ordine specificato. Prima di eseguire le attività in questa lezione, è necessario avere completato la lezione precedente: [lezione 4: creare relazioni](../analysis-services/lesson-4-create-relationships.md). 
  
## <a name="create-calculated-columns"></a>Creare colonne calcolate  
  
#### <a name="create-a-monthcalendar-calculated-column-in-the-dimdate-table"></a>Creare una colonna calcolata di MonthCalendar della tabella DimDate  
  
1.  Fare clic su di **modello** menu > **vista modello** > **vista dati**.  
  
    Le colonne calcolate possono essere create solo tramite Progettazione modelli in Vista dati.  
  
2.  In Progettazione modelli fare clic su di **DimDate** tabella (scheda).  
  
3.  Fare doppio clic su di **CalendarQuarter** intestazione di colonna e quindi fare clic su **Inserisci colonna**.  
  
    Una nuova colonna denominata **CalculatedColumn1** verrà inserita a sinistra della colonna **Calendar Quarter** .  
  
4.  Sulla barra della formula sopra la tabella digitare la formula seguente. La funzionalità Completamento automatico consente di digitare i nomi completi di colonne e tabelle ed elencare le funzioni disponibili.  
  
    ```  
    =RIGHT(" " & FORMAT([MonthNumberOfYear],"#0"), 2) & " - " & [EnglishMonthName]  
    ``` 
  
    I valori vengono quindi popolati per tutte le righe nella colonna calcolata. Scorrendo la tabella verso il basso, si vedrà che le righe possono avere valori diversi per questa colonna, in base ai dati presenti in ogni riga.    
  
5.  Rinominare questa colonna come **MonthCalendar**. 

    ![come-tabulare-lesson5-newcolumn](../analysis-services/media/as-tabular-lesson5-newcolumn.png) 
  
MonthCalendar calcolato colonna fornisce un nome ordinabile per mese.  
  
#### <a name="create-a-dayofweek-calculated-column-in-the-dimdate-table"></a>Creare una colonna calcolata DayOfWeek della tabella DimDate  
  
1.  Con il **DimDate** ancora attiva, fare clic su di **colonna** menu e quindi fare clic su **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
    
    ```
    =RIGHT(" " & FORMAT([DayNumberOfWeek],"#0"), 2) & " - " & [EnglishDayNameOfWeek]  
    ```
    
    Al termine della compilazione della formula, premere INVIO. La nuova colonna verrà aggiunta all'estremità destra della tabella.  
  
3.  Rinominare la colonna in **DayOfWeek**.  
  
4.  Fare clic sull'intestazione di colonna e quindi trascinare la colonna tra la **EnglishDayNameOfWeek** colonna e **DayNumberOfMonth** colonna.  
  
    > [!TIP]  
    > Lo spostamento delle colonne nella tabella semplifica l'esplorazione.  
  
L'enumerazione DayOfWeek calcolato colonna fornisce un nome ordinabile per il giorno della settimana.  
  
#### <a name="create-a-productsubcategoryname-calculated-column-in-the-dimproduct-table"></a>Creare una colonna calcolata ProductSubcategoryName nella tabella DimProduct  
  
  
1.  Nel **DimProduct** tabella, scorrimento all'estrema destra della tabella. Si noti che la colonna all'estrema destra è denominata **Aggiungi colonna** (in corsivo). Fare clic sull'intestazione di colonna.  
  
2.  Sulla barra della formula digitare la formula seguente.  
    
    ```
    =RELATED('DimProductSubcategory'[EnglishProductSubcategoryName])  
    ```
  
3.  Rinominare la colonna in **ProductSubcategoryName**.  
  
La colonna calcolata ProductSubcategoryName viene utilizzata per creare una gerarchia nella tabella DimProduct che includono i dati dalla colonna EnglishProductSubcategoryName nella tabella DimProductSubcategory. Le gerarchie non possono estendersi in più di una tabella. Si creerà le gerarchie in un secondo momento nella lezione 9.  
  
#### <a name="create-a-productcategoryname-calculated-column-in-the-dimproduct-table"></a>Creare una colonna calcolata ProductCategoryName nella tabella DimProduct  
  
1.  Con il **DimProduct** ancora attiva, fare clic di tabella il **colonna** menu e quindi fare clic su **Aggiungi colonna**.  
  
2.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    =RELATED('DimProductCategory'[EnglishProductCategoryName]) 
    ```
    
3.  Rinominare la colonna in **ProductCategoryName**.  
  
La colonna calcolata di ProductCategoryName viene utilizzata per creare una gerarchia nella tabella DimProduct che includono i dati dalla colonna EnglishProductCategoryName nella tabella DimProductCategory. Le gerarchie non possono estendersi in più di una tabella.  
  
#### <a name="create-a-margin-calculated-column-in-the-factinternetsales-table"></a>Creare una colonna calcolata Margin nella tabella FactInternetSales  
  
1.  In Progettazione modelli selezionare la **FactInternetSales** tabella.  
  
2.  Aggiungere una nuova colonna.  
  
3.  Sulla barra della formula digitare la formula seguente:  
  
    ```
    =[SalesAmount]-[TotalProductCost]
    ``` 

4.  Rinominare la colonna in **Margin**.  
  
5.  Trascinare la colonna tra la **SalesAmount** colonna e **TaxAmt** colonna. 
 
      ![come-tabulare-lesson5-newmargin](../analysis-services/media/as-tabular-lesson5-newmargin.png)
      
    La colonna calcolata Margin viene utilizzata per analizzare i margini di profitto per ogni vendita.  
  
## <a name="whats-next"></a>Quali sono le operazioni successive?
Passare alla lezione successiva: [lezione 6: creare misure](../analysis-services/lesson-6-create-measures.md).
  
  
  
