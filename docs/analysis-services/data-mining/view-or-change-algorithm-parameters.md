---
title: Visualizzazione o modifica i parametri dell'algoritmo | Documenti Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49cdffc9723f7d3489f84d7f40e6c0eb24150f52
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="view-or-change-algorithm-parameters"></a>Visualizzare o modificare i parametri dell'algoritmo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  È possibile modificare i parametri forniti con gli algoritmi utilizzati per compilare modelli di data mining per personalizzare i risultati del modello.  
  
 I parametri dell'algoritmo forniti in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non modificano solo le proprietà del modello: possono essere usati per modificare in modo fondamentale la modalità di elaborazione, raggruppamento e visualizzazione dei dati. Ad esempio, è possibile utilizzare i parametri dell'algoritmo per effettuare le operazioni seguenti:  
  
-   Modificare il metodo di analisi, ad esempio il metodo di clustering.  
  
-   Controllare il comportamento di selezione delle funzionalità.  
  
-   Specificare le dimensioni dei set di elementi o la probabilità delle regole.  
  
-   Controllare la diramazione e la profondità degli alberi delle decisioni.  
  
-   Specificare un valore di inizializzazione o le dimensioni del set di dati di controllo interni utilizzato per la creazione del modello.  
  
 I parametri forniti per ogni algoritmo variano notevolmente; per un elenco dei parametri che è possibile impostare per ogni algoritmo, vedere gli argomenti di riferimento tecnici in questa sezione: [Algoritmi di data mining &#40;Analysis Services - Data Mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
### <a name="change-an-algorithm-parameter"></a>Modificare un parametro di un algoritmo  
  
1.  Nella scheda **Modelli di data mining** di Progettazione modelli di data mining in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]fare clic con il pulsante destro del mouse sul modello di data mining per il quale si vuole ottimizzare l'algoritmo e quindi scegliere **Imposta parametri algoritmo**.  
  
     Verrà visualizzata la finestra di dialogo **Parametri algoritmo** .  
  
2.  Nella colonna **Valore** impostare un nuovo valore per l'algoritmo che si vuole modificare.  
  
     Se non si immette un valore nella colonna **Valore** , in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene usato il valore predefinito del parametro. La colonna **Intervallo** descrive i valori che è possibile immettere.  
  
3.  Scegliere **OK**.  
  
     Il parametro dell'algoritmo viene impostato con il nuovo valore. Le modifiche al parametro non verranno applicate al modello di data mining fino a quando non si rielabora il modello.  
  
### <a name="view-the-parameters-used-in-an-existing-model"></a>Visualizzare i parametri utilizzati in un modello esistente  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aprire una finestra di query DMX.  
  
2.  Digitare una query come la seguente:  
  
    ```  
    select MINING_PARAMETERS   
    from $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = '<model name>'  
  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate e attività di modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  
