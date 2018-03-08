---
title: Opzioni di distribuzione dei modelli (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: non-specific
ms.reviewer: 
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
caps.latest.revision: 
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 649ebc2220f3e19806ec325886b8a0216cbf5a8e
ms.sourcegitcommit: 6ac1956307d8255dc544e1063922493b30907b80
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="model-deployment-options-master-data-services"></a>Opzioni di distribuzione dei modelli (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]quando si distribuisce un file di pacchetto di modello, è necessario decidere se distribuire un modello nuovo o clonato oppure se aggiornare un modello clonato in precedenza.  
  
## <a name="workflows"></a>Flussi di lavoro  
 Quando si utilizzano pacchetti di modello, vi sono due flussi di lavoro principali.  
  
-   Creare un pacchetto di un modello in un ambiente di testing e distribuire un clone del modello in un ambiente di produzione. Con il tempo, distribuire gli aggiornamenti dall'ambiente di testing all'ambiente di produzione.  
  
-   Creare un pacchetto di un modello e distribuirlo come nuovo modello nello stesso ambiente. In questo caso, è necessario assegnare al modello un nuovo nome.  
  
## <a name="options"></a>Opzioni  
 Nel database MDS ogni oggetto modello dispone di un identificatore univoco (ID). Questi ID sono inclusi nei pacchetti di distribuzione dei modelli. Quando si distribuisce il pacchetto, è necessario scegliere come utilizzare questi ID.  
  
 Le informazioni nella tabella seguente consentono di determinare la scelta da effettuare quando si distribuisce un modello utilizzando la Distribuzione guidata modello di Amministrazione sistema o lo strumento MDSModelDeploy.  
  
|Opzione|Description|Note|  
|------------|-----------------|-----------|  
|Nuovo|Consente di creare un nuovo modello con un nome univoco. Per tutti gli oggetti modello vengono creati nuovi identificatori.|Se si crea un nuovo modello con nuovi identificatori, non è possibile utilizzare gli strumenti di distribuzione del modello per applicare aggiornamenti al modello in un secondo momento. Quando si utilizza la procedura guidata nell'applicazione Web per distribuire un pacchetto di modello, è possibile creare un nuovo modello solo se è già presente un modello con lo stesso nome o ID.|  
|Clona|Consente di creare un nuovo modello che è un clone esatto del modello nel pacchetto. Questa opzione funziona solo se il modello non è presente (con lo stesso nome o identificatore) nell'ambiente di destinazione. Utilizzare la clonazione quando si desidera disporre dello stesso modello in più ambienti e aggiornare il modello clonato nel tempo.|Si tratta del comportamento predefinito della procedura guidata nell'applicazione Web. Se è già presente un modello con lo stesso nome o ID, viene richiesto di creare invece un nuovo modello.|  
|Update|Consente di aggiornare un modello esistente con il modello nel pacchetto. Gli identificatori devono essere gli stessi in entrambi i modelli. Questa opzione consente di aggiornare un modello clonato in precedenza.|È possibile aggiornare solo i modelli precedentemente clonati. (I nomi e gli ID devono corrispondere).|  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)   
 [Distribuire un pacchetto di distribuzione di modelli tramite la procedura guidata](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)   
 [Distribuzione di modelli &#40;Master Data Services&#41;](../master-data-services/deploying-models-master-data-services.md)  
  
  
