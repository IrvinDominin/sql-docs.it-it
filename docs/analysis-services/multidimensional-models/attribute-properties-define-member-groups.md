---
title: Definire gruppi di membri | Documenti Microsoft
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
- member groups [Analysis Services]
- grouping members
- DiscretizationMethod property
ms.assetid: 006cc915-c499-4781-b9a7-01ad31bebf6a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 36110a1967917adda6c06ca0e32d138639e1871e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2018
---
# <a name="attribute-properties---define-member-groups"></a>Attributo di proprietà: definire i gruppi di membri
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
Se un attributo include un numero elevato di membri, è possibile scegliere di raggruppare tali membri in bucket, riducendo il numero di membri visualizzati dagli utenti durante la ricerca dei dati in una gerarchia. È inoltre possibile determinare il numero di bucket in cui sono raggruppati i membri e impostare uno schema di denominazione per i bucket. Per altre informazioni, vedere [Raggruppare membri di attributo &#40;discretizzazione&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
 I membri vengono raggruppati impostando la proprietà **DiscretizationMethod**, accessibile tramite la finestra **Proprietà** di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Durante la creazione di gruppi di membri, le modifiche apportate non sono disponibili per gli utenti fino a quando non è stata elaborata la dimensione. Per altre informazioni, vedere [Elaborazione di un modello multidimensionale &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md).  
  
### <a name="to-create-member-groups"></a>Per creare gruppi di membri  
  
1.  Aprire la dimensione che si desidera utilizzare. Per impostazione predefinita, verrà visualizzata la scheda **Struttura dimensione** .  
  
2.  In **Attributi**fare clic con il pulsante destro del mouse sull'attributo di cui si vuole raggruppare i membri e quindi scegliere **Proprietà**.  
  
3.  Selezionare un metodo di raggruppamento dei membri nell'elenco a discesa accanto alla proprietà **DiscretizationMethod**. Per altre informazioni sulle impostazioni della proprietà **DiscretizationMethod**, vedere [Raggruppare membri di attributo &#40;discretizzazione&#41;](../../analysis-services/multidimensional-models/attribute-properties-group-attribute-members.md).  
  
  
