---
title: Supporto delle transazioni | Documenti Microsoft
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
helpviewer_keywords: transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4964565ce7de30b30fa3dc4c7705c5656ebcb88b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-support"></a>Supporto delle transazioni
Il livello di supporto per le transazioni è definito dal driver. ODBC è progettato per essere implementata in un database utente singolo o desktop che non è necessario che per gestire gli aggiornamenti più ai relativi dati. Inoltre, alcuni database che supportano le transazioni di eseguire in modo che solo per le istruzioni Data Manipulation Language (DML) di SQL. Esistono restrizioni o semantica delle transazioni speciali relative all'uso di Strumentazione gestione Windows (DDL, Data Definition Language) quando è attiva una transazione. Ovvero, è possibile il supporto delle transazioni per più aggiornamenti simultanei a tabelle ma non per modificare il numero e la definizione delle tabelle durante una transazione.  
  
 Un'applicazione determina se sono supportate le transazioni, se DDL possono essere inclusi in una transazione e gli effetti speciali di inclusione di DDL in una transazione, chiamando **SQLGetInfo** con l'opzione SQL_TXN_CAPABLE. Per ulteriori informazioni, vedere il [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) descrizione della funzione.  
  
 Se il driver non supporta le transazioni ma l'applicazione ha la possibilità (tramite un'API diverso da ODBC) per bloccare e sbloccare i dati, le applicazioni possono ottenere il supporto delle transazioni dai record di blocco e sblocco e dalle tabelle in base alle esigenze. Per implementare l'esempio di trasferimento di account, l'applicazione verrebbe bloccare i record per entrambi gli account, copiare i valori correnti, dare il primo account, il secondo account del credito e sbloccare i record. Se tutte le operazioni non è riuscita, l'applicazione verrebbe reimpostare gli account con le copie.  
  
 Origini di dati che supportano le transazioni potrebbero non essere in grado di supportare più di una transazione alla volta all'interno di un particolare ambiente. Le applicazioni chiamano **SQLGetInfo** con l'opzione SQL_MULTIPLE_ACTIVE_TXN per determinare se un'origine dati può supportare le transazioni attive simultanee in più connessioni nello stesso ambiente. Poiché è presente una transazione per ogni connessione, questa opzione per le applicazioni che dispongono di più connessioni alla stessa origine dati.
