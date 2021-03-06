---
title: Visualizzare un modello utilizzando il visualizzatore Microsoft Sequence Clustering | Documenti Microsoft
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cce1203b73f5a1685634c4b50f6e5941bed3eb98
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34016788"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a>Visualizzare un modello utilizzando il Visualizzatore Microsoft Sequence Clustering
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering disponibile in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di visualizzare i modelli di data mining compilati con l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering. L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering è un algoritmo di analisi delle sequenze da usare per l'esplorazione di dati contenenti eventi che possono essere collegati dai percorsi o *sequenze*seguenti. Per altre informazioni su questo algoritmo, vedere [Algoritmo Microsoft Sequence Clustering](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md).  
  
> [!NOTE]  
>  Per visualizzare informazioni dettagliate sulle equazioni utilizzate nel modello e sui modelli individuati, utilizzare il visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree Viewer. Per altre informazioni, vedere [Visualizzare un modello utilizzando Microsoft Generic Content Tree Viewer](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) o [Microsoft Generic Content Tree Viewer &#40;Data Mining&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).  
  
> [!NOTE]  
>  Nel Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering sono disponibili funzionalità e opzioni analoghe a quelle del Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Clustering. Per altre informazioni, vedere [Visualizzare un modello usando il Visualizzatore Microsoft Clustering](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md).  
  
##  <a name="BKMK_ViewerTabs"></a> Schede del visualizzatore  
 Per la visualizzazione di un modello di data mining in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]viene utilizzato il visualizzatore appropriato nella scheda **Visualizzatore modello di data mining** di Progettazione modelli di data mining. Per l'esplorazione di modelli di data mining per il clustering delle sequenze, nel Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering sono disponibili le schede seguenti:  
  
-   [Diagramma dei cluster](#BKMK_Diagram)  
  
-   [Profili cluster](#BKMK_Profile)  
  
-   [Caratteristiche cluster](#BKMK_Characteristics)  
  
-   [Analisi discriminante tra cluster](#BKMK_Discrimination)  
  
-   [Transizioni di stato](#BKMK_Transitions)  
  
###  <a name="BKMK_Diagram"></a> Diagramma dei cluster  
 Nella scheda **Diagramma dei cluster** del Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Clustering vengono visualizzati tutti i cluster di un modello di data mining. L'ombreggiatura della linea che collega un cluster all'altro rappresenta il grado di somiglianza dei cluster. Se l'ombreggiatura è chiara o inesistente, il grado di somiglianza dei cluster è basso. Man mano che la linea diventa più scura, il grado di somiglianza dei collegamenti aumenta. È possibile modificare il numero di linee visualizzate regolando il dispositivo di scorrimento a destra dei cluster. Se si sposta il dispositivo di scorrimento verso il basso, vengono visualizzati solo i collegamenti più attendibili.  
  
 Per impostazione predefinita, l'ombreggiatura rappresenta la popolazione del cluster. Le opzioni **Variabile****ombreggiatura** e **Stato** consentono di selezionare la coppia attributo/stato rappresentata dall'ombreggiatura. Più scura è l'ombreggiatura, maggiore è la distribuzione dell'attributo per uno stato specifico. La distribuzione diminuisce man mano che l'ombreggiatura diventa più chiara.  
  
 Per rinominare un cluster, fare clic con il pulsante destro del mouse sul nodo corrispondente e scegliere **Rinomina cluster**. Il nuovo nome è persistente nel server.  
  
 Per copiare la sezione visibile del diagramma negli Appunti, fare clic su **Copia parte visibile del grafico**. Per copiare il diagramma completo, fare clic su **Copia grafico intero**. È anche possibile ingrandire o ridurre il diagramma tramite **Zoom avanti** e **Zoom indietro**oppure adattarlo alla schermata tramite **Ridimensiona e adatta il diagramma alla finestra**.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> Profili cluster  
 La scheda **Profili cluster** offre una vista globale dei cluster creati dall'algoritmo nel modello. Ogni colonna che segue la colonna **Popolazione** della griglia rappresenta un cluster individuato dal modello. Il \<attributo > riga Samples rappresenta sequenze diverse di dati presenti nel cluster, e \<attributo > riga descrive tutti gli elementi contenuti nel cluster e la distribuzione complessiva.  
  
 L'opzione **Barre istogramma** consente di controllare il numero di barre visibili nell'istogramma. Se esiste un numero di barre superiore a quello che si sceglie di visualizzare, le barre più importanti vengono mantenute mentre le barre rimanenti vengono raggruppate in un bucket grigio.  
  
 È possibile modificare i nomi predefiniti dei cluster in modo da renderli più descrittivi. Per rinominare un cluster, fare clic con il pulsante destro del mouse sull'intestazione di colonna corrispondente e scegliere **Rinomina cluster**. È possibile nascondere i cluster selezionando **Nascondi colonna**, nonché trascinare le colonne per riordinarle nel visualizzatore.  
  
 Per aprire una finestra contenente una visualizzazione più grande e dettagliata dei cluster, fare doppio clic su una cella nella colonna **Stati** o su un istogramma nel visualizzatore.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> Caratteristiche cluster  
 Per usare la scheda **Caratteristiche cluster** , selezionare un cluster dall'elenco **Cluster** . Dopo aver selezionato un cluster, è possibile esaminare le caratteristiche del cluster specifico. Gli attributi contenuti nel cluster sono elencati nelle colonne **Variabili** , mentre lo stato di ogni attributo è elencato nella colonna **Valori** . Gli stati degli attributi sono elencati in ordine di importanza, in base alla probabilità che vengano inclusi nel cluster. La probabilità è indicata nella colonna **Probabilità** .  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> Analisi discriminante tra cluster  
 La scheda **Analisi discriminante tra cluster** consente di confrontare gli attributi di due cluster, al fine di determinare in che misura gli elementi di una sequenza prediligono un cluster rispetto a un altro. Per selezionare i cluster da confrontare, usare gli elenchi **Cluster 1** e **Cluster 2** . Il visualizzatore determina le differenze più importanti tra i cluster e mostra gli stati degli attributi associati alle differenze, in ordine di importanza. Una barra a destra dell'attributo indica il cluster che lo stato predilige e le dimensioni della barra indicano, in proporzione, quanto lo predilige.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Transitions"></a> Transizioni di stato  
 Se si seleziona un cluster nella scheda **Transizioni di stato** , è possibile visualizzare le transizioni tra stati di sequenza nel cluster selezionato. Ogni nodo all'interno del visualizzatore rappresenta uno stato della colonna relativa alla sequenza. Una freccia rappresenta una transizione tra due stati e la probabilità associata alla transizione. Se una transizione torna al nodo di origine, la freccia può puntare di nuovo a tale nodo.  
  
 Una freccia che ha origine da un punto rappresenta la probabilità che il nodo sia l'inizio di una sequenza. Un bordo finale che conduce a un valore Null rappresenta la probabilità che il nodo sia la fine della sequenza.  
  
 È possibile filtrare il bordo dei nodi mediante il dispositivo di scorrimento a sinistra della scheda.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Algoritmo Microsoft Sequence Clustering](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [Strumenti di Data Mining](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visualizzatori modello di Data Mining](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [Visualizzare un modello utilizzando il visualizzatore Microsoft Clustering](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
