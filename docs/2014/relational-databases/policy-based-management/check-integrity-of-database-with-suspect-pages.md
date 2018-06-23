---
title: Verificare l'integrità di un database contenente pagine sospette | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58be64be62903502cc6f585148b168d2e03227bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36068513"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Verifica del'integrità di un database contenente pagine sospette
  Questa regola consente di controllare i database utente con stato impostato come sospetto. Quando il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] legge una pagina di database contenente un errore 824, la pagina viene considerata sospetta, l'ID di pagina corrispondente viene registrato nella tabella suspect_pages in msdb e il database contenente la pagina viene impostato come sospetto.  
  
 L'errore 824 indica che è stato rilevato un errore logico correlato alla consistenza durante un'operazione di lettura. Questo errore indica in genere il danneggiamento dei dati causato da un componente del sottosistema di I/O difettoso. Si tratta di una condizione di errore grave che può compromettere l'integrità del database e che deve essere corretta immediatamente.  
  
## <a name="best-practices-recommendations"></a>Procedure consigliate  
  
-   Esaminare il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per individuare informazioni dettagliate sull'errore 824 per il database.  
  
-   Eseguire una verifica di coerenza del database ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).  
  
-   Implementare le azioni dell'utente definite in [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Ulteriori informazioni  
 [Gestione della tabella suspect_pages &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
