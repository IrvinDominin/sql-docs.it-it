---
title: "Specificare una colonna da utilizzare come regressore in un modello | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
caps.latest.revision: 6
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 6
---
# Specificare una colonna da utilizzare come regressore in un modello
  Un modello di regressione lineare rappresenta il valore dell'attributo stimabile come il risultato di una formula che consente di combinare gli input in modo che i dati si adattino il più possibile a una retta di regressione stimata. L'algoritmo accetta come input sono valori numerici e rileva automaticamente gli input che si adattano meglio.  
  
 Per specificare che una colonna può essere inclusa come regressore, è possibile tuttavia aggiungere il parametro FORCE_REGRESSOR al modello e indicare i regressori da utilizzare. Questa operazione può essere eseguita nei casi in cui l'attributo è significativo anche se l'effetto è insufficiente per essere rilevato dal modello o quando si desidera garantire che l'attributo venga incluso nella formula.  
  
 Di seguito viene descritto come creare un modello di regressione lineare semplice usando gli stessi dati di esempio usati per l'[esercitazione sulle reti neurali](../Topic/Lesson%205:%20Building%20Neural%20Network%20and%20Logistic%20Regression%20Models%20\(Intermediate%20Data%20Mining%20Tutorial\).md). Sebbene non sia necessariamente affidabile, il modello dimostra i concetti di base per utilizzare Progettazione modelli di data mining per personalizzare un modello di regressione lineare.  
  
### Come creare un semplice modello di regressione lineare  
  
1.  In **Esplora soluzioni** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] espandere **Strutture di data mining**.  
  
2.  Fare doppio clic su Call Center.dmm per aprirlo nella finestra di progettazione.  
  
3.  Scegliere **Nuovo modello di data mining** dal menu **Modello di data mining**.  
  
4.  Selezionare **Microsoft Linear Regression** come algoritmo. e digitare **Regressione Call Center** come nome.  
  
5.  Nella scheda **Modelli di data mining** modificare l'uso delle colonne come indicato di seguito. È necessario impostare su **Ignora** tutte le colonne non presenti nell'elenco seguente, se tale impostazione non è già specificata.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Operatori totali**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  Scegliere l'opzione **Set Model Parameters** (Imposta parametri modello) dal menu **Modello di data mining**.  
  
7.  Per il parametro FORCE_REGRESSOR, nella colonna **Valore** digitare i nomi di colonna racchiusi tra parentesi quadre e separati da una virgola come indicato di seguito:  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  Le colonne che rappresentano i regressori migliori verranno rilevate automaticamente. È necessario applicare i regressori solo quando si desidera garantire che una colonna venga inclusa nella formula finale.  
  
8.  Scegliere **Elabora modello** nel menu **Modello di data mining**.  
  
     Nel visualizzatore il modello è rappresentato da un nodo singolo che contiene la formula di regressione. È possibile visualizzare la formula in **Legenda data mining** oppure è possibile usare le query per estrarre i coefficienti per la formula.  
  
## Vedere anche  
 [Algoritmo Microsoft Linear Regression](../../analysis-services/data-mining/microsoft-linear-regression-algorithm.md)   
 [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md)   
 [Riferimento tecnico per l'algoritmo Microsoft Linear Regression](../../analysis-services/data-mining/microsoft-linear-regression-algorithm-technical-reference.md)   
 [Contenuto dei modelli di data mining per i modelli di regressione lineare &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  