---
title: Algoritmo Microsoft Neural Network | Documenti Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- training neural networks
- output neurons [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- neurons [Analysis Services]
- classification algorithms [Analysis Services]
- neural networks
- multilayer perceptron network of neurons [Analysis Services]
- hidden neurons
- Back-Propagated Delta Rule network
- input neurons [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 8af39f31c569beb4df25d8da1dd933c902d3b4f6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="microsoft-neural-network-algorithm"></a>Algoritmo Microsoft Neural Network
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network è un'implementazione dell'architettura di rete neurale diffusa e flessibile per l'apprendimento automatico.  Il funzionamento dell'algoritmo si basa sulla verifica di ogni possibile stato dell'attributo di input rispetto a ogni possibile stato dell'attributo di stima e sul calcolo delle probabilità per ogni combinazione in base ai dati di training. Queste probabilità possono quindi essere usate a scopo di classificazione o regressione o per stimare un risultato, sulla base di alcuni attributi di input. Una rete neurale può essere usata anche per l'analisi di associazione.  
  
 Quando si crea un modello di data mining con l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network, è possibile includere più output e l'algoritmo creerà più reti. Il numero di reti incluse in un singolo modello di data mining dipende dal numero di stati (o valori di attributi) contenuti nelle colonne di input, nonché dal numero di colonne stimabili usate dal modello e dal numero di stati in tale colonne.  
  
## <a name="example"></a>Esempio  
 L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network è utile per l'analisi di dati di input complessi, ad esempio relativi a un processo di produzione o commerciale, oppure di problemi aziendali per i quali è disponibile una quantità significativa di dati di training ma non è possibile derivare facilmente regole specifiche tramite altri algoritmi.  
  
 Tra gli scenari consigliati per l'utilizzo dell'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network sono inclusi i seguenti:  
  
-   Analisi di marketing e di promozioni, ad esempio la misurazione del successo di una promozione tramite mailing diretto o di una campagna pubblicitaria radiofonica  
  
-   Stima di fluttuazioni del mercato azionario e valutarie o di altre informazioni finanziarie ad elevata variabilità in base a dati cronologici  
  
-   Analisi di processi di produzione e industriali  
  
-   Text mining  
  
-   Qualsiasi modello di stima che analizza le relazioni complesse tra molti input e un numero relativamente basso di output  
  
## <a name="how-the-algorithm-works"></a>Funzionamento dell'algoritmo  
 L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network crea una rete composta da un massimo di tre livelli di nodi, a volte definiti *neuroni*. Tali livelli rappresentano il *livello di input*, il *livello nascosto*e il *livello di output*.  
  
 **Livello di input** : i nodi di input definiscono tutti i valori dell'attributo di input per il modello di data mining e le relative probabilità.  
  
 **Livello nascosto** : i nodi nascosti ricevono input dai nodi di input e forniscono output ai nodi di output. Alle diverse probabilità degli input vengono assegnati pesi sul livello nascosto. Un peso descrive la pertinenza o l'importanza di un particolare input rispetto al nodo nascosto. Maggiore è il peso assegnato a un input, più importante è il valore di quell'input. Quando i pesi sono negativi, l'input può inibire, anziché favorire, un risultato specifico.  
  
 **Livello di output** : i nodi di output rappresentano valori dell'attributo stimabile per il modello di data mining.  
  
 Per una spiegazione dettagliata della creazione dei livelli di output, input e nascosti e dell'assegnazione dei punteggi a tali livelli, vedere [Riferimento tecnico per l'algoritmo Microsoft Neural Network](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="data-required-for-neural-network-models"></a>Dati necessari per modelli di rete neurale  
 Un modello di rete neurale deve contenere una colonna chiave, una o più colonne di input e una o più colonne stimabili.  
  
 I modelli di data mining che usano l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network dipendono considerevolmente dai valori specificati per i parametri disponibili per l'algoritmo. I parametri definiscono le modalità di campionamento e distribuzione dei dati in ciascuna colonna e stabiliscono quando deve essere chiamata la selezione delle caratteristiche per limitare i valori utilizzati nel modello finale.  
  
 Per altre informazioni sull'impostazione di parametri per personalizzare il comportamento del modello, vedere [Riferimento tecnico per l'algoritmo Microsoft Neural Network](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md).  
  
## <a name="viewing-a-neural-network-model"></a>Visualizzazione di un modello di rete neurale  
 Per usare i dati e osservare il modo in cui il modello mette in correlazione gli input con gli output, usare il **Visualizzatore Microsoft Neural Network**. Tramite questo visualizzatore personalizzato, è possibile impostare un filtro sugli attributi di input e i relativi valori e visualizzarne graficamente l'impatto sugli output. Le descrizioni comandi nel visualizzatore mostrano la probabilità e l'accuratezza associate a ogni coppia di valori di input e output. Per altre informazioni, vedere [Visualizzare un modello usando il Visualizzatore Microsoft Neural Network](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md).  
  
 Il modo più semplice per esplorare la struttura del modello consiste nell'usare il **Microsoft Generic Content Tree Viewer**. È possibile visualizzare gli input, gli output e le reti creati dal modello e fare clic su qualsiasi nodo per espanderlo e visualizzare le statistiche correlate ai nodi di input, output o dei livelli nascosti. Per altre informazioni, vedere [Visualizzare un modello usando Microsoft Generic Content Tree Viewer](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).  
  
## <a name="creating-predictions"></a>Creazione di stime  
 Dopo avere elaborato il modello, è possibile utilizzare la rete e i pesi archiviati in ciascun nodo per fare delle stime. Un modello di rete neurale supporta l'analisi di regressione, classificazione e associazione. Pertanto, il significato di ogni stima potrebbe essere diverso. È anche possibile eseguire una query sul modello stesso, allo scopo di esaminare le correlazioni trovate e recuperare le statistiche correlate. Per alcuni esempi di come creare query su un modello di rete neurale, vedere [Esempi di query sul modello di rete neurale](../../analysis-services/data-mining/neural-network-model-query-examples.md).  
  
 Per informazioni generali sulla creazione di query su un modello di data mining, vedere [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md).  
  
## <a name="remarks"></a>Osservazioni  
  
-   Non supporta il drill-through di dimensioni di data mining. Questo perché la struttura dei nodi nel modello di data mining non corrisponde necessariamente in modo diretto ai dati sottostanti.  
  
-   Non supporta la creazione di modelli nel formato PMML (Predictive Model Markup Language).  
  
-   Supporta l'utilizzo di modelli di data mining OLAP.  
  
-   Non supporta la creazione di dimensioni di data mining.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento tecnico l'algoritmo Microsoft Neural Network](../../analysis-services/data-mining/microsoft-neural-network-algorithm-technical-reference.md)   
 [Contenuto del modello di data mining per i modelli di rete neurale &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)   
 [Esempi di Query del modello di rete neurale](../../analysis-services/data-mining/neural-network-model-query-examples.md)   
 [Algoritmo Microsoft Logistic Regression](../../analysis-services/data-mining/microsoft-logistic-regression-algorithm.md)  
  
  
