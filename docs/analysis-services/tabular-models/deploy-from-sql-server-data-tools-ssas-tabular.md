---
title: Distribuire da SQL Server Data Tools | Documenti Microsoft
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.deploystatus.f1
ms.assetid: 67dde3fe-ba43-41f3-b56c-c656029ee93f
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c009ba69247d754c95f98732f41e4023db0fcaa4
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/23/2018
---
# <a name="deploy-from-sql-server-data-tools"></a>Distribuire da SQL Server Data Tools
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
Utilizzare le attività in questo argomento per distribuire una soluzione di modello tabulare utilizzando il comando Distribuisci in SSDT.  
  
##  <a name="bkmk_deploy"></a> Configurare le proprietà Opzioni di distribuzione e Server di distribuzione  
 Prima di distribuire tale soluzione, è necessario innanzitutto specificare le proprietà Opzioni di distribuzione e Server di distribuzione. Per ulteriori informazioni sulle impostazioni e le proprietà di distribuzione, vedere [distribuzione della soluzione di modello tabulare](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md).  
  
#### <a name="to-configure-options-and-properties"></a>Per configurare le proprietà e opzioni  
  
1.  In SSDT in **Esplora**, fare doppio clic sul nome del progetto e quindi fare clic su **proprietà**.  
  
2.  Nel  **\<nome progetto > proprietà** finestra di dialogo, nella **opzioni di distribuzione**, specificare le impostazioni delle proprietà se diverse dalle impostazioni predefinite.  
  
    > [!NOTE]  
    >  Per i modelli in modalità cache, in corrispondenza di **Modalità query** è sempre selezionata l'opzione **In-Memory**.  
  
    > [!NOTE]  
    >  Non è possibile specificare **Impostazioni di rappresentazione** per i modelli in modalità DirectQuery.  
  
3.  In **Server di distribuzione**specificare le impostazioni delle proprietà **Server** (nome), **Edizione**, **Database** (nome) e **Nome cubo** , se diverse dalle impostazioni predefinite, quindi fare clic su **OK**.  
  
> [!NOTE]  
>  È inoltre possibile specificare l'impostazione della proprietà Server di distribuzione predefinito in modo che tutti i nuovi progetti creati vengano distribuiti automaticamente nel server specificato. Per ulteriori informazioni, vedere [configurare le proprietà di modellazione e distribuzione dei dati predefinite](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md).  
  
##  <a name="bkmk_deploy_proc"></a> Distribuire un modello tabulare  
  
#### <a name="to-deploy-a-tabular-model"></a>Per distribuire un modello tabulare
  
-   In SSDT, sul **compilare** menu, fare clic su **Distribuisci \<nome progetto >**.  
  
     Verrà visualizzata la finestra di dialogo **Distribuisci** e verrà fornita l'indicazione dello stato della distribuzione dei metadati e dell'elaborazione di ogni tabella inclusa nel modello, a meno che la proprietà Opzione di elaborazione non sia impostata su Non elaborare. Al termine del processo di distribuzione, utilizzare SSMS per connettersi all'istanza di Analysis Services e verificare che il nuovo oggetto di database modello è stato creato o un client di creazione report di applicazione per connettersi al modello distribuito.  
  
##  <a name="bkmk_deploy_status"></a> Stato distribuzione  
 La finestra di dialogo **Distribuisci** consente di monitorare lo stato di un'operazione di distribuzione. Inoltre è possibile arrestare un'operazione di distribuzione.  
  
 **Stato**  
 Viene indicato se l'operazione di distribuzione ha avuto esito positivo o negativo.  
  
 **Dettagli**  
 Vengono elencati gli elementi dei metadati distribuiti, lo stato di ogni elemento dei metadati e viene fornito un messaggio relativo a eventuali problemi.  
  
 **Arresta distribuzione**  
 Fare clic su questa opzione per arrestare l'operazione di distribuzione. Questa opzione è utile se l'operazione di distribuzione è troppo lunga o se si sono verificati troppi errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione della soluzione di modello tabulare](../../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)   
 [Configurare la modellazione dei dati e le proprietà di distribuzione predefinite](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
  
  
