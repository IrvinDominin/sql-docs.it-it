---
title: Definire una relazione di tipo regolare e le proprietà di relazione di tipo regolare | Documenti Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 62820860d8479776abc232f9355367cc35da1966
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36067491"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Definire una relazione di tipo Regolare e le relative proprietà
  Quando si definisce un nuovo gruppo di misure o una nuova dimensione del cubo, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tenta di rilevare la presenza di una relazione di tipo Regolare e quindi imposta l'utilizzo della dimensione su `Regular`. È possibile visualizzare o modificare la relazione di una dimensione regolare nella scheda **Utilizzo dimensioni** di Progettazione cubi.  
  
 Quando si definisce la relazione tra una dimensione del cubo e un gruppo di misure, si specifica inoltre l'attributo di granularità per la relazione. L'attributo di granularità definisce il livello di dettaglio più basso disponibile nel cubo per la dimensione, che in genere corrisponde all'attributo chiave per la dimensione. Talvolta, tuttavia, potrebbe essere necessario impostare diversamente la granularità di una particolare dimensione del cubo in un determinato gruppo di misure. Potrebbe ad esempio rivelarsi utile impostare l'attributo di granularità per la dimensione Time su Month anziché su Day, se si utilizza un gruppo di misure Sales Quotas o Budget. Quando si specifica l'attributo di granularità in base a un attributo diverso dall'attributo chiave, è necessario garantire che tutti gli altri attributi della dimensione siano collegati direttamente o indirettamente a quest'altro attributo tramite relazioni tra attributi. In caso contrario, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] non sarà in grado di eseguire correttamente l'aggregazione dei dati.  
  
  