---
title: Eliminare una vista origine dati (Analysis Services) | Documenti Microsoft
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
- deleting data source views
- data source views [Analysis Services], deleting
- removing data source views
ms.assetid: ae3f5ca0-ecbf-4b52-8386-eb457719d854
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2ba0ddbe0a7b3dc2768b76f09852b311c46e846b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="delete-a-data-source-view-analysis-services"></a>Eliminare una vista origine dati (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Se non si usa più una vista origine dati in un progetto OLAP, è possibile eliminarla dal progetto in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 L'eliminazione di una vista origine dati è permanente. Non è possibile ripristinare una vista origine dati eliminata in un progetto o database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Non è possibile eliminare viste origine dati da cui dipendono altri oggetti da un database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] aperto da [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online. Per eliminare una vista origine dati da un progetto connesso o da un database in esecuzione in un server, è necessario eliminare innanzitutto tutti gli oggetti nel database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che dipendono da tale vista prima di eliminare la vista origine dati stessa.  
  
 Se si elimina una vista origina dati, gli altri oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] da cui dipendono non saranno validi pertanto, prima di eliminare la vista origine dati, si esaminerà l'elenco di oggetti che diventeranno non validi una volta rimossa tale vista. Esaminare con attenzione l'elenco per assicurarsi che non siano inclusi oggetti che si prevede di utilizzare ancora.  
  
 ![Eliminare la finestra di dialogo oggetti](../../analysis-services/multidimensional-models/media/ssas-olapdsv-deleteobjects.gif "la finestra di dialogo Elimina oggetti")  
  
## <a name="see-also"></a>Vedere anche  
 [Viste origine dati nei modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Modificare le proprietà in una vista origine dati &#40; Analysis Services &#41;](../../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
