---
title: Configurare le proprietà della relazione attributo | Documenti Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a7270dd698dfb8d3d3002c302186e97b912044f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023148"
---
# <a name="attribute-relationships---configure-attribute-properties"></a>Relazioni tra attributi - configurare le proprietà di attributo
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Nella tabella seguente vengono elencate e descritte le proprietà di una relazione tra attributi.  
  
|Proprietà|Description|  
|--------------|-----------------|  
|Attribute|Nome dell'attributo.|  
|Cardinalità|Indica la cardinalità della relazione. Il valore è Many per una relazione molti-a-uno e One per una relazione uno-a-uno. Il valore predefinito è Many. In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]la proprietà Cardinality non ha alcun effetto. L'uso di tale proprietà è riservato per un'implementazione futura.|  
|Nome|Nome descrittivo dell'attributo.|  
|RelationshipType|Indica se le relazioni tra membri cambiano nel tempo. Il valore di questa proprietà è Rigid se le relazioni tra membri non cambiano nel tempo o Flexible in caso contrario. Il valore predefinito è Flexible. Se si definisce una relazione flessibile, le aggregazioni verranno eliminate e ricalcolate come parte di un aggiornamento incrementale. Non verranno invece eliminate se vengono aggiunti solo nuovi membri. Se viene definita una relazione rigida, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di mantenere le aggregazioni quando la dimensione viene aggiornata in modo incrementale. Se una relazione definita rigida viene modificata, in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verrà generato un errore durante l'aggiornamento incrementale. L'impostazione corretta delle relazioni e delle rispettive proprietà determina un miglioramento delle prestazioni durante l'esecuzione di query e i processi di elaborazione.|  
|Visible|Determina la visibilità della relazione tra attributi. Il valore è True o False. Il valore predefinito è True.|  
  
  
