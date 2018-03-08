---
title: Progetto di servizi di distribuzione di un'analisi | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5d98bab3-3577-4143-b737-5196444a36ac
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: d6717a94aeacf2891c48050b6bb33f706cb2c2c0
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="lesson-2-5---deploying-an-analysis-services-project"></a>Lezione 2-5-distribuisce un progetto di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

Per visualizzare i dati del cubo e delle dimensioni relativi agli oggetti del cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial del progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial, è necessario distribuire il progetto in un'istanza specificata di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], quindi elaborare il cubo e le relative dimensioni. La *distribuzione* di un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] determina la creazione degli oggetti definiti in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. L'*elaborazione* degli oggetti in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] determina la copia dei dati delle origini dati sottostanti negli oggetti cubo. Per altre informazioni, vedere [Distribuire progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md) e [Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
In questa fase del processo di sviluppo il cubo viene in genere distribuito in un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in un server di sviluppo. Al termine dello sviluppo del progetto di Business Intelligence, si utilizza in genere la Distribuzione guidata [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per distribuire il progetto dal server di sviluppo a un server di produzione. Per altre informazioni, vedere [Distribuzione di soluzioni di modelli multidimensionali](../analysis-services/multidimensional-models/multidimensional-model-solution-deployment.md) e [Distribuire soluzioni di modelli tramite la Distribuzione guidata](../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md).  
  
Nell'attività successiva verranno esaminate le proprietà di distribuzione del progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial, quindi il progetto verrà distribuito nell'istanza locale di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
### <a name="to-deploy-the-analysis-services-project"></a>Per distribuire il progetto di Analysis Services  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto **Analysis Services Tutorial** e quindi scegliere **Proprietà**.  
  
    Verrà visualizzata la finestra di dialogo **Pagine delle proprietà** di Analysis Services Tutorial, in cui vengono illustrate le proprietà della configurazione Active(Development). È possibile definire più configurazioni, ognuna con proprietà diverse. Ad esempio, potrebbe rendersi necessario per uno sviluppatore configurare lo stesso progetto per la distribuzione in diversi computer di sviluppo e con diverse proprietà di sviluppo quali, ad esempio, proprietà di elaborazione o nomi di database diversi. Si noti il valore della proprietà **Percorso output** . Questa proprietà specifica la posizione in cui vengono salvati gli script di sviluppo XMLA per il progetto quando quest'ultimo viene compilato. Tali script vengono utilizzati per distribuire gli oggetti del progetto su un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
2.  Nel nodo **Proprietà di configurazione** fare clic su **Distribuzione**.  
  
    Esaminare le proprietà di sviluppo del progetto. Per impostazione predefinita, il modello del progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] configura un progetto di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] per la distribuzione incrementale di tutti i progetti nell'istanza predefinita di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nel computer locale, per creare un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] con lo stesso nome del progetto ed elaborare gli oggetti dopo la distribuzione utilizzando l'opzione di elaborazione predefinita. Per altre informazioni, vedere [Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md).  
  
    > [!NOTE]  
    > Se si desidera distribuire il progetto in un'istanza denominata di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] nel computer locale o a un'istanza in un server remoto, modificare il **Server** nome di proprietà all'istanza appropriata, ad esempio \<  *ServerName**>\\<**InstanceName * * >*.  
  
3.  Scegliere **OK**.  
  
4.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto **Analysis Services Tutorial** e scegliere **Distribuisci**. Potrebbe essere necessario attendere alcuni istanti.  
  
    > [!NOTE]  
    > Se si verificano errori durante la distribuzione, utilizzare SQL Server Management Studio per controllare le autorizzazioni per il database. L'account specificato per la connessione all'origine dati deve disporre di un accesso sull'istanza di SQL Server. Fare doppio clic sull'account di accesso per visualizzare le proprietà Mapping utenti. L'account deve avere le autorizzazioni db_datareader per il database **AdventureWorksDW2012** .  
  
    [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] consente di compilare e quindi di distribuire il progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial nell'istanza specificata di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] usando uno script di distribuzione. Lo stato di avanzamento della distribuzione viene visualizzato in due finestre: la finestra **Output** e la finestra **Stato distribuzione - Analysis Services Tutorial** .  
  
    Se necessario, aprire la finestra Output scegliendo **Output** dal menu **Visualizza** . Nella finestra **Output** viene visualizzato lo stato di avanzamento generale della distribuzione. La finestra **Stato distribuzione - Analysis Services Tutorial** offre informazioni dettagliate sui singoli passaggi della distribuzione. Per altre informazioni, vedere [Compilare progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md) e [Distribuire progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md).  
  
5.  Esaminare il contenuto delle finestre **Output** e **Stato distribuzione - Analysis Services Tutorial** per verificare che il cubo sia stato compilato, distribuito ed elaborato senza errori.  
  
6.  Per nascondere la finestra **Stato distribuzione - Analysis Services Tutorial** , fare clic sull'icona **Nascondi automaticamente** (a forma di puntina da disegno) sulla barra degli strumenti della finestra.  
  
7.  Per nascondere la finestra **Output** fare clic sull'icona **Nascondi automaticamente** sulla barra degli strumenti della finestra.  
  
In questo modo è stato distribuito il cubo [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial in un'istanza locale di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], quindi il cubo distribuito è stato elaborato.  
  
## <a name="next-task-in-lesson"></a>Attività successiva della lezione  
[Esplorazione del cubo](../analysis-services/lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>Vedere anche  
[Distribuire progetti di Analysis Services &#40; SSDT &#41;](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
[Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  
  
