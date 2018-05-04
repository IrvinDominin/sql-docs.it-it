---
title: I livelli di programmazione del modello tabulare per la compatibilità 1050 e 1103 | Documenti Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 0ceb461e-12c1-44ea-97ac-b99bf308676b
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 99d03c35c9f50d0d232814300f5a07bed289d47e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="tabular-model-programming-for-compatibility-levels-1050-through-1103"></a>Programmazione del modello tabulare per la compatibilità 1050 1103 tramite i livelli
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  I modelli tabulari utilizzano costrutti relazionali per modellare i dati di Analysis Services utilizzati dalle applicazioni analitiche e di report. Questi modelli vengono eseguiti in un'istanza di Analysis Services configurata per la modalità tabulare, utilizzando un motore di analisi in memoria per l'archiviazione in memoria e rapide scansioni di tabella in grado di aggregare e calcolare i dati in base alle esigenze.  
  
 Se i requisiti della soluzione BI personalizzata vengono meglio soddisfatti da un database modello tabulare, è possibile utilizzare qualsiasi libreria client di Analysis Services e interfaccia di programmazione per integrare l'applicazione con i modelli tabulari in un'istanza di Analysis Services. Per eseguire query e calcoli sui dati del modello tabulare, è possibile utilizzare il linguaggio MDX o DAX incorporato nel codice.  
  
 Per i modelli tabulari creati in versioni precedenti di Analysis Services, in particolari modelli con livelli di compatibilità 1050 e 1103, gli oggetti utilizzati a livello di codice in AMO, ADOMD.NET, XMLA o OLE DB sono fondamentalmente gli stessi per sia tabulare e soluzioni multidimensionali. In particolare, i metadati degli oggetti definiti per i modelli multidimensionali viene usato anche per i livelli di compatibilità tabulare 1050-1103.  
  
 A partire da SQL Server 2016, i modelli tabulari possono essere creati o aggiornati a livello di compatibilità 1200 o superiore, che usa metadati tabulari per definire il modello. I metadati e la programmabilità sono fondamentalmente diverse a questo livello. Vedere [tabulare del modello di programmazione 1200 a livello di compatibilità e successive](../../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md) e [Upgrade Analysis Services](../../database-engine/install-windows/upgrade-analysis-services.md) per ulteriori informazioni.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Annotazioni CSDL per Business Intelligence & #40; CSDLBI & #41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
 [Informazioni sul modello a oggetti tabulare alla compatibilità 1050 1103 tramite i livelli](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
 [Riferimento tecnico per le annotazioni di Business Intelligence per CSDL](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  

[Interfaccia IMDEmbeddedData](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/imdembeddeddata-interface.md)


  
  
