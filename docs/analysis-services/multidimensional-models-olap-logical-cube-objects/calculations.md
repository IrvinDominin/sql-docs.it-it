---
title: Calcoli | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- calculations [Analysis Services]
- OLAP objects [Analysis Services], calculations
- MDX [Analysis Services], calculations
- calculations [Analysis Services], about calculations
- cubes [Analysis Services], calculations
ms.assetid: 6be84916-fd05-4efc-ab98-6adbbad80154
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: dd006ee1a6896e4b9bdd6264d16a8406786f8d39
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="calculations"></a>Calcoli
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Un calcolo è un'espressione MDX (Multidimensional Expressions) o script che viene utilizzato per definire un membro calcolato, un set denominato o un'assegnazione di ambito di un cubo in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I calcoli consentono di aggiungere oggetti definiti non dai dati del cubo, ma da espressioni che possono fare riferimento ad altre parti del cubo, ad altri cubi o persino a informazioni esterne al database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. I calcoli consentono di estendere le funzionalità di un cubo, aggiungendo flessibilità e potenza alle applicazioni di Business Intelligence. Per ulteriori informazioni sui calcoli di script, vedere [Introduzione alla creazione di script MDX in Microsoft SQL Server 2005](http://go.microsoft.com/fwlink/?LinkId=81892). Per ulteriori informazioni sui problemi di prestazioni relativi alle query e calcoli MDX, vedere il [Guida alle prestazioni di SQL Server 2005 Analysis Services](http://go.microsoft.com/fwlink/?LinkId=81621).  
  
## <a name="calculated-members"></a>Membri calcolati  
 Un membro calcolato è un membro il cui valore viene calcolato in fase di esecuzione utilizzando un'espressione MDX (Multidimensional Expressions) specificata dall'utente durante la definizione del membro stesso. Un membro calcolato è disponibile per le applicazioni di Business Intelligence come qualsiasi altro membro. I membri calcolati non aumentano le dimensioni del cubo dato che solo le definizioni vengono archiviate nel cubo, mentre il calcolo dei valori, necessario per rispondere alle query, viene eseguito in memoria.  
  
 È possibile definire membri calcolati per qualsiasi dimensione, inclusa la dimensione delle misure. I membri calcolati creati per la dimensione Measures vengono denominati "misure calcolate".  
  
 Sebbene i membri calcolati siano generalmente basati su dati già esistenti nel cubo, è possibile creare espressioni complesse combinando questi dati con operatori aritmetici, numeri e funzioni. È possibile utilizzare anche funzioni MDX, ad esempio LookupCube per accedere in altri cubi nel database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include librerie di funzione Visual Studio standardizzate ed è possibile utilizzare stored procedure per recuperare dati da origini diverse dal database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] corrente. Per ulteriori informazioni sulle stored procedure, vedere [la definizione di Stored procedure](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md).  
  
 Si supponga, ad esempio, che i dirigenti di una società di spedizioni desiderino determinare i tipi di merci più vantaggiosi da trasportare in base al profitto per unità di volume. A tale scopo, utilizzano un cubo Shipments contenente le dimensioni Cargo, Fleet e Time e le misure Price_to_Ship, Cost_to_Ship e Volume_in_Cubic_Meters. Il cubo, tuttavia, non contiene una misura per la redditività. In tal caso, è possibile creare nel cubo un membro calcolato come misura denominata Profit_per_Cubic_Meter combinando le misure esistenti nell'espressione seguente:  
  
```  
([Measures].[Price_to_Ship] - [Measures].[Cost_to_Ship]) /  
[Measures].[Volume_in_Cubic_Meters]  
```  
  
 Dopo aver creato il membro calcolato, la misura Profit_per_Cubic_Meter verrà visualizzata insieme alle altre alla successiva esplorazione del cubo Shipments.  
  
 Per creare membri calcolati, utilizzare il **calcolo**scheda in Progettazione cubi. Per ulteriori informazioni, vedere [creare membri calcolati](../../analysis-services/multidimensional-models/create-calculated-members.md)  
  
## <a name="named-sets"></a>Set denominati  
 Un set denominato è un'istruzione CREATE SET MDX che restituisce un set. L'espressione MDX viene salvata come parte della definizione di un cubo in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Un set denominato viene creato per il riutilizzo in query MDX e consente agli utenti aziendali di semplificare le query e utilizzare un nome di set anziché un'espressione set per le espressioni set complesse utilizzate di frequente. **Argomento correlato:** [creare set denominati](../../analysis-services/multidimensional-models/create-named-sets.md)  
  
## <a name="script-commands"></a>Comandi script  
 Un comando script è uno script MDX incluso nella definizione del cubo. I comandi script consentono di eseguire quasi tutte le operazioni supportate da MDX in un cubo, ad esempio la definizione dell'ambito di un calcolo da applicare solo a parte del cubo. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], gli script MDX possono essere applicato all'intero cubo o a sezioni specifiche del cubo, in punti specifici durante l'esecuzione dello script. L'istruzione CALCULATE, che è il comando script predefinito, popola le celle del cubo con dati aggregati in base all'ambito predefinito.  
  
 L'ambito predefinito è l'intero cubo, ma è possibile definire un ambito più limitato, noto come sottocubo, e quindi applicare uno script MDX solo a tale area del cubo. L'istruzione SCOPE definisce l'ambito di tutte le successive espressioni e istruzioni MDX nello script di calcolo fino a quando l'ambito non viene terminato o ridefinito. Viene quindi utilizzata l'istruzione THIS per applicare un'espressione MDX all'ambito corrente. È possibile utilizzare l'istruzione BACK_COLOR per applicare alle celle nell'ambito corrente un colore di sfondo che agevoli le operazioni di debug.  
  
 È ad esempio possibile utilizzare un comando script per allocare obiettivi di vendita ai dipendenti, suddivisi per periodo di tempo e territorio di vendita, in base ai valori ponderati delle vendite in un periodo di tempo precedente.  
  
## <a name="see-also"></a>Vedere anche  
 [Calcoli nei modelli multidimensionali](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  
