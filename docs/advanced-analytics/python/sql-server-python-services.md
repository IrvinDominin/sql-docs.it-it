---
title: Machine Learning servizi con Python | Documenti Microsoft
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: python
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 7051781664efd2924dcb187d456197bc9bc88686
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="machine-learning-services-with-python"></a>Servizi di Machine Learning con Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Python è un linguaggio che offre una notevole flessibilità e potenza per un'ampia gamma di attività di apprendimento automatico. Librerie open source per Python includono diverse piattaforme per le reti neurali personalizzabile, nonché le librerie comuni per l'elaborazione in linguaggio naturale. A questo punto, il diffuso linguaggio è supportato in SQL Server 2017 CTP 2.0 e versioni successive.

Poiché Python è integrato con il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] motore di database, è possibile mantenere analitica dati ed eliminare i costi e i rischi di protezione associati allo spostamento dei dati.  È possibile distribuire soluzioni di apprendimento macchina basate su Python con strumenti familiari pratici, ad esempio Visual Studio. Le applicazioni di produzione è possono ottenere stime, modelli, o elementi visivi di runtime di Python 3,5 semplicemente chiamando una T-SQL stored procedure.

Questa versione include la distribuzione Anaconda di Python, nonché il nuovo [revoscalepy](../python/what-is-revoscalepy.md) libreria, per migliorare la scalabilità e prestazioni del computer di soluzioni di apprendimento.

È possibile installare tutto ciò che occorre per iniziare a utilizzare Python tramite l'installazione di SQL Server 2017:

+ **Machine Learning Services (In-Database):** installare questa funzionalità, con il motore di database di SQL Server, attivare l'esecuzione sicura degli script Python di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.
  
     Quando si seleziona questa funzionalità, le estensioni vengono installate nel motore di database per supportare l'esecuzione di script Python e viene creato un nuovo servizio, il [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], per gestire le comunicazioni tra il runtime di Python e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] istanza.

+ **Machine Learning Server (Standalone):** se non è necessario l'integrazione di SQL Server, installare questa funzionalità per ottenere il supporto di Python e R per distribuita machine learning. È inoltre possibile distribuire la soluzione di Python come servizio web tramite **mrsdeploy**.
  
     Non installare questa funzionalità nello stesso computer che esegue servizi di SQL Server Machine Learning.


## <a name="additional-resources"></a>Risorse aggiuntive

[Impostare i servizi nel Database di apprendimento automatico di Python](setup-python-machine-learning-services.md)

[Esercitazioni di Python](../tutorials/sql-server-python-tutorials.md)
