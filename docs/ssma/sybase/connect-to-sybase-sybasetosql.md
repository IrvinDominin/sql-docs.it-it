---
title: Connettersi a Sybase (SybaseToSQL) | Documenti Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 524f95ef-10bd-497c-84ca-c06a0ae794fb
caps.latest.revision: "4"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ebf5f7f5c12a8a2e3af85ba2901e2348da92c30b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-sybase-sybasetosql"></a>Connettersi a Sybase (SybaseToSQL)
Utilizzare il **Connetti Sybase** finestra di dialogo per connettersi all'istanza di Sybase Adaptive Server Enterprise (ASE) che si desidera eseguire la migrazione.  
  
Per accedere a questa finestra di dialogo, scegliere il **File** dal menu **Connetti Sybase**. Se in precedenza si è connessi, il comando è **riconnessione per Sybase**.  
  
## <a name="options"></a>Opzioni  
**Provider**  
Selezionare una qualsiasi del Provider installato nel computer per la connessione al Server di Sybase.  
  
**Mode**  
Selezionare entrambe le modalità di connessione standard o avanzata. In modalità standard, immettere o selezionare i valori per il nome del server, porta, nome utente e password. Nella modalità avanzata è fornire una stringa di connessione.  
  
**Nome server**  
Immettere o selezionare il nome o indirizzo IP del Server adattivo. Il nome del server predefinito è lo stesso nome del computer. Questa è un'opzione di modalità standard.  
  
**Porta server**  
Se si utilizza una porta non predefinita per le connessioni a ASE, immettere il numero di porta. Il numero di porta predefinito è 5000. Questa è un'opzione di modalità standard.  
  
**User name**  
Immettere il nome utente utilizzato per connettersi a ASE. Questa è un'opzione di modalità standard.  
  
**Password**  
Immettere la password associata al nome utente. Questa è un'opzione di modalità standard.  
  
**Stringa di connessione**  
Immettere la stringa di connessione completa per la connessione di base.  
  
Le stringhe di connessione è costituito da coppie nome / valore di parametro. I nomi dei parametri variano con il provider in uso.  
  
**Come indicato di seguito sono riportati i parametri di connessione per diversi provider:**  
  
1.  Parametri di connessione per **Provider OLE DB**  
  
    |Impostazione|Parametro Sybase 12,5|Parametro Sybase 15|  
    |-----------|-------------------------|-----------------------|  
    |Nome server|Server Name|Server|  
    |Port|Indirizzo di porta del server|Port|  
    |Nome utente|ID utente|ID utente|  
    |Password|Password|Password|  
    |Provider|Provider|Provider|  
  
    Per Sybase ASE 12,5, una stringa di connessione di esempio è la seguente:  
  
    `Server Name=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=Sybase.ASEOLEDBProvider;`  
  
    Per Sybase ASE 15, una stringa di connessione di esempio è la seguente:  
  
    `Server=sybserver;User ID=MyUserID;Password=MyP@$$word;Provider=ASEOLEDB;Port=5000;`  
  
2.  Parametri di connessione per **Provider ODBC**  
  
    |Impostazione|Parametro Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Nome del driver|Driver|  
    |Server Name|Server|  
    |Nome utente|UID|  
    |Password|Pwd|  
    |Numero di porta|Port|  
  
    Per Sybase ASE 12,5 o 15, una stringa di connessione di esempio è la seguente:  
  
    `driver=Adaptive Server Enterprise;Server=sybserver;uid=MyUserID;pwd=MyP@$$word;Port=5000;`  
  
3.  Parametri di connessione per **Provider ADO.NET**  
  
    |Impostazione|Parametro Sybase 12,5/15|  
    |-----------|-----------------------------|  
    |Server Name|Server|  
    |Nome utente|UID|  
    |Password|Pwd|  
    |Numero di porta|Port|  
  
    Un esempio di stringa di connessione per il Provider ADO.NET è come segue:  
  
    `Server=sybserver;Port=5000;uid=MyUserID;pwd=MyP@$$word;`  
  
Per ulteriori informazioni, vedere la documentazione di base.  
  
Si tratta di un'opzione di modalità avanzata.  
  
