---
title: Editor trasformazione estrazione termini (scheda Avanzate) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ce44e2709013a6d56d47ad30c90ecf5d92825503
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185331"
---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>Editor trasformazione Estrazione termini (Scheda Avanzate)
  Usare la scheda**Avanzate** della finestra di dialogo **Editor trasformazione Estrazione termini** per specificare le proprietà per l'estrazione, ad esempio la frequenza, la lunghezza e le eventuali parole o frasi da estrarre.  
  
 Per ulteriori informazioni sulla trasformazione Estrazione termini, vedere [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Opzioni  
 **Sostantivo**  
 Consente di specificare che la trasformazione estrarrà solo singoli sostantivi.  
  
 **Sintagma nominale**  
 Consente di specificare che la trasformazione estrarrà solo sintagmi nominali.  
  
 **Sostantivo e sintagma nominale**  
 Consente di specificare che la trasformazione estrarrà sia sostantivi che sintagmi nominali.  
  
 **Frequenza**  
 Consente di specificare che il punteggio è rappresentato dalla frequenza del termine.  
  
 **TFIDF**  
 Consente di specificare che il punteggio è rappresentato dal valore TFIDF del termine. Il punteggio TFIDF è il prodotto della frequenza dei termini e della frequenza inversa dei documenti, definito come: TFIDF di un termine T = (frequenza di T) * log( (numero di righe nell'input) / (numero di righe contenenti T) )  
  
 **Soglia di frequenza**  
 Consente di specificare il numero di volte in cui una parola o una frase deve ricorrere prima che venga estratta. Il valore predefinito è 2.  
  
 **Lunghezza massima termine**  
 Consente di specificare la lunghezza massima in parole di una frase. Questa opzione ha effetto soltanto sui sintagmi nominali. Il valore predefinito è 12.  
  
 **Estrazione con distinzione maiuscole/minuscole**  
 Consente di specificare se eseguire l'estrazione rilevando la distinzione tra maiuscole e minuscole. Il valore predefinito è `False`.  
  
 **Configura output errori**  
 Usare la finestra di dialogo [Configura output errori](../../2014/integration-services/configure-error-output.md) per specificare la gestione degli errori per le righe che causano errori.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento ai messaggi e agli errori di Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Editor trasformazione estrazione termini &#40;scheda estrazione termini&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Editor trasformazione estrazione termini &#40;scheda di esclusione&#41;](../../2014/integration-services/term-extraction-transformation-editor-exclusion-tab.md)   
 [Trasformazione Ricerca termini](data-flow/transformations/lookup-transformation.md)  
  
  
