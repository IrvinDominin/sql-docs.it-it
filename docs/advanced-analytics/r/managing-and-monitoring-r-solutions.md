---
title: Gestione e monitoraggio di soluzioni di machine learning | Documenti Microsoft
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 65398ab522f7a39aae08b1f438d2fa59291e4e8f
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2018
---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>Gestione e monitoraggio di soluzioni di machine learning
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In questo articolo descrive le funzionalità di SQL Server Machine Learning Services rilevanti per gli amministratori di database è necessario procedere con le soluzioni R e Python.

**Si applica a:** R Services SQL Server 2016, SQL Server 2017 di Machine Learning Services

## <a name="security"></a>Sicurezza

Gli amministratori di database devono fornire l'accesso ai dati non solo per gli esperti di dati, ma a un'ampia gamma di sviluppatori di report, analisti aziendali e fruitori dei dati aziendali. L'integrazione di R (e ora Python) in SQL Server offre numerosi vantaggi all'amministratore di database che supporta il ruolo della scienza dei dati.

+ L'architettura di [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] mantiene sicuri i database e isola l'esecuzione delle sessioni R dal funzionamento dell'istanza del database.

+ È possibile specificare gli utenti autorizzati a eseguire gli script R e verificare che i dati usati nei processi R siano gestiti usando gli stessi ruoli di sicurezza definiti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

+ L'amministratore del database può utilizzare i ruoli per gestire l'installazione dei pacchetti R e l'esecuzione di script R e Python.

Per altre informazioni, vedere le risorse seguenti:

+ [Considerazioni sulla sicurezza per il runtime R in SQL Server](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [Cenni preliminari sulla sicurezza di R](../r/security-overview-sql-server-r.md)

+ [Cenni preliminari sulla sicurezza di Python](../python/security-overview-sql-server-python-services.md)

+ [Installazione e gestione dei pacchetti R](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>Configurazione e gestione

Gli amministratori del database devono integrare progetti e priorità in concorrenza all'interno di un singolo punto di contatto: il server di database. Devono supportare analitica, mantenendo l'integrità degli archivi dati operativi e dei report. L'integrazione di machine learning con SQL Server offre numerosi vantaggi all'amministratore di database, che viene utilizzato sempre più di un ruolo fondamentale nella distribuzione di un'infrastruttura efficiente per l'analisi scientifica dei dati.

+ Le sessioni di R e Python vengono eseguite in un processo separato per garantire che il server continui a funzionare normalmente anche se il runtime dello script esterno presenta problemi.

+ Account con privilegi limitati utente fisico vengono utilizzati per contenere e isolare attività dello script esterno.

+ L'amministratore di database è possibile utilizzare strumenti di gestione di risorse SQL Server standard per controllare la quantità di risorse allocate al runtime di R, per evitare che calcoli grande da entità possano compromettere le prestazioni complessive del server.

Per altre informazioni, vedere le risorse seguenti:

+ [Governance delle risorse per R Services](../r/resource-governance-for-r-services.md)

+ [Configurare e gestire Advanced Extensions Analitica](../r/configure-and-manage-advanced-analytics-extensions.md)
