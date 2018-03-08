---
title: La libreria di cursori ODBC | Documenti Microsoft
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
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- scrollable cursors [ODBC]
- cursors [ODBC], cursor library
- block cursors [ODBC]
ms.assetid: 32fb7df0-953a-4f68-b041-7d2852e45d0f
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 45bce6d2b39ee15bcabd362b0a2fbfba377fe386
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="the-odbc-cursor-library"></a>La libreria di cursori ODBC
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzare questa funzionalità nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che attualmente utilizzano questa funzionalità. Si consiglia di utilizzare le funzionalità del driver del cursore.  
  
 Blocco e i cursori scorrevoli vengono aggiunti molto utili per molte applicazioni. Tuttavia, non tutti i driver supportano blocco e i cursori scorrevoli. Lo stesso vale per gli aggiornamenti posizionati e istruzioni delete e **SQLSetPos**, che vengono discussi in aggiornamento dei dati. Pertanto, il componente ODBC di Windows SDK, in precedenza incluso in Microsoft Data Access Components (MDAC) SDK, include una libreria di cursori. La libreria di cursori implementa blocchi, i cursori statici, per gli aggiornamenti posizionati e le istruzioni delete, e **SQLSetPos** per un driver conforme al livello di conformità Apri gruppo Standard CLI. La libreria di cursori può essere ridistribuita con le applicazioni ODBC; il contratto di licenza in SDK per ulteriori informazioni, vedere.  
  
 Per utilizzare la libreria di cursori, un'applicazione imposta l'attributo di connessione SQL_ATTR_ODBC_CURSORS prima che si connetta all'origine dati. Per ulteriori informazioni sulla libreria di cursori, vedere [libreria di cursori ODBC appendice f:](../../../odbc/reference/appendixes/appendix-f-odbc-cursor-library.md).
