---
title: Conversione automatica di tipo di dati di tipo carattere | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 26dc8b3db6dae8f93f7e029a47b28d438d418cbf
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="autotranslation-of-character-data"></a>Conversione automatica dei dati di tipo carattere
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dati di tipo carattere, ad esempio ANSI carattere variabili dichiarate con SQL_C_CHAR o i dati archiviati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzando il **char**, **varchar**, o **testo** tipi di dati, è possibile rappresentare solo un numero limitato di caratteri. I dati di tipo carattere archiviati utilizzando un byte per carattere possono rappresentare solo 256 caratteri. I valori archiviati nelle variabili SQL_C_CHAR vengono interpretati mediante la tabella codici ANSI (ACP) del computer client. I valori archiviati utilizzando **char**, **varchar**, o **testo** tipi di dati nel server vengono valutati utilizzando l'ACP del server.  
  
 Se il server e i client hanno la stessa tabella codici ANSI, quindi non dispongono di alcun problema di interpretazione dei valori archiviati in SQL_C_CHAR **char**, **varchar**, o **testo** oggetti. Se il server e il client ha ACP differenti, quindi i dati SQL_C_CHAR del client possono essere interpretati come un carattere diverso sul server se viene utilizzato in **char**, **varchar**, o **testo** colonne, variabili o parametri. Ad esempio, un byte di caratteri contenente il valore 0xA5 viene interpretato come carattere Ñ in un computer con tabella codici 437 e viene interpretato come il simbolo dello yen (¥) in un computer con tabella codici 1252.  
  
 I dati Unicode vengono archiviati utilizzando due byte per carattere. Poiché tutti i caratteri estesi sono inclusi nella specifica Unicode, tutti i caratteri Unicode vengono interpretati allo stesso modo da tutti i computer.  
  
 La caratteristica AutoTranslate del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client tenta di ridurre al minimo i problemi lo spostamento di dati di tipo carattere tra un client e un server che dispongono di tabelle codici diverse. AutoTranslate può essere impostata nella stringa di connessione di [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md), nella stringa di configurazione di [SQLConfigDataSource](../../relational-databases/native-client-odbc-api/sqlconfigdatasource.md), o durante la configurazione di origini dati per il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC Native Client driver tramite Amministratore ODBC.  
  
 Quando AutoTranslate è impostata su "no", viene effettuata alcuna conversione sui dati spostati tra le variabili SQL_C_CHAR sul client e **char**, **varchar**, o **testo** colonne, variabili i parametri in o un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database. Se i dati contengono caratteri estesi e i due computer dispongono di tabelle codici diverse, gli schemi di bit potrebbero essere interpretati in modo diverso sui computer client e server. I dati verranno interpretati nello stesso modo se entrambi computer dispongono della stessa tabella codici.  
  
 Quando AutoTranslate è impostata su "yes", il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver ODBC Native Client utilizza Unicode per convertire i dati spostati tra le variabili SQL_C_CHAR sul client e **char**, **varchar**, o **testo** colonne, variabili o parametri in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:  
  
-   Quando i dati vengono inviati da una variabile SQL_C_CHAR sul client per un **char**, **varchar**, o **testo** colonna, variabile o parametro in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database ODBC driver converte innanzitutto da SQL_C_CHAR a Unicode utilizzando la tabella codici ANSI del client, quindi da Unicode al carattere utilizzando la tabella codici ANSI del server.  
  
-   Quando i dati vengono inviati da un **char**, **varchar**, o **testo** colonna, variabile o parametro in un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database a una variabile SQL_C_CHAR sul client, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver innanzitutto Converte caratteri in Unicode utilizzando l'ACP del server, quindi da Unicode a SQL_C_CHAR utilizzando l'ACP del client.  
  
 Poiché tutte le conversioni vengono eseguite dal [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'esecuzione di driver ODBC di Native Client sul client, l'ACP del server deve essere una delle tabelle codici installate nel computer client.  
  
 L'utilizzo di Unicode consente di eseguire la conversione più appropriata di tutti i caratteri presenti in entrambe le tabelle codici. Se tuttavia un carattere esiste in una tabella codici ma non in un'altra, non può essere rappresentato nella tabella codici di destinazione. Il simbolo del marchio registrato (®), ad esempio, è presente nella tabella codici 1252, ma non nella tabella codici 437.  
  
 L'impostazione di AutoTranslate non ha effetto sulle conversioni seguenti:  
  
-   Lo spostamento dei dati tra variabili del client SQL_C_CHAR carattere e Unicode **nchar**, **nvarchar**, o **ntext** colonne, variabili o parametri in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
-   Lo spostamento dei dati tra variabili del client SQL_C_WCHAR Unicode e caratteri **char**, **varchar**, o **testo** colonne, variabili o parametri in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.  
  
 I dati devono essere sempre convertiti nel passaggio da carattere a Unicode.  
  
## <a name="see-also"></a>Vedere anche  
 [Elaborazione dei risultati &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)   
 [Regole di confronto e supporto Unicode](../../relational-databases/collations/collation-and-unicode-support.md)  
  
  
