---
title: File di traccia | Documenti Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- trace files [ODBC]
- tracing options [ODBC], trace files
ms.assetid: ec97f949-126f-40a2-b67e-e74520a524cb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb9089ed49e623247384557e8650731f6abc9816
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915266"
---
# <a name="trace-file"></a>File di traccia
Un'applicazione specifica il file di traccia impostando il **TraceFile** parola chiave nella voce del Registro di sistema ODBC o chiamando **SQLSetConnectAttr** con l'attributo di connessione SQL_ATTR_TRACEFILE. Se il file non esiste quando la traccia è abilitata, gestione Driver verrà creato il file. Ogni applicazione deve avere un proprio file di traccia dedicato per evitare conflitti. Un'applicazione può utilizzare più di un file di traccia. il programma di installazione di un'applicazione può fornire all'utente una scelta di file di traccia. Se è attivata in modo dinamico, un'applicazione può anche visualizzare i risultati della traccia, anziché la registrazione nel file di traccia.  
  
 Il file di traccia fornisce i valori di tutti gli argomenti e un log di ogni chiamata di funzione ODBC con i tipi di dati. Registra le funzioni di tutti gli input ed esegue tutte le funzioni restituite con i codici restituiti e gli stati di errore.  
  
 In ODBC 3*x*, parametri delle funzioni di connessione non disponibili per la DLL di traccia.
