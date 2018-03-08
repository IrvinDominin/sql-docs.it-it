---
title: L'impostazione del livello di isolamento delle transazioni | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- isolation levels [ODBC]
- transaction isolation [ODBC]
- transactions [ODBC], isolation
ms.assetid: 64a037f0-5065-4f45-9669-6710404a540c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 74c345bb8bdfae60a06576b43b655ef78e4a6dfc
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-transaction-isolation-level"></a>L'impostazione del livello di isolamento delle transazioni
Per impostare il livello di isolamento delle transazioni, un'applicazione utilizza l'attributo di connessione SQL_ATTR_TXN_ISOLATION. Se l'origine dati non supporta il livello di isolamento richiesto, il driver o l'origine dati è possibile impostare un livello superiore. Per determinare quali isolamento della transazione i livelli di un'origine dati supporta ed è il livello di isolamento predefinito, un'applicazione chiama **SQLGetInfo** con le opzioni SQL_TXN_ISOLATION_OPTION e SQL_DEFAULT_TXN_ISOLATION, rispettivamente.  
  
 Livelli di isolamento della transazione offrono la massima protezione per l'integrità dei dati di database. Le transazioni serializzabili sono garantite sarà interessato da altre transazioni e pertanto garantite per mantenere l'integrità del database.  
  
 Tuttavia, un livello di isolamento delle transazioni può un rallentamento delle prestazioni poiché aumenta le probabilità che l'applicazione dovrà attendere i blocchi sui dati da rilasciare. Un'applicazione può specificare un livello inferiore di isolamento per migliorare le prestazioni nei casi seguenti:  
  
-   Quando possibile garantire che nessun altro sono presenti transazioni che potrebbe interferire con le transazioni di un'applicazione. Questa situazione si verifica solo in alcune circostanze specifiche, ad esempio quando una persona una piccola società gestisce file dBASE che contengono dati personale in un computer e non condivide tali file.  
  
-   Cui la velocità è prioritaria rispetto alla precisione e gli eventuali errori è probabile che sia esiguo. Ad esempio, si supponga che una società rende l'importo delle vendite di piccole dimensioni e che le vendite di grandi dimensioni sono rare. Una transazione di cui si stima il valore totale di tutte le vendite potrebbe utilizzare in modo sicuro il livello di isolamento Read Uncommitted. Anche se la transazione include gli ordini che sono viene aperto o chiuso e successivamente il rollback, questi verrebbe in genere annullano reciprocamente e la transazione sarà molto più veloce perché non è bloccato ogni volta che rileva un ordine di questo tipo.  
  
 Per ulteriori informazioni, vedere [la concorrenza ottimistica](../../../odbc/reference/develop-app/optimistic-concurrency.md).
