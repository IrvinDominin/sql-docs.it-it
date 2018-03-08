---
title: Utilizzare il drill-through dai visualizzatori modello | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5e065ad-c688-4c2c-8c82-7f3038e04915
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 31ac0cffe6656c5d644b5424b56f150572dc9af6
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="use-drillthrough-from-the-model-viewers"></a>Utilizzare il drill-through dai visualizzatori modello
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
A seconda del tipo di modello, è possibile utilizzare il drill-through dai visualizzatori nella scheda **Visualizzatore modello di data mining** di Progettazione modelli di data mining per esplorare i case utilizzati nel modello di data mining o per visualizzare colonne aggiuntive nella struttura di data mining. Sebbene molti tipi di modello non supportino il drill-through perché gli schemi del modello non possono essere collegati direttamente a case specifici, i tipi di modello seguenti supportano il drill-through.  
  
 Ricordare che è necessario abilitare il drill-through per il modello e disporre delle autorizzazioni appropriate. L'opzione di drill-through deve invece essere disabilitata se il modello si trova in uno stato non elaborato, indipendentemente dal fatto che il modello sia stato elaborato o meno in precedenza e disponga di contenuto. Per recuperare i dati del case del modello tramite il drill-through, la cache della struttura e del modello deve essere quella corrente.  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a>Utilizzare il drill-through nel Visualizzatore Microsoft Decision Trees  
  
1.  In Progettazione modello di data mining selezionare un modello di albero delle decisioni e selezionare **Esplora modello** per aprire il modello nel **Visualizzare Microsoft Decision Trees**. In SQL Server Management Studio fare clic con il pulsante destro del mouse sul modello e selezionare **Sfoglia**  
  
2.  Fare clic con il pulsante destro del mouse su qualsiasi nodo del grafico dell'albero e selezionare **Drill-through**.  
  
3.  Selezionare una delle opzioni seguenti: **Solo colonne modello** o **Colonne struttura e modello**. Se non si dispone delle autorizzazioni necessarie, è possibile che un'opzione non sia disponibile.  
  
4.  Verrà visualizzata la finestra di dialogo **Drill-through** contenente i dati del case e/o i dati della struttura. La barra del titolo della finestra di dialogo contiene inoltre una descrizione del nodo da cui è stata eseguita la query drill-through.  
  
5.  Fare clic con il pulsante destro del mouse in qualsiasi punto nei risultati e selezionare **Copia tutto** per salvare i risultati negli Appunti.  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a>Utilizzare il drill-through nel Visualizzatore Microsoft Clustering  
  
1.  In Progettazione modello di data mining selezionare un modello di clustering e selezionare **Esplora modello** per aprire il modello nel **Visualizzare Microsoft Clustering**. In SQL Server Management Studio fare clic con il pulsante destro del mouse sul modello e selezionare **Sfoglia**.  
  
2.  Nella scheda **Cluster** fare clic con il pulsante destro del mouse su un nodo qualsiasi.  
  
3.  Selezionare **Drill-through**, quindi scegliere una delle opzioni seguenti: **Solo colonne modello** o **Colonne struttura e modello**. Se non si dispone delle autorizzazioni necessarie, è possibile che un'opzione non sia disponibile.  
  
4.  Verrà visualizzata la finestra di dialogo **Drill-through** contenente i dati del case e/o i dati della struttura. La barra del titolo della finestra di dialogo contiene inoltre una descrizione del cluster per i case.  
  
5.  Fare clic con il pulsante destro del mouse in qualsiasi punto nei risultati e selezionare **Copia tutto** per salvare i risultati negli Appunti.  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a>Utilizzare il drill-through nel Visualizzatore Microsoft Association Rules  
  
1.  In Progettazione modello di data mining selezionare un modello di associazione e selezionare **Esplora modello** per aprire il modello nel **Visualizzare Microsoft Association Rules**. In SQL Server Management Studio fare clic con il pulsante destro del mouse sul modello e selezionare **Sfoglia**  
  
2.  Nella scheda **Regole** fare clic con il pulsante destro del mouse sulla riga di una regola. Nella scheda **Set di elementi** fare clic su una riga che contiene un set di elementi.  
  
3.  Selezionare **Drill-through**, quindi scegliere una delle opzioni seguenti: **Solo colonne modello** o **Colonne struttura e modello**. Se non si dispone delle autorizzazioni necessarie, è possibile che un'opzione non sia disponibile.  
  
4.  Verrà visualizzata la finestra di dialogo **Drill-through** contenente i dati del case e/o i dati della struttura. La barra del titolo della finestra di dialogo contiene inoltre una descrizione del nome della regola.  
  
5.  Fare clic con il pulsante destro del mouse in qualsiasi punto nei risultati e selezionare **Copia tutto** per salvare i risultati dei case completi negli Appunti. È anche possibile selezionare **Copia** per copiare soltanto il case selezionato. Se il modello contiene una colonna di una tabella nidificata, verrà incollato solo il nome della colonna della tabella nidificata. Per recuperare i valori dei dati all'interno della colonna della tabella nidificata per ogni case, è necessario creare una query sul contenuto del modello.  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a>Utilizzare il drill-through nel Visualizzatore Microsoft Sequence Clustering  
  
1.  In Progettazione modello di data mining selezionare un modello di clustering e selezionare **Esplora modello** per aprire il modello nel **Visualizzare Microsoft Clustering**. In SQL Server Management Studio fare clic con il pulsante destro del mouse sul modello e selezionare **Sfoglia**.  
  
2.  Nella scheda **Diagramma dei cluster**fare clic con il pulsante destro del mouse su qualsiasi nodo che rappresenta un cluster. Nella scheda **Profili cluster** fare clic in qualsiasi punto di un profilo cluster o nel cluster che rappresenta il popolamento totale del modello.  
  
3.  Selezionare **Drill-through**, quindi scegliere una delle opzioni seguenti: **Solo colonne modello** o **Colonne struttura e modello**. Se non si dispone delle autorizzazioni necessarie, è possibile che un'opzione non sia disponibile.  
  
4.  Verrà visualizzata la finestra di dialogo **Drill-through** contenente i dati del case e/o i dati della struttura. La barra del titolo della finestra di dialogo contiene inoltre una descrizione del cluster per i case.  
  
5.  Fare clic con il pulsante destro del mouse in qualsiasi punto nei risultati e selezionare **Copia tutto** per salvare i risultati negli Appunti. Se il modello contiene una colonna di una tabella nidificata, verrà incollato solo il nome della colonna della tabella nidificata. Per recuperare i valori dei dati all'interno della colonna della tabella nidificata per ogni case, è necessario creare una query sul contenuto del modello.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività del visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Drill-through sui modelli di Data Mining](../../analysis-services/data-mining/drillthrough-on-mining-models.md)   
 [Drill-through sulle strutture di Data Mining](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
