---
title: "Passaggio 5: Test del pacchetto creato nella lezione 4 dell'esercitazione | Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
caps.latest.revision: 22
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 10e6f1b123364f13c0132fb376794b9e37fdc96c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36063634"
---
# <a name="step-5-testing-the-lesson-4-tutorial-package"></a>Passaggio 5: Test del pacchetto creato nella lezione 4 dell'esercitazione
  In fase di esecuzione, il file danneggiato Currency_BAD.txt non sarà in grado di generare una corrispondenza all'interno della trasformazione Lookup Currency Key. Dato che l'output degli errori di Lookup Currency Key è stato configurato per il reindirizzamento delle righe con esito negativo alla nuova destinazione Failed Rows, il componente non presenta errori e il pacchetto viene eseguito correttamente. Tutte le righe di errore sono riportate nel file ErrorOutput.txt.  
  
 In questa attività verrà eseguito il test della configurazione dell'output degli errori modificata tramite l'esecuzione del pacchetto. Al termine dell'esecuzione corretta del pacchetto sarà possibile visualizzare il contenuto del file ErrorOutput.txt.  
  
> [!NOTE]  
>  Per evitare l'accumulo di righe di errore nel file ErrorOutput.txt, è consigliabile eliminare manualmente il contenuto del file dopo l'esecuzione di ogni pacchetto.  
  
## <a name="checking-the-package-layout"></a>Verifica del layout del pacchetto  
 Prima di testare il pacchetto è consigliabile verificare che il flusso di controllo e il flusso di dati nel pacchetto della lezione 4 contengano gli oggetti visualizzati nelle figure seguenti. Il flusso di controllo deve essere identico a quello nelle lezioni 2 - 4.  
  
 **Flusso di controllo**  
  
 ![Flusso di controllo nel pacchetto](../../2014/tutorials/media/task4lesson2control.gif "Flusso di controllo nel pacchetto")  
  
 **Flusso di dati**  
  
 ![Flusso di dati nel pacchetto](../../2014/tutorials/media/task5lesson5data.gif "Flusso di dati nel pacchetto")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Per eseguire il pacchetto creato nella lezione 4 dell'esercitazione  
  
1.  Scegliere **Avvia debug** dal menu **Debug**.  
  
2.  Al termine dell'esecuzione del pacchetto, scegliere **Arresta debug** dal menu **Debug**.  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>Per verificare il contenuto del file ErrorOutput.txt  
  
-   Aprire il file ErrorOutput.txt in Blocco note o qualsiasi altro editor di testo. L'ordine predefinito delle colonne è: AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
  
     Si noti che tutte le righe nel file contengono il valore BAD per il CurrencyID privo di corrispondenza, il valore -1071607778 per ErrorCode, il valore 0 per ErrorColumn e il valore "Nessuna corrispondenza per la riga durante le ricerca" per ErrorDescription. Il valore di ErrorColumn è impostato su 0 perché l'errore non è specifico della colonna. È l'operazione di ricerca che ha avuto esito negativo. ,  
  
  