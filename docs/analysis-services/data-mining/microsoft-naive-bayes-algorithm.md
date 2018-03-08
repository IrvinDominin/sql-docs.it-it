---
title: Algoritmo Microsoft Naive Bayes | Documenti Microsoft
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
- Bayesian classifiers
- algorithms [data mining]
- predictive modeling [Analysis Services]
- classification algorithms [Analysis Services]
- naive bayes algorithms [Analysis Services]
ms.assetid: 3b53e011-3b1a-4cd1-bdc2-456768ba31b5
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0ac78f4108cfde4efa5de2e04be3a7e2e9c7a2ff
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="microsoft-naive-bayes-algorithm"></a>Algoritmo Microsoft Naive Bayes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes è un algoritmo di classificazione basato su teoremi di Bayes e può essere usato sia per la modellazione predittiva che per quella esplorativa. La parola naive nel nome Naive Bayes deriva dal fatto che nell'algoritmo vengono utilizzate tecniche di Bayes, ma non vengono considerate le dipendenze eventualmente presenti.  
  
 Questo algoritmo include funzionalità di calcolo più semplici di quelle di altri algoritmi [!INCLUDE[msCoName](../../includes/msconame-md.md)] ed è utile pertanto per generare rapidamente i modelli di data mining al fine di individuare le relazioni tra colonne di input e colonne stimabili. È possibile utilizzare questo algoritmo per eseguire l'esplorazione iniziale dei dati e applicare successivamente i risultati ottenuti per creare modelli di data mining aggiuntivi con altri algoritmi dotati di funzionalità di calcolo più avanzate e accurate.  
  
## <a name="example"></a>Esempio  
 Come strategia promozionale continuativa, il reparto marketing dell'azienda Adventure Works Cycle ha deciso di inviare volantini ai potenziali clienti mediante mailing diretto. Per ridurre i costi, i volantini verranno inviati solo ai clienti che probabilmente risponderanno. L'azienda archivia in un database le informazioni demografiche e relative alla risposta dei clienti a un mailing precedente. L'obiettivo è analizzare tali dati per scoprire in che modo è possibile utilizzare informazioni demografiche come l'età e il luogo di residenza per eseguire la stima relativa alla risposta a una promozione, confrontando i potenziali clienti con quelli che presentano caratteristiche analoghe e in passato hanno acquistato prodotti dell'azienda. In particolare, si intende esaminare le differenze tra i clienti che hanno acquistato una bicicletta e quelli che non l'hanno acquistata.  
  
 Tramite l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes, il reparto marketing può eseguire rapidamente la stima relativa al profilo di un cliente specifico e determinare quindi i clienti che, con maggiore probabilità, risponderanno ai volantini. Mediante il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes disponibile in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], il reparto può inoltre individuare visivamente in modo specifico le colonne di input che contribuiscono alle risposte positive ai volantini.  
  
## <a name="how-the-algorithm-works"></a>Funzionamento dell'algoritmo  
 L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes consente di calcolare la probabilità di ogni stato per ogni colonna di input, considerando ogni stato possibile della colonna stimabile.  
  
 Per comprendere questo funzionamento, utilizzare il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] (come mostrato nel grafico seguente) per esplorare in modo visivo la distribuzione degli stati eseguita dall'algoritmo.  
  
 ![Naive bayes distribuzione degli stati](../../analysis-services/data-mining/media/naive-bayes.gif "Naive bayes distribuzione degli Stati")  
  
 Nel Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes viene elencata ogni colonna di input nel set di dati e viene mostrata la distribuzione degli stati corrispondenti, considerando ogni stato della colonna stimabile.  
  
 Questa vista del modello consente di identificare le colonne di input significative ai fini della differenziazione degli stati della colonna stimabile.  
  
 Ad esempio, nella riga per Distanza dal lavoro qui indicata, la distribuzione dei valori di input è visibilmente diversa per gli acquirenti rispetto ai non acquirenti. Questo indica che l'input, Distanza dal lavoro = 0-1 chilometri, è un potenziale criterio di stima.  
  
 Il visualizzatore fornisce inoltre valori per le distribuzioni, pertanto è possibile visualizzare che, per i clienti che risiedono a una distanza dal posto di lavoro compresa tra uno e due chilometri, la probabilità che acquistino una bicicletta è pari a 0,387, mentre la probabilità che non effettuino tale acquisto è pari a 0,287. In questo esempio nell'algoritmo vengono utilizzate le informazioni numeriche derivate da caratteristiche del cliente, ad esempio la distanza dal posto di lavoro, per stimare se il cliente acquisterà una bicicletta.  
  
 Per altre informazioni sull'uso del visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes, vedere [Visualizzare un modello utilizzando il Visualizzatore Microsoft Naive Bayes](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md).  
  
