---
title: Uso delle funzioni di profiling del codice R | Microsoft Docs
ms.custom: 
ms.date: 11/29/2016
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 132db249-b9f1-48f5-a63e-c9806cacc4af
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3aecbcf80a76fdfd84cca277f5f0de0f8dc7bb4e
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2018
---
# <a name="using-r-code-profiling-functions"></a>Uso delle funzioni di profiling del codice R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Oltre a usare risorse e strumenti di SQL Server per monitorare l'esecuzione di script R, è possibile usare gli strumenti per le prestazioni forniti da altri pacchetti R per ottenere altre informazioni sulle chiamate di funzioni interne. Questo argomento contiene un elenco di alcune risorse di base per iniziare. Per linee guida per utenti esperti, è consigliabile fare riferimento al capitolo sulle [prestazioni](http://adv-r.had.co.nz/Performance.html) del libro ""Advanced R"" di Hadley Wickham.

## <a name="using-rprof"></a>Uso di RPROF

*rprof* è una funzione inclusa nel pacchetto di base **utils**, caricato per impostazione predefinita. Un vantaggio di *rprof* è il fatto di eseguire il campionamento, riducendo il carico delle prestazioni sul monitoraggio.

Per usare il profiling R nel codice, chiamare questa funzione e specificarne i parametri, incluso il percorso del file di log che verrà scritto. Per informazioni dettagliate, vedere la Guida di *rprof*.

In generale, la funzione *rprof* opera scrivendo lo stack di chiamate in un file a intervalli specificati. È quindi possibile usare la funzione *summaryRprof* per elaborare il file di output. 

È possibile attivare o disattivare il profiling nel codice. Per attivare il profiling, sospenderlo e quindi riavviarlo, è necessario usare una sequenza di chiamate a *rprof*:

1. Specificare il file di output del profiling.

    ```R
    varOutputFile <- "C:/TEMP/run001.log")
    Rprof(varOutputFile)
    ```
2. Disattivare il profiling
    ```R
    Rprof(NULL)
    ```
    
3. Riavviare il profiling
    ```R
    Rprof(append=TRUE)
    ```


> [!NOTE]
> Per poter usare questa funzione, è necessario che Windows Perl sia installato nel computer in cui viene eseguito il codice. Di conseguenza, è consigliabile profilare il codice durante lo sviluppo in un ambiente R e quindi distribuire il codice sottoposto a debug in SQL Server.  


## <a name="r-system-functions"></a>Funzioni di sistema R

Il linguaggio R include molte funzioni di pacchetto di base per la restituzione del contenuto delle variabili di sistema. 

Come parte del codice R, ad esempio, è possibile usare `Sys.timezone` per ottenere il fuso orario corrente o `Sys.Time` per ottenere l'ora di sistema da R. 

Per ottenere informazioni su singole funzioni di sistema R, digitare il nome della funzione come argomento per la funzione R `help()` da un prompt dei comandi di R.

```R
help("Sys.time")
```

## <a name="debugging-and-profiling-in-r"></a>Debug e profiling in R

La documentazione per Microsoft R Open, installata per impostazione predefinita, include un manuale sullo sviluppo di estensioni per il linguaggio R, che descrive il profiling e il debug in modo dettagliato.

Questo capitolo è anche disponibile online: [https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging](https://cran.r-project.org/doc/manuals/r-release/R-exts.html#Debugging)

### <a name="location-of-r-help-files"></a>Percorso dei file della Guida di R

C:\Programmi\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\doc\manual



