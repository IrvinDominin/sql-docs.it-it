---
title: La comprensione dell'analisi dello Script di distribuzione di servizi | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 84179762d2c4819fb5fc5f82ad6d0528ea689ecf
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38021426"
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Informazioni sullo script di distribuzione di Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Lo script di distribuzione XMLA generato dalla Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] include due sezioni:  
  
-   La prima parte dello script di distribuzione contiene i comandi necessari per creare, modificare o eliminare gli oggetti di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriati nel database di destinazione. Per impostazione predefinita, i file di input generati dal progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sono basati su una distribuzione incrementale. Lo script di distribuzione di XMLA avrà pertanto effetto solo sugli oggetti modificati o eliminati.  
  
-   La seconda parte dello script di distribuzione contiene i comandi necessari per elaborare soltanto gli oggetti creati o modificati nel server di destinazione (opzione Elaborazione predefinita) o per elaborare completamente il database di destinazione. Si può inoltre scegliere di non includere alcun comando di elaborazione nello script di distribuzione.  
  
 L'intero script di distribuzione può essere eseguito in una singola transazione o in più transazioni. Se lo script viene eseguito in più transazioni, la prima parte dello script viene eseguita come singola transazione e ogni oggetto viene elaborato nella relativa transazione.  
  
> [!IMPORTANT]  
>  Tramite la Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] è possibile distribuire oggetti solo in un singolo database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Non è possibile distribuire alcun oggetto o dato a livello del server.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione della Distribuzione guidata Analysis Services](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Informazioni sui file di input utilizzati per creare uno script di distribuzione](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  
