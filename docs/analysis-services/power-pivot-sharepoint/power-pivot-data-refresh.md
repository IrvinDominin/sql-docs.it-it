---
title: Power Pivot Data Refresh | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2647d94f0f1d8edc1d5c6ef9b364167f330e30a2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981443"
---
# <a name="power-pivot-data-refresh"></a>Aggiornamento dati Power Pivot
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dopo avere creato una cartella di lavoro che contiene dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , è possibile aggiornare periodicamente i dati rieseguendo una query o un comando per ottenere informazioni aggiornate dalle origini usate in origine per creare la cartella di lavoro. Questo processo, denominato **aggiornamento dati**, consente di aggiornare i dati su richiesta in [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]o come operazione pianificata eseguita come processo di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un server applicazioni in una farm di SharePoint. Per altre informazioni, vedere:  
  
-   [Aggiornamento dati PowerPivot con SharePoint 2010](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [Configurare Power Pivot (Power Pivot per SharePoint) Account di aggiornamento dati automatico](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Configurare le credenziali archiviate per l'aggiornamento di dati Power Pivot (Power Pivot per SharePoint)](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [Pianificare un aggiornamento di dati (Power Pivot per SharePoint)](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [Visualizzare la cronologia dell'aggiornamento dati &#40;Power Pivot per SharePoint&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] e SharePoint Server 2013 Excel Services utilizzata un'architettura diversa per l'aggiornamento di dati di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] modelli di dati. L'architettura supportata da SharePoint 2013 usa Excel Services come componente principale per caricare modelli di dati [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] . L'architettura di aggiornamento dati usata in precedenza era basata su un server che eseguiva il servizio di sistema di [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modalità SharePoint per caricare i modelli di dati. Per ulteriori informazioni, vedere quanto segue:  
>   
>  -   [Aggiornamento dati PowerPivot con SharePoint 2013](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [Aggiornare le cartelle di lavoro e l'aggiornamento dati pianificato &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
