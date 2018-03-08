---
title: "Che cos'è ODBC? | Microsoft Docs"
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
helpviewer_keywords: ODBC [ODBC], about ODBC
ms.assetid: badf3a45-f941-44ae-a31d-393116f68a18
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f1cb1869039572d0d6da1302f66ce64abc3f2590
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-odbc"></a>Che cos'è ODBC?
Molti pregiudizi ODBC esistono nell'ambiente di elaborazione. Per l'utente finale, è un'icona nel Pannello di controllo di Microsoft® Windows®. Per il programmatore di applicazione, è una libreria che contiene la routine di accesso ai dati. In molti altri controlli, è la risposta a tutti i problemi di accesso al database possibili.  
  
 Prima di tutto, ODBC è una specifica per un'API di database. Questa API è indipendente da qualsiasi un DBMS o sistema operativo. Sebbene questo manuale utilizza C, l'API ODBC è indipendente dal linguaggio. L'API ODBC si basa sulle specifiche di CLI da Open Group e ISO/IEC. ODBC 3. *x* completamente implementa entrambe queste specifiche, ovvero le versioni precedenti di ODBC sono basate su versioni preliminari di queste specifiche, ma non viene tuttavia implementata completamente e sono state aggiunte funzionalità comunemente utilizzate dagli sviluppatori di basate su schermo applicazioni di database, ad esempio i cursori scorrevoli.  
  
 Le funzioni dell'API ODBC vengono implementate dagli sviluppatori di driver DBMS specifici. Applicazioni di chiamano le funzioni in questi driver per accedere ai dati in modo indipendente dal DBMS. Una gestione Driver gestisce le comunicazioni tra applicazioni e driver.  
  
 Sebbene Microsoft fornisce un gestore di driver per i computer che eseguono Microsoft Windows® 95 e versioni successive, è scritto diversi driver ODBC e chiama funzioni ODBC da alcune delle relative applicazioni, che chiunque possa scrivere i driver e le applicazioni ODBC. In effetti, la maggior parte delle applicazioni ODBC e driver disponibili oggi vengono scritte da Microsoft. Inoltre, le applicazioni e driver ODBC presenti nel Macintosh® e un'ampia gamma di piattaforme UNIX.  
  
 Per consentire agli sviluppatori di applicazioni e driver, Microsoft offre un ODBC Software Development Kit (SDK) per i computer che eseguono Windows 95 e versioni successive che fornisce la gestione driver, installazione DLL, strumenti di test e applicazioni di esempio. Microsoft è raggruppata con Visigenic Software alla porta questi SDK per Macintosh e un'ampia gamma di piattaforme UNIX.  
  
 È importante comprendere che ODBC sia progettato per esporre funzionalità di database, non completarli. Di conseguenza, gli autori di applicazioni non dovrebbero che l'utilizzo di ODBC trasformerà improvvisamente un database semplice in un motore di database relazionale completamente in primo piano. Né gli sviluppatori di driver devono implementare la funzionalità non trovata nel database sottostante. Un'eccezione è che gli sviluppatori che scrivono i driver che accedono direttamente ai dati di file (ad esempio, i dati in un file Xbase) sono necessari per scrivere un motore di database che supporta la funzionalità SQL almeno minima. Un'altra eccezione è che il componente ODBC di Windows SDK, in precedenza incluso in Microsoft Data Access Components (MDAC) SDK, fornisce una libreria di cursori che simula i cursori scorrevoli per i driver che implementano un certo livello di funzionalità.  
  
 Le applicazioni che utilizzano ODBC sono responsabili di eventuali funzionalità tra database. Ad esempio ODBC non è un motore di join eterogeneo, non è un processore di transazione distribuita. Tuttavia, poiché è indipendente dal sistema DBMS, può essere utilizzato per compilare tali strumenti tra database.
