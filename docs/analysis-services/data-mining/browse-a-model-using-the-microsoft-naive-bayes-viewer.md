---
title: Visualizzare un modello utilizzando il visualizzatore Microsoft Naive Bayes | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e7afe60ffa61af8e2c1ae5b60deb596230738a78
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34014778"
---
# <a name="browse-a-model-using-the-microsoft-naive-bayes-viewer"></a>Visualizzare un modello utilizzando il Visualizzatore Microsoft Naive Bayes
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes disponibile in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di visualizzare i modelli di data mining compilati con l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes. L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes è un algoritmo di classificazione altamente adattabile alle attività di modellazione predittiva. Per altre informazioni su questo algoritmo, vedere [Algoritmo Microsoft Naive Bayes](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md).  
  
 Poiché uno degli scopi principali di un modello Naive Bayes consiste nell'esplorare rapidamente i dati di un set, il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes include diversi metodi per la visualizzazione dell'interazione tra gli attributi stimabili e gli attributi di input per una tabella del case.  
  
> [!NOTE]  
>  Per visualizzare informazioni dettagliate sulle equazioni utilizzate nel modello e sugli schemi individuati, utilizzare il [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer. Per altre informazioni, vedere [Visualizzare un modello utilizzando Microsoft Generic Content Tree Viewer](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) o [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).  
  
##  <a name="BKMK_ViewerTabs"></a> Schede del visualizzatore  
 Per la visualizzazione di un modello di data mining in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]viene utilizzato il visualizzatore appropriato nella scheda **Visualizzatore modello di data mining** di Progettazione modelli di data mining. Per l'esplorazione dei dati, nel Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes sono disponibili le schede seguenti:  
  
-   [Rete di dipendenze](#BKMK_Dependency)  
  
-   [Profili attributo](#BKMK_Profiles)  
  
-   [Caratteristiche attributo](#BKMK_Characteristics)  
  
-   [Analisi discriminante attributi](#BKMK_Discrimination)  
  
##  <a name="BKMK_Dependency"></a> Rete di dipendenze  
 Nella scheda **Rete di dipendenze** vengono visualizzate le dipendenze tra gli attributi di input e gli attributi stimabili di un modello. Il dispositivo di scorrimento a sinistra del visualizzatore svolge la funzione di filtro correlato ai livelli di attendibilità delle dipendenze. Se si sposta il dispositivo di scorrimento verso il basso, vengono visualizzati solo i collegamenti più attendibili.  
  
 Quando si seleziona un nodo, nel visualizzatore vengono evidenziate le dipendenze specifiche del nodo. Se ad esempio si sceglie un nodo stimabile, nel visualizzatore verrà inoltre evidenziato ogni nodo che contribuisce alla stima del nodo stimabile.  
  
 La legenda nella parte inferiore del visualizzatore consente di individuare le corrispondenze tra i colori e i tipi di dipendenza rappresentati nel grafico. Ad esempio, quando si seleziona un nodo stimabile, a quest'ultimo viene applicata un'ombreggiatura turchese mentre ai nodi utilizzati per la stima del nodo selezionato viene applicata un'ombreggiatura arancione.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Profiles"></a> Profili attributo  
 Nella scheda **Profili attributo** viene visualizzata una griglia con istogrammi. Tale griglia consente di confrontare l'attributo stimabile selezionato nella casella **Stimabile** con tutti gli altri attributi del modello. Ogni colonna della scheda rappresenta uno stato dell'attributo stimabile. Se l'attributo stimabile include molti stati, è possibile modificare il numero di stati visualizzati nell'istogramma regolando le **Barre istogramma**. Se il numero scelto è inferiore al numero totale di stati dell'attributo, gli stati saranno elencati nell'ordine in cui vengono supportati, con gli stati rimanenti raccolti in un singolo bucket grigio.  
  
 Fare clic sulla casella di controllo **Mostra legenda** per visualizzare una legenda di data mining che consente di individuare le corrispondenze tra i colori dell'istogramma e gli stati di un attributo. Nella legenda di data mining viene visualizzata anche la distribuzione di case per ogni coppia attributo-valore selezionata.  
  
 Per copiare il contenuto della griglia negli Appunti in formato tabella HTML, fare clic con il pulsante destro del mouse sulla scheda **Profili attributo** e scegliere **Copia**.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Characteristics"></a> Caratteristiche attributo  
 Per usare la scheda **Caratteristiche attributo** , è necessario selezionare un attributo stimabile dall'elenco **Attributo** e uno degli stati corrispondenti dall'elenco **Valore** . Quando si impostano tali variabili, nella scheda **Caratteristiche attributo** vengono visualizzati gli stati degli attributi associati al case dell'attributo selezionato. Gli attributi vengono ordinati in base alla priorità.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
##  <a name="BKMK_Discrimination"></a> Analisi discriminante attributi  
 Per usare la scheda **Analisi discriminante attributi** , è necessario selezionare un attributo stimabile e due degli stati corrispondenti dagli elenchi **Attributo**, **Valore 1**e **Valore 2** . Nella griglia della scheda **Analisi discriminante attributi** verranno visualizzate colonne con le informazioni seguenti:  
  
 **Attributo**  
 Elenca altri attributi nel set di dati contenente uno stato che predilige in modo significativo uno stato dell'attributo stimabile.  
  
 **Valori**  
 Mostra il valore dell'attributo nella colonna **Attributo** .  
  
 **Predilige \<valore 1 >**  
 Mostra una barra colorata che indica in quale misura il valore dell'attributo predilige il valore dell'attributo stimabile mostrato in **Valore 1**.  
  
 **Predilige \<valore 2 >**  
 Mostra una barra colorata che indica in quale misura il valore dell'attributo predilige il valore dell'attributo stimabile mostrato in **Valore 2**.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Vedere anche  
 [Algoritmo Microsoft Naive Bayes](../../analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)   
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Strumenti di Data Mining](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visualizzatori modello di Data Mining](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