## <a name="data-required-for-naive-bayes-models"></a>Dati necessari per i modelli Naive Bayes  
 Quando si preparano i dati da utilizzare per il training di un modello Naive Bayes, verificare che siano chiari i requisiti dell'algoritmo, tra cui la quantità di dati necessari e la modalità di utilizzo dei dati.  
  
 I requisiti di un modello Naive Bayes sono i seguenti:  
  
-   **Una colonna a chiave singola** Ogni modello deve contenere una colonna numerica o di testo che identifichi in modo univoco ogni record. Le chiavi composte non sono consentite.  
  
-   **Colonne di input** In un modello Naive Bayes tutte le colonne devono essere colonne discrete, oppure devono contenere valori suddivisi. Per informazioni su come eseguire la discretizzazione (bin) delle colonne, vedere [Metodi di discretizzazione &#40;data mining&#41;](../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
-   **Le variabili possono essere indipendenti.** Per un modello Naive Bayes, è importante verificare inoltre che gli attributi di input siano indipendenti uno dall'altro. Questo aspetto è particolarmente importante quando si utilizza il modello per la stima. L'uso di due colonne di dati già strettamente correlati comporterebbe un'influenza ancora maggiore di tali colonne e verrebbero pertanto messi in secondo piano gli altri fattori che influiscono sul risultato.  
  
     Viceversa, la possibilità dell'algoritmo di identificare le correlazioni fra variabili è utile quando si esplora un modello o un set di dati, per identificare le relazioni fra input.  
  
-   **Almeno una colonna stimabile** Nell'attributo stimabile devono essere contenuti valori discreti o discretizzati.  
  
     I valori della colonna stimabile possono essere utilizzati come input. Ciò può essere utile quando si esplora un nuovo set di dati, per trovare le relazioni fra le colonne.  
  
## <a name="viewing-the-model"></a>Visualizzazione del modello  
 Per esplorare il modello, è possibile usare il **Visualizzatore Microsoft Naive Bayes**. Nel visualizzatore viene illustrato il modo in cui gli attributi di input sono correlati all'attributo stimabile. Nel visualizzatore viene inoltre fornito un profilo dettagliato di ogni cluster, un elenco degli attributi che consentono di distinguere ogni cluster dagli altri e le caratteristiche dell'intero set di dati di training. Per altre informazioni, vedere [Visualizzare un modello utilizzando il Visualizzatore Microsoft Naive Bayes](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md).  
  
 Per maggiori dettagli, è possibile esplorare il modello in [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c). Per altre informazioni sul tipo di informazioni archiviate nel modello, vedere [Contenuto dei modelli di data mining per i modelli Naive Bayes &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md).  
  
## <a name="making-predictions"></a>Esecuzione di stime  
 In seguito al training del modello, i risultati vengono archiviati come set di modelli, esplorabili o utilizzabili per eseguire stime.  
  
 È possibile creare query per restituire stime sul modo in cui i nuovi dati sono correlati all'attributo stimabile oppure recuperare statistiche che descrivono le correlazioni rilevate dal modello.  
  
 Per informazioni sulla creazione di query in base a un modello di data mining, vedere [Query di data mining](../../analysis-services/data-mining/data-mining-queries.md). Per esempi di come usare le query con un modello Naive Bayes, vedere [Esempi di query sul modello Naive Bayes](../../analysis-services/data-mining/naive-bayes-model-query-examples.md).  
  
## <a name="remarks"></a>Osservazioni  
  
-   Supporta l'utilizzo del linguaggio PMML (Predictive Model Markup Language) per la creazione di modelli di data mining.  
  
-   Supporta il drill-through.  
  
-   Non supporta la creazione di dimensioni di data mining.  
  
-   Supporta l'utilizzo di modelli di data mining OLAP.  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmi di Data Mining &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Selezione funzionalità &#40; Data Mining &#41;](../../analysis-services/data-mining/feature-selection-data-mining.md)   
 [Esempi di Query modello Naive Bayes](../../analysis-services/data-mining/naive-bayes-model-query-examples.md)   
 [Contenuto del modello di data mining per i modelli Naive Bayes &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)   
 [Riferimento tecnico di Microsoft Naive Bayes algoritmo](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
  
