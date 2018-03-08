---
title: Grafico profitti (Analysis Services - Data Mining) | Documenti Microsoft
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
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e1bfda7f42bdc4423ee1ea1bc0ad2d59abe26347
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="profit-chart-analysis-services---data-mining"></a>Grafico profitti (Analysis Services - Data mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
In un grafico dei profitti viene visualizzata la redditività associata all'utilizzo di un modello di data mining. Si supponga, ad esempio, che il modello preveda quali sono i clienti che una società dovrebbe contattare in uno scenario aziendale. In tal caso, sarebbe necessario aggiungere le informazioni del grafico dei profitti in merito al costo della campagna di mailing diretto. Successivamente, nel grafico completato verrà visualizzato il profitto stimato della campagna indirizzata ai clienti corretti, rispetto a quello di una campagna con clienti contattati casualmente.  
  
## <a name="build-a-profit-chart"></a>Creare un grafico dei profitti  
 Un grafico dei profitti è simile a uno di accuratezza. Iniziare creando un grafico di accuratezza e quindi aggiungere le informazioni sui costi e i profitti.  
  
 Per creare un grafico dei profitti, è necessario disporre di un modello esistente.  
  
 Per questo esempio, è stato utilizzato il modello di albero delle decisioni di Mailing diretto. Il modello identifica i clienti che con una certa probabilità acquisteranno una bicicletta. È possibile applicare il **Grafico profitti** per determinare il numero di clienti di destinazione per ottimizzare il profitto.  
  
 Se non si dispone del modello di esempio, è possibile crearlo svolgendo l' [Esercitazione di base sul data mining](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
1.  Aprire il generatore del grafico di accuratezza del modello di data mining.  
  
    -   In SQL Server Management Studio fare clic con il pulsante destro del mouse sul modello e scegliere **Visualizza grafico di accuratezza**.  
  
    -   In SQL Server Data Tools aprire il progetto in cui è stato creato il modello e fare clic sulla scheda **Grafico accuratezza modello di data mining** .  
  
2.  Nella scheda **Selezione input** selezionare il modello e scegliere il valore dell'attributo stimabile.  
  
     Per questo scenario specifico, si è interessati solo alla redditività della stima accurata di un valore: [Bike buyer] =1.  
  
     Esistono tuttavia altri scenari in cui si sarà ugualmente interessati alla stima corretta dei valori falsi. Ad esempio, il costo di un falso positivo in un test di diagnosi medica può essere significativo e deve essere incluso nella redditività della stima, oltre al costo dei falsi negativi. In questi scenari sarà necessario misurare tutti gli esiti.  
  
3.  Selezionare un set di dati per il testing. Per questo esempio, selezionare il set di dati di testing.  
  
4.  Fare clic sulla scheda **Grafico di accuratezza** .  
  
     Verrà generato automaticamente un grafico di accuratezza.  
  
5.  Per convertire questo grafico in un grafico dei profitti, selezionare **Grafico profitti** nell'elenco **Tipo di grafico** .  
  
6.  Dopo avere scelto il grafico dei profitti come tipo di grafico, verrà aperta automaticamente la finestra di dialogo **Impostazione grafico profitti** .  
  
     Questa finestra di dialogo consente di specificare i costi e i vantaggi associati a una campagna di mailing diretto. Per il grafico mostrato in questi esempi, sono stati utilizzati i valori seguenti:  
  
    |Impostazione|Valore|Commenti|  
    |-------------|-----------|--------------|  
    |**Popolazione**|20,000|Impostare il valore per la popolazione target totale<br /><br /> Il database può contenere molti clienti, ma per risparmiare sulle spese di mailing è possibile scegliere di individuare come destinatari solo i primi 20.000 clienti aventi maggiore probabilità di rispondere. È possibile ottenere questo elenco eseguendo una query di stima e ordinando i dati in base alla probabilità restituita dal modello predittivo.|  
    |**Costi fissi**|500|Immettere il costo una tantum per la configurazione di una campagna di mailing diretto per 20.000 persone. Nel costo possono essere incluse le spese di stampa o le spese di configurazione di una campagna di posta elettronica.|  
    |**Costi singolo contatto**|3|Immettere il costo unitario per la campagna di mailing diretto<br /><br /> Questa quantità verrà moltiplicata per un numero minore o uguale a 20.000, a seconda del numero di clienti stimati dal modello come buone possibilità.|  
    |**Ricavi per singolo contatto**|400|Immettere un valore che rappresenta la quantità di profitto o reddito che può essere previsto da un risultato positivo In questo caso, si partirà dal presupposto che la spedizione di un catalogo genera un acquisto di accessori o di biciclette per una media di € 400.<br /><br /> Questo importo verrà utilizzato per prevedere il profitto complessivo associato ai case con probabilità elevata.|  
  
7.  Dopo avere impostato i parametri obbligatori, fare clic su **OK**.  
  
8.  Il grafico verrà aggiornato per mostrare la curva dei profitti.  
  
## <a name="understanding-the-profit-chart"></a>Informazioni sul grafico dei profitti  
 Nel diagramma seguente viene mostrato il grafico basato su questi parametri. L'asse Y del grafico rappresenta i profitti, mentre l'asse X rappresenta la percentuale di clienti contattata mediante la campagna di marketing diretto.  
  
 Come illustrato, è possibile utilizzare un grafico dei profitti per confrontare più modelli, purché in tutti venga stimato lo stesso attributo discreto.  
  
 ![confronto tra tre modelli del grafico profitti](../../analysis-services/data-mining/media/dm14-profitchartupdated.gif "profitto grafico di confronto tra tre modelli")  
  
 Si noti la linea verticale grigia nel grafico. Quando si fa clic e si trascina la riga, la descrizione comando mostra la percentuale della popolazione di destinazione inclusa sotto la curva in corrispondenza di quel punto.  
  
 Man mano che si sposta la linea, la **Legenda data mining** viene aggiornata per visualizzare il valore in percentuale, un punteggio per il profitto e la probabilità di stima associata alla percentuale di popolazione in corrispondenza della linea verticale grigia.  
  
 Se, ad esempio, si utilizza questo modello per stabilire a chi conviene inviare il materiale promozionale, è possibile decidere di selezionare come destinatari il 25% della popolazione, in base alle probabilità di stima. Tuttavia, l'area sotto la curva dei profitti del grafico risulta maggiore tra il 40 e il 70 percento, indicando così che indirizzando la campagna a un maggior numero di persone è possibile ottimizzare il ritorno anche se risponde una percentuale complessiva di destinatari inferiore.  
  
## <a name="saving-charts"></a>Salvataggio di grafici  
 Quando si crea un grafico di accuratezza o un grafico dei profitti, nel server non viene creato alcun oggetto. Al contrario, le query vengono eseguite su un modello esistente e i risultati vengono visualizzati nel visualizzatore. Per salvare i risultati, è necessario copiare il grafico o i risultati in Excel o in un altro file.  
  
## <a name="related-content"></a>Contenuto correlato  
 Negli argomenti seguenti sono contenute ulteriori informazioni su come sia possibile compilare e utilizzare i grafici di accuratezza.  
  
|Argomento|Collegamenti|  
|------------|-----------|  
|Viene fornita una procedura dettagliata relativa alla creazione di un grafico di accuratezza per il modello Targeted Mailing.|[Esercitazione di base di Data Mining](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)<br /><br /> [Test dell'accuratezza con i grafici di accuratezza &#40; Esercitazione di base di Data Mining &#41;](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)|  
|Vengono illustrati i tipi di grafici correlati.|[Grafico di accuratezza &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)<br /><br /> [Matrice di classificazione &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)<br /><br /> [Grafico a dispersione &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/scatter-plot-analysis-services-data-mining.md)|  
|Viene descritta la convalida incrociata per modelli e strutture di data mining.|[La convalida incrociata &#40; Analysis Services - Data Mining &#41;](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)|  
|Vengono descritti i passaggi per la creazione di grafici di accuratezza e di altri grafici simili.|[Test e convalida le attività e procedure relative alla &#40; Data Mining &#41;](../../analysis-services/data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Test e convalida &#40; Data Mining &#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Test dell'accuratezza con i grafici di accuratezza &#40; Esercitazione di base di Data Mining &#41;](http://msdn.microsoft.com/library/822d414b-4a39-473f-80c3-53476e30655a)  
  
  
