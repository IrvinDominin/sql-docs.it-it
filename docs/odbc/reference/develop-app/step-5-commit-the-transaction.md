---
title: 'Passaggio 5: Eseguire il Commit della transazione | Documenti Microsoft'
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
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8494c26badd04a1c009f8f23c60559ed695ea3d2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="step-5-commit-the-transaction"></a>Passaggio 5: Eseguire il Commit della transazione
Il passaggio successivo è il commit della transazione, come illustrato nella figura seguente.  
  
 ![Viene illustrato come eseguire il commit di una transazione](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 Il quinto passaggio consiste nel chiamare **SQLEndTran** per eseguire il commit o il rollback della transazione. L'applicazione esegue questo passaggio solo se è impostata la modalità di commit della transazione di commit manuale; Se la modalità di commit della transazione è commit automatico, ovvero l'impostazione predefinita, quando viene eseguita l'istruzione viene automaticamente il commit della transazione. Per ulteriori informazioni, vedere [transazioni](../../../odbc/reference/develop-app/transactions-odbc.md).  
  
 Per eseguire un'istruzione in una nuova transazione, l'applicazione torna al passaggio 3. Per disconnettersi dall'origine dati, l'applicazione procede al passaggio 6.
