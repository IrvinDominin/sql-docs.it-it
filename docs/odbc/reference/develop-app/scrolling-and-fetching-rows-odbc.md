---
title: Scorrimento e recupero di righe (ODBC) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scrollable cursors [ODBC]
- fetches [ODBC], scrollable cursors
- cursors [ODBC], scrollable
- scrolling rows [ODBC]
ms.assetid: c43764cb-5841-4b89-9dc0-984a7488b3c1
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5b5a9aefccf51cc4b3aac1aeba02c7878c6dceed
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="scrolling-and-fetching-rows-odbc"></a>Scorrimento e recupero di righe (ODBC)
Quando si utilizza un cursore scorrevole, le applicazioni chiamano **SQLFetchScroll** per posizionare il cursore e recuperare righe. **SQLFetchScroll** supporta lo scorrimento relativo (successivo, precedente e relativo * n * righe), lo scorrimento assoluto (primo, ultimo e di riga * n *), e posizionamento dal segnalibro. Il *FetchOrientation* e *FetchOffset* argomenti **SQLFetchScroll** specificare quale set di righe da recuperare, come illustrato nelle figure seguenti.  
  
 ![Recupero del successivo, precedente, primo e ultimo set di righe](../../../odbc/reference/develop-app/media/pr20_2.gif "pr20_2")  
  
 **Recupero del successivo, precedente, primo e ultimo set di righe**  
  
 ![Recupero del Rowset assoluto, relativo e con segnalibro](../../../odbc/reference/develop-app/media/pr20_1.gif "pr20_1")  
  
 **Recupero del rowset assoluto, relativo e con segnalibro**  
  
 **SQLFetchScroll** posiziona il cursore nella riga specificata e restituisce le righe nel set di righe a partire da tale riga. Se il set di righe specificato si sovrappone la fine del set di risultati, viene restituito un set di righe parziale. Se il set di righe specificato si sovrappone all'inizio del risultato è impostato, il primo set di righe nel risultato viene restituito in genere set; Per informazioni dettagliate, vedere il [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md) descrizione della funzione.  
  
 In alcuni casi, l'applicazione potrebbe essere utile posizionare il cursore senza recuperare i dati. Ad esempio, consiglia di verificare l'esistenza di una riga o ottenere solo il segnalibro per la riga senza visualizzare altri dati attraverso la rete. A tale scopo, impostato l'attributo di istruzione SQL_ATTR_RETRIEVE_DATA SQL_RD_OFF. La variabile associata alla colonna segnalibro (se presente) viene sempre aggiornata, indipendentemente dall'impostazione di questo attributo di istruzione.  
  
 Dopo aver recuperato il set di righe, l'applicazione può chiamare **SQLSetPos** per posizionare in una particolare riga nelle righe del set di righe o di aggiornamento nel set di righe. Per ulteriori informazioni sull'utilizzo **SQLSetPos**, vedere [aggiornamento dei dati con SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md).  
  
> [!NOTE]  
>  Lo scorrimento è supportato in ODBC 2. *x* driver da **SQLExtendedFetch**. Per ulteriori informazioni, vedere [cursori a blocchi, i cursori scorrevoli e compatibilità con le versioni precedenti](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)nell'appendice g: Driver le linee guida per la compatibilità con le versioni precedenti.