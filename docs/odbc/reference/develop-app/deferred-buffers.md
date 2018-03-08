---
title: Posticipata buffer | Documenti Microsoft
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
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6cbe554b72bf971e6b589b936cd6901ef5fa59a7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="deferred-buffers"></a>Buffer posticipato
Oggetto *buffer posticipata* uno cui valore è utilizzato in un momento *dopo* è specificato in una chiamata di funzione. Ad esempio, **SQLBindParameter** viene utilizzato per associare, o *associare,* un buffer di dati con un parametro in un'istruzione SQL. L'applicazione specifica il numero del parametro e passa l'indirizzo, lunghezza in byte e il tipo di buffer. Il driver queste informazioni vengono salvate ma non esamina il contenuto del buffer. In un secondo momento, quando l'applicazione viene eseguita l'istruzione, il driver recupera le informazioni e viene utilizzato per recuperare i dati del parametro e inviarlo all'origine dati. Pertanto, l'input di dati nel buffer viene posticipata. Poiché posticipata i buffer sono specificati in una funzione e usati in un altro, è un'applicazione di un errore di programmazione per liberare un buffer posticipato, mentre il driver ancora prevede che altri utenti. Per ulteriori informazioni, vedere [allocazione e liberando buffer](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md), più avanti in questa sezione.  
  
 È possibile rinviare i buffer di input e di output. Nella tabella seguente sono riepilogati gli utilizzi di buffer posticipato. Si noti che posticipato buffer associato a un set di colonne vengono specificati con **SQLBindCol**, e posticipata i buffer associati a parametri di istruzioni SQL vengono specificati con **SQLBindParameter**.  
  
|Utilizzo di buffer|Tipo|Specificato con|Usato da|  
|----------------|----------|--------------------|-------------|  
|L'invio dei dati per i parametri di input|Input posticipata|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Imposta l'invio dei dati per aggiornare o inserire una riga in un risultato|Input posticipata|**SQLBindCol**|**SQLSetPos**|  
|Restituzione di dati per i parametri di input/output e output|Output posticipato|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Restituzione di risultati set di dati|Output posticipato|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
