---
title: Ricerca incrementale in un documento attivo | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba2c50eadb3e3f8a93a4f1f24bddf7d4bc7c6637
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2018
---
# <a name="search-an-active-document-incrementally"></a>Ricerca incrementale in un documento attivo
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] È possibile eseguire una ricerca incrementale in un singolo documento o in una singola finestra immettendo il testo. Verrà evidenziato il primo set di caratteri che corrisponde ai caratteri immessi durante la ricerca incrementale nel documento o nella finestra. La ricerca viene estesa automaticamente a tutto il testo all'interno di un documento o di una finestra, fatta eccezione per il testo nascosto.  
  
 Se viene scelta l'opzione **Maiuscole/minuscole** , per la ricerca incrementale verranno usati i criteri della ricerca precedente. Se, ad esempio, in precedenza è stata eseguita una ricerca su più file tramite la finestra di dialogo **Cerca nei file** , viene selezionata l'opzione **Maiuscole/minuscole**e quindi viene eseguita una ricerca incrementale. Nella ricerca verrà fatta distinzione tra maiuscole e minuscole.  
  
### <a name="to-search-incrementally"></a>Per eseguire una ricerca incrementale  
  
1.  Aprire il file o la finestra in cui si desidera eseguire la ricerca.  
  
2.  Scegliere **Avanzate** dal menu **Modifica**e quindi fare clic su **Ricerca incrementale**.  
  
     L'icona del cursore si trasforma in un binocolo con una freccia, che indica la direzione della ricerca, mentre sulla barra di stato viene visualizzato "Ricerca incrementale".  
  
3.  Iniziare a digitare la stringa di testo.  
  
     Sulla barra di stato viene visualizzato il testo immesso mentre l'editor evidenzia la prima occorrenza corrispondente. Mentre la digitazione continua, l'editor si sposta sulla corrispondenza successiva e la evidenzia. Se non viene trovata nessuna corrispondenza, sulla barra di stato viene visualizzato quanto segue.  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 Le ricerche incrementali vengono eseguite procedendo verso il basso e da sinistra a destra a partire dalla posizione corrente nel documento. È possibile utilizzare i tasti di scelta rapida.  
  
> [!NOTE]  
>  Per un elenco completo dei tasti di scelta rapida, vedere [Tasti di scelta rapida di SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione](../../relational-databases/scripting/search-and-replace.md)   
 [Ricerca interattiva all'interno di documenti](../../relational-databases/scripting/search-documents-interactively.md)   
 [Ricerca nei documenti utilizzando gli elenchi dei risultati](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [Testo di ricerca con caratteri jolly](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Eseguire ricerche di testo con espressioni regolari](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
