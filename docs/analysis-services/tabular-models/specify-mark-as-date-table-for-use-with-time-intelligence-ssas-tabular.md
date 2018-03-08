---
title: Specificare contrassegna come tabella data | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2520764fdd298dc63d6af5b2d44fd41bd67160ce
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="specify-mark-as-date-table-for-use-with-time-intelligence"></a>Specificare contrassegna come tabella data per l'utilizzo con Business intelligence
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Per utilizzare le funzioni di business intelligence nelle formule DAX, è necessario specificare una tabella di data e una colonna identificatore univoco (datetime) del tipo di dati Data. Una volta specificata una colonna nella tabella relativa alla data come identificatore univoco, è possibile creare le relazioni tra le colonne nella tabella in questione e tutte le tabelle dei fatti.  
  
 Quando si utilizzano funzioni di business intelligence, si applicano le regole seguenti:  
  
-   Quando si utilizzano funzioni di business intelligence DAX, non specificare mai una colonna datetime da una tabella dei fatti. Creare sempre una tabella relativa alla data separata nel modello con almeno un colonna di tipo datetime con tipo di dati Date e con valori univoci.  
  
-   Verificare che la tabella relativa alla data disponga di un intervallo di date continuo.  
  
-   È consigliabile che la granularità della colonna di tipo datetime nella tabella relativa alla data sia a livello di giorno, senza frazioni di un giorno.  
  
-   È necessario specificare una tabella relativa alla data e una colonna dell'identificatore univoco utilizzando la finestra di dialogo **Contrassegna come tabella data** .  
  
-   Creare le relazioni tra le tabelle dei fatti e le colonne di tipo di dati Date nella tabella relativa alla data.  
  
#### <a name="to-specify-a-date-table-and-unique-identifier"></a>Per specificare una tabella relativa alla data e un identificatore univoco  
  
1.  In Progettazione modelli fare clic sulla tabella relativa alla data.  
  
2.  Fare clic sul menu **Tabella** , selezionare **Data**, quindi scegliere **Contrassegna come tabella data**  
  
3.  Nella casella di riepilogo **Data** della finestra di dialogo **Contrassegna come tabella data** selezionare una colonna da utilizzare come identificatore univoco. In questa colonna devono essere inclusi valori univoci e il tipo di dati utilizzato deve essere Date. Ad esempio  
  
    |date|  
    |----------|  
    |7/1/2010 12:00:00 AM|  
    |7/2/2010 12:00:00 AM|  
    |7/3/2010 12:00:00 AM|  
    |7/4/2010 12:00:00 AM|  
    |7/5/2010 12:00:00 AM|  
  
4.  Se necessario, creare tutte le relazioni tra le tabelle dei fatti e la tabella relativa alla data.  
  
## <a name="see-also"></a>Vedere anche  
 [Calcoli](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [Funzioni di business intelligence (DAX)](http://msdn.microsoft.com/en-us/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  
